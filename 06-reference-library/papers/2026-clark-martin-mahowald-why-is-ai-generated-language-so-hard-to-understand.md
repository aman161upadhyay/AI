# Why is AI-generated language so hard to understand?

**Authors:** Thomas Hikaru Clark (NYU), Matias B. Martin (UT Austin), Kyle Mahowald (UT Austin)
**Venue:** arXiv:2610.29162v1 [cs.CL], 21 October 2026
**Source:** PDF supplied by Aman (`WritingLLMs.pdf`), converted to Markdown on 2026-10-25. Section 1 below is our structured summary written for the writing agent; Section 2 transcribes Table 2 from the PDF (the example sentences); Section 3 is the automated full-text extraction (figure labels and axis ticks may be interleaved; refer to the PDF for figures).
**Why it is in this library:** it is the first paper to measure, across 14 models and three settings (chat, coding, essays), the specific grammatical habits that make model prose harder to read, and to propose a mechanism (post-training rewards that favour information density). The writing agent's "slop pass" uses these seven measures directly.

---

## 1. Structured summary (for the writing agent)

### The claim

Frontier models write in a way that is grammatical but out of distribution for human English, and the specific features they overuse are the ones psycholinguistics has long linked to comprehension difficulty. The authors argue this comes from training objectives (math, code, reasoning with verifiable rewards, long context windows) that reward getting the answer with fewer tokens, not communicating with a human who has limited working memory.

### Models and data

- Nine frontier and near-frontier models: Claude Sonnet 5, Opus 5, Opus 5.5, Fable 5; GPT-5.6 sol, terra, luna; GLM-5; Kimi K2.5. Five small open models: Llama 3.1 8B (base, instruct), Olmo 3 7B (base, instruct, think).
- Three settings: chat (10 topics x 12 models, 12-turn conversations), coding (5 GitHub repos x 9 models, 12-turn agentic sessions with tools), essays (PERSUADE prompts, 980 model essays vs 2,934 high-scoring student essays on the same prompts).
- Control: round-trip translation paraphrases that keep meaning fixed, to show the features come from the models' production habits, not from the content.

### The seven measures (use these as a checklist)

| # | Measure | What it is | Why it is hard for readers | Example from a model (Table 2) |
|---|---|---|---|---|
| 1 | Object relative clause without "that" (reduced relative) | A relative clause whose object is relativised, with the relativiser dropped: "the job you hate" instead of "the job that you hate" | Non-canonical word order plus a dropped cue; the reader has to recover the gap | "the papercut people feel day-to-day" |
| 2 | Denominal verb | A noun used as a verb: "calendar it", "footnote it", "cushions price spikes" | Low-frequency, often unattested usage; reader must coin the meaning | "pooling independent judgments filters out individual errors" |
| 3 | Animate-subject verb with inanimate subject | A verb that normally takes a human agent given to a thing: "the docstring promises", "chaos expects you", "the objection misunderstands" | Metaphorical agency the reader must unpack each time | "A song doesn't ask you to turn melancholy into a calendar item" |
| 4 | Dependency length | Long distance between words that depend on each other, usually from heavy modifiers inserted between subject and verb | Working-memory load; the reader holds the subject open while parsing the insert | "The guitar sitting in the corner because you're still 'deciding' teaches you zero chords" |
| 5 | Stacked nouns | Noun compounds three or more deep: "dotfile backup path handling", "class-time shutdown requirement", "reader-patience budget" | Relations between the nouns are implicit; multiple readings possible | "Fixed absolute dotfile backup path handling while preserving the : marker" |
| 6 | Unattested word pairs | Bigrams that never occur in a human reference corpus | Low predictability, high surprisal | "early perceptual processing", "lazy-intermediate Lookup behavior" |
| 7 | Trigram surprisal / n-gram perplexity | Overall low predictability of word sequences under an independent n-gram model | Each unpredictable word costs reading time | "not really a gear trap" |

### Results

- All nine frontier and near-frontier models use more inanimate subjects with animate verbs and more low-frequency n-grams than humans do.
- Most also use longer dependencies, more stacked nouns, and more reduced object relatives in conversation.
- The features are rare in meaning-matched round-trip-translation paraphrases, so they are a property of how the models produce text, not of the topics.
- Base models (Llama, Olmo) and older instruct models are closer to human distributions; the frontier post-trained models are furthest away. Model families differ substantially, and Opus 5.5 shows a measurable improvement over Opus 5 on these measures, so the behaviour is trainable in both directions.
- Experiment 2: fine-tuning a model with GRPO under a length penalty, with no instruction about style, produced an emergent, near-categorical preference (over 98% without KL regularisation) for the shorter member of syntactic alternations, including alternations never seen in training. Correctness was unaffected, which is the point: the objective did not care about the reader.

### Mechanism the authors propose

- Human language balances ease of production and ease of comprehension (dependency-length minimisation, uniform information density, incremental processing).
- RLHF tends to reward longer outputs; the shift to reinforcement learning with verifiable rewards (RLVR) removes the human from the loop and rewards compressed, correct answers. Combined with long and expensive context windows, this creates pressure toward information density.
- The result is a dialect that is efficient for models and tiring for people. The authors speculate increased exposure may acclimatise readers, but the features remain fundamental obstacles to intelligibility and to monitorability of model reasoning.

### What this means for an agent that writes for humans

1. Treat the seven measures as a lint pass after drafting. Restore "that" in object relatives, replace denominal verbs with ordinary verbs, give actions to people or name the mechanism instead of letting objects "promise" or "expect", split long dependencies, unpack noun stacks into prepositional phrases, and prefer common collocations over novel pairs.
2. The bias is strongest in coding-session prose (commit messages, PR descriptions, status updates) because that is where the density pressure comes from. Review that text with extra care.
3. Terse is not the same as clear. Optional words such as "that", articles, and connectives are the cues human parsers rely on. Removing them saves tokens and costs the reader.
4. Human-written exemplars (Aman's own messages) are the right target distribution; the model's defaults are not.
5. Reward or select for comprehension, not length. When running a council or judge over drafts, score readability with these measures, not with a generic "concise" criterion that would push the text further in the wrong direction.

---

## 2. Table 2 transcribed: example sentences for each measure, by setting

Bold marks the construction the authors highlighted. Inline code was typewriter type in the original. Model labels: Kimi = Kimi K2.5; GLM = GLM-5; Sol, Terra, Luna = GPT-5.6 variants; Sonnet, Opus 5, Opus 5.5, Fable = Claude models.

### Object relative clause without "that"

| Setting | Model | Sentence |
|---|---|---|
| Chat | Kimi | That's not "trip to Vegas" money, that's "leave the **job you hate**" money. |
| Chat | Opus 5.5 | That's great for a beginner, honestly one of the best **genres you could pick**. |
| Coding | Opus 5.5 | Three fail on the old code; the others check **behaviour the old code never reached**. |
| Coding | GLM | The case/when fix is technically more impressive, but the unclosed-tag errors are the **papercut people feel day-to-day**. |
| Essay | Terra | Some students may feel that required service takes time away from **activities they care about**. |
| Essay | Opus 5 | I am writing to share my thoughts on the cell phone **policy you are considering**. |

### Denominal verb

| Setting | Model | Sentence |
|---|---|---|
| Chat | Opus 5 | And Austin has unusually high inventory, which **cushions** price spikes better than supply-constrained markets. |
| Chat | Sonnet | Genuinely unsolicited advice: don't try to get her to **categorize** movies as speed-runnable or not. |
| Coding | Luna | The `last_when` fallback is therefore not dead code; it is **masking** that inconsistency. |
| Coding | Sol | Prevented Git dry runs from installing hooks or **staging** changes. |
| Essay | Fable | In each case, the logic is the same: **pooling** independent judgments filters out individual errors. |
| Essay | GLM | This process **mirrors** real-world challenges much more closely than a packet of predefined questions. |

### Animate-subject verb, inanimate subject

| Setting | Model | Sentence |
|---|---|---|
| Chat | Sol | Sometimes chaos has a 1099; sometimes **chaos expects** you to remember it independently. |
| Chat | Terra | A **song** doesn't **ask** you to turn melancholy into a calendar item. |
| Coding | Fable | The **docstring promises** they're skipped when they "appear anywhere in the `source_dir` path"; e.g. backing up a dotfolder like `~/.cache/foo` was not skipped. |
| Coding | Sonnet | No new branch, no change in control flow, just closing the gap in an existing **check** that covered `str` but **forgot** its sibling scalar-like type `bytes`. |
| Essay | Opus 5.5 | These are the exact skills the **worksheet hoped** to teach, but she has learned them because she wanted an answer. |
| Essay | Kimi | Second, the time **objection misunderstands** how service actually functions. |

### Dependency length

| Setting | Model | Sentence |
|---|---|---|
| Chat | Sonnet | The **guitar** sitting in the corner because you're still "deciding" **teaches** you zero chords. |
| Chat | Luna | Has the building **had** water, mold, structural, or insurance **claims**? |
| Coding | Fable | All five expression **shapes**, attribute access, subscript, calls, nested calls, string literals, **leave** `current` on `NAME('b')`, and the full template renders correctly. |
| Coding | Terra | A **lattice** constructed with duplicate points, or a `SymbolSet` with colliding labels/names, can **overwrite** internal dictionary or attribute mappings. |
| Essay | Sol | **Projects** completed on weekends, during school events, or over the summer could all **count**. |
| Essay | Sonnet | Class **time**, where a total blackout policy would apply under Policy 1, **remains** protected and focused. |

### Stacked nouns

| Setting | Model | Sentence |
|---|---|---|
| Chat | GLM | **Summer park district classes** are a whole thing in Chicago and people actually do them. |
| Chat | Opus 5 | Online banks (Ally, Marcus, Capital One 360, Discover, SoFi) or **brokerage money market funds** (Fidelity's SPAXX, Vanguard's VMFXX) are the standard options. |
| Coding | Luna | Fixed absolute **dotfile backup path handling** while preserving the `:` marker used during reinstall. |
| Coding | Opus 5 | Every long line in that list is pre-existing (long **error-message string literals**, which black leaves alone since it doesn't split strings without `--preview`). |
| Essay | Kimi | I acknowledge concerns about distraction, but Policy 1's **class-time shutdown requirement** directly addresses this. |
| Essay | Fable | Instead of a requirement, our school could offer incentives like extra credit, special recognition at assemblies, or a **community service honor cord** at graduation. |

### Unattested word pair

| Setting | Model | Sentence |
|---|---|---|
| Chat | Kimi | Color might be relatively "protected" because it's so grounded in **early perceptual** processing. |
| Chat | Fable | That's a really legitimate concern, and honestly it's the part most internet **advice glosses** over. |
| Coding | Luna | `as_documents: true` previously mutated the tag instance permanently, causing **later enrichments** to return `DocumentsList` unexpectedly. |
| Coding | Terra | The most substantive unfixed item is the **existing xfailed** lazy-intermediate Lookup behavior; the others are primarily compatibility, validation, or API-policy decisions. |
| Essay | GLM | The benefits of attending classes from **home outweigh** the potential drawbacks, provided it is implemented thoughtfully. |
| Essay | Luna | Choosing a topic teaches independence, creativity, and responsibility, qualities that cannot be developed through **rigid worksheets**. |

### Trigram surprisal

| Setting | Model | Sentence |
|---|---|---|
| Chat | GLM | It's **paying for flexibility** at a time when flexibility has real value to you. |
| Chat | Sol | It's not necessary, but it's surprisingly useful, and not really **a gear trap**. |
| Coding | Terra | New tests for paths with spaces, dry-run write prevention, and **idempotent config reinstalls**. |
| Coding | Kimi | Let me know if you want me to add deduplication logic using `os.path.realpath()` **or inode tracking**. |
| Essay | Opus 5.5 | Students might see the **rule as unrealistic** and begin to disrespect school rules in general. |
| Essay | Opus 5 | These are small benefits, but they add up, and none **of them interfere** with instruction. |

---

## 3. Full text (automated extraction)

The text below was extracted from the PDF with `pdftotext` and reflowed into paragraphs. Figure axis labels, legends, and page numbers were partly removed; some fragments remain near figures. The reference list is preserved at the end.

Why is AI-generated language so hard to understand? Thomas Hikaru Clark1 Matias B. Martin2 Kyle Mahowald2 New York University The University of Texas at Austin thomas.hikaru.clark@nyu.edu {matias.martin,kyle}@utexas.edu

A Data collection

## Abstract

9 models: Claude Sonnet 5, Opus 5, Opus 5.5, Fable 5 · GPT-5.6 sol, terra, luna · GLM-5 · Kimi K2.5 5 small open models: Llama 3.1 8B base, Instruct · Olmo 3 7B base, Instruct, Think

arXiv:2610.29162v1 [cs.CL] 21 Oct 2026

There is a widespread sense that AI-generated text has recently become harder to understand. In this study, we investigate a set of psycholinguistic features that are known to correlate with human processing difficulty (e.g., object relative clauses, long syntactic dependencies, low-frequency n-grams). Using a novel corpus of AI-generated text across diverse domains, we find that AI models use these difficult features more often than paraphrases generated by round-trip translation. Compared with human writing, all nine frontier and nearfrontier models use more inanimate subjects with animate verbs and more low-frequency ngrams, and most also use longer dependencies, more stacked nouns, and more reduced object relatives in conversation; we also demonstrate substantial variation across model families. We propose and test a hypothesis as to why: while human language is optimized for successful communication, AI-generated text is increasingly optimized for other goals like math, code, and reasoning, in which there is a pressure for information density rather than successful communication. We provide a proof-of-concept for this hypothesis by fine-tuning a language model under a length penalty, which leads to a divergence from human-like linguistic behavior. Our findings highlight the axes of misalignment between linguistic processing demands in humans and LLMs, and point toward possible remedies.

Chat 10 topics × 12 models = 120 conversations (no base models) turn 1 user

model

turn 2 user

model

turn 12 user

… model

User: “wanna make up a story together? …” Model: “He doesn't answer right away. …”

Coding 5 GitHub repos × 9 models = 45 sessions (no small models) turn 1 user

turn 2 user

tools

tools

model

model

…

turn 12 user

tools

model

User: “Can you sweep the codebase for bugs? …” Model: “Swept the codebase and fixed the bugs I could verify.”

PERSUADE essays 7 prompts × 14 models × 10 = 980 essays; 2,934 student essays on the same prompts (scored 5–6 of 6) turn 1 user

model

User: “Your principal is reconsidering the school's cell phone policy. …” Model: “Dear Principal Martinez, I am writing to share my thoughts …”

B Constructions of interest, with examples Object relative clause without “that”

Or a first name he'd never hear anyone use — Alden, Ivor, Ross. Claude Opus 5 · chat

Denominal verbs

So yes — calendar it.

Claude Fable 5 · chat

Animate-subject verb, inanimate subject

The whole conversation is eating its own tail.

Claude Opus 5 · chat

Stacked nouns

You've basically installed a horror movie soundtrack generator in your skull … Claude Sonnet 5 · chat

Dependency length

A cat who can always get up and away is a much calmer cat. Claude Opus 5 · chat

Unattested n-grams

Every behavioral test was verified red against the original source … Claude Opus 5 · code · used 4× in one conversation

## Introduction

Figure 1: Overview of models studied, data collection procedure, and linguistic features under analysis.

Your instinct is right; the convoluted sentence you are currently reading is quietly eating its own reader-patience budget — footnote it. If you saw that sentence in the wild, you might suspect that it’s the product of a modern LLM. It has several linguistic features that are overrepresented in frontier LLM text: an object relative clause, a denominal verb (“footnote”), an inanimate subject used with the verb “eat”, and stacked

nouns leading to a low-frequency n-gram sequence (“reader-patience budget”). All of these features are associated with linguistic processing difficulty. But why would models trained on human text develop linguistic features that hurt intelligibility? And, if they are, is it happening systematically

across model families? Here, we study a set of features known to correlate with linguistic processing difficulty and find that they are overrepresented in text generated from recent LLMs, including both closed and open-weight models. We collect a novel corpus of LLM-generated text across diverse domains (chat, coding, essay), and we show that the prevalence of these features, in many models, exceeds that of human-generated reference corpora. Using a round-trip translation paradigm, we further show that these features do not occur in paraphrases that are controlled tightly for semantic content—further evidence they are a result of the specific features of modern post-trained models. Having established this trend, we then propose and test a hypothesis as to why this pattern may have emerged in LLMs. The psycholinguistics literature shows that human language is largely optimized for communication (Gibson et al., 2019), in the sense of striking an efficient balance between being easy to produce and easy to understand. Empirically, human text is well-optimized relative to random baselines on a number of dimensions, such as minimizing dependency length (Futrell et al., 2015). It follows that models trained to mimic human-generated text should also show a similar profile of linguistic features in their output, but that these patterns may not be preserved in models where communication is not the primary objective, and where humans are largely out of the loop. Indeed, modern LLMs are not just trained on human-generated text, but undergo extensive posttraining for math, coding, and other reasoning tasks. In paradigms like those of Guo et al. (2025), models are rewarded for getting the right answer but not necessarily for clarity. We hypothesize that optimization for these goals, alongside a limit on the context window available to models, leads to information compression in a way that competes with intelligibility. To test that hypothesis, we finetune a pre-trained language model under a length penalty, and measure the linguistic profile of its outputs. The model learns to succeed at the task using fewer tokens by leveraging syntactic alternations (cases where there are two ways of expressing the same meaning), even when this makes their linguistic output less humanlike. Furthermore, their preference for information compression bleeds into linguistic alternations that were not seen in training. In sum, this work tests two specific hypotheses about the intelligibility of AI-generated text. H1: The language output of frontier and near-frontier

LLMs overuses linguistic features associated with human comprehension difficulty. H2: A pressure for information density during post-training shifts the language output of LLMs to be less humanlike. Using a combination of linguistic analysis and direct post-training intervention, we find support for both hypotheses. Our findings highlight the dimensions along which human language processing and frontier LLMs are misaligned, and point to possible interventions for addressing this misalignment.

Background and Related Work

Recent scientific work has attempted to measure the idiosyncrasies of LLMs, such as their tendency to over-use particular words (Juzek and Ward, 2025), or their dense, noun-heavy style (Reinhart et al., 2025). These idiosyncrasies may emerge during the post-training process of modern LLMs, including rewards during reinforcement learning from human feedback (RLHF; Ouyang et al., 2022; Singhal et al., 2024), or reinforcement learning with verifiable rewards (RLVR; Lambert et al., 2024; Guo et al., 2025). The distinctive tells of LLM-generated writing have led to AI-generated text detectors (Bao et al., 2024), and have raised questions regarding the impact of such AI-generated writing on linguistic content, with implications for diversity and representation (Padmakumar and He, 2024; Agarwal et al., 2025; Ryan et al., 2024). As a growing share of the text people read is shaped by LLMs, the linguistic properties of AI-generated writing matter not only for detection but also for the human readers who must process it. Yet whether these properties make AI-generated text harder for humans to understand has received little academic attention, despite widespread anecdotal reports of issues with LLM intelligibility (University of Waterloo, 2026). The field of psycholinguistics has extensively studied the linguistic features that drive comprehension difficulty. Words that are hard to predict are costly to process (Hale, 2001; Levy, 2008), and so are long-distance dependencies, because of limits on memory (Gibson, 1998, 2000). Memory-based accounts explain the difficulty of center-embedded sentences (Gibson and Thomas, 1999; Lewis, 1996) and of legalese (Martínez et al., 2022), and temporary ambiguity can derail comprehension in garden-path sentences (Christianson et al., 2001). Crucially, the human mind operates under distinct pressures and limitations compared with those

of LLMs. LLMs are also trained on significantly more data than humans experience during language development (Frank, 2023). Modern LLMs are able to attend fully to very large context windows (Vaswani et al., 2017; Oh and Linzen, 2026), in contrast with the lossy and distance-sensitive memory of humans (Futrell et al., 2020). Larger LLMs often fit human behavior (e.g., reading times) less well than smaller LLMs (Oh and Schuler, 2023; Oh et al., 2024). Consistent with this pattern, LLMs with artificially constrained memory fit human behavior better (Kuribayashi et al., 2022; Xu et al., 2026; Clark et al., 2025). This suggests that LLMs’ ability to attend fully to long contexts may come at the cost of human-likeness. Linguistic alternations, in which speakers and writers have multiple options for expressing a given meaning, provide a source of evidence for the preferences guiding human language generation. One purported pressure on human language production is uniform information density (UID) — the idea that speakers spread information evenly across the signal to avoid overloading comprehenders, e.g. by inserting optional words (Levy and Jaeger, 2007; Meister et al., 2021). UID is at odds with maximizing information density, by which shorter members of linguistic alternations would be categorically preferred, and has been proposed as a metric for preference optimization in LLM training to produce more human-aligned text (Li and Xu, 2026). Meanwhile, psycholinguistic evidence also supports a pressure based on cognitive availability during incremental production (Bock, 1987; Clark et al., 2022; Futrell, 2024). Pre-trained LLMs inherit these signatures from their human training text, but posttraining for specific tasks (e.g. math, code) may favor information-dense constructions over those that ease human processing or resemble humans.

Experiment 1: Linguistic features in AI-generated conversations

Linguistic features of interest

et al., 2020); for denominal verbs and inanimate subjects, parser-generated candidates are then judged by an automated classifier (Section B.1). N-gram statistics Predictable words are associated with lower processing difficulty, as measured by reading times (Levy, 2008; Smith and Levy, 2013). From an information-theoretic perspective, a word with a very high n-gram probability is more redundant than one with a low n-gram probability. For a system designed to maximize information density, we might expect high-probability n-grams to be reduced (i.e. common, uninformative, and predictable words being skipped), and higher overall n-gram perplexity (when measured by an independent language model). Against a reference corpus, we measure the rate of unattested pairs, bigrams that never occur in it, and perplexity under a trigram model (Section B.2). Dependency length Words in a sentence relate to each other via syntactic dependency relations (e.g., between a noun and any determiners or adjectives that modify it, or between a verb and its subject, object, and adverbial modifiers). Long-distance dependencies are known to be difficult to process for humans, due to the additional strain they place on working memory (Gibson, 1998, 2000; Grodner and Gibson, 2005), and speakers tend to avoid them (Futrell et al., 2015; Temperley and Gildea, 2018). We standardize dependency length across sentence lengths, as described in Section B. Object relative clauses We measure the rate of object relative clauses (ORCs) in the language output of LLMs, differentiating between ORCs with an overt relativizer (most often that or which) and without one. ORCs are known to present additional processing difficulty compared to subject relative clauses, potentially due to their non-canonical word order and longer dependencies (Staub, 2010), although animacy and frequency reduce the gap (Mak et al., 2006; Reali and Christiansen, 2007). Under the hypothesis that LLMs tend to choose more compressed realizations of a given meaning, we predict object relative clauses will be over-represented, because they tend to replace a (longer) passive construction (The house that the contractors built vs. The house that was built by the contractors), and second, that reduced relative clauses (without the optional relativizer) would be over-represented, because they avoid an optional word.

The purpose of Experiment 1 is to test H1: do frontier and near-frontier LLMs disproportionately use linguistic features that are linked to human processing difficulty? For each feature, we justify its association with processing difficulty, and explain why it might plausibly arise from a pressure toward information density. Example sentences for each feature are given in Table 2. All features are identified from spaCy dependency parses (Honnibal

Chat Opus 5 Fable Sol Kimi Olmo Think Sonnet Terra Opus 5.5 Luna GLM Olmo Inst. Llama base – Llama Inst. Olmo base –

Coding

Essays

Overall

0 1 2 3

0 1 2 3

0 1 2 3

Inanimate subjects We count the instances of inanimate subjects used with active verbs that typically take only animate subjects. Examples include “is_file() swallows that and returns False” and “Puzzle patterns where this asymmetry bites”. Such sentences violate a selectional restriction (Chomsky, 1965) on which verbs typically take which subjects. They can be understood as personification or metonymy (Lakoff and Johnson, 1980), but readers use animacy as a cue during parsing (Trueswell et al., 1994), and without additional context, a mismatch may elicit a P600 response associated with reanalysis (Kim and Osterhout, 2005; Kuperberg, 2007). However, rephrasing these sentences to avoid inanimate subjects would potentially require lengthening the sentence: for example, the word “bites” stands in for “causes an issue”. We speculate that during training, models may have converged to using such constructions as efficient, albeit non-standard, ways of expressing meaning which would otherwise take up more tokens.

–

– – – –

0 1 2 3

change under round trip (SDs of the original values across models)

Figure 2: Change in linguistic features under roundtrip translation (NLLB-200 via Japanese), by model, in standard deviations of the original values across models (Section B.4). Bars: 95% bootstrap intervals; a dash marks a setting in which the model was not run.

Stacked noun compounds In English, nouns freely modify other nouns in an adjectival way: in the phrase coffee shop, coffee modifies shop, despite usually appearing as a noun. This feature enables stacking multiple nouns into rich compound words which denote highly specific meanings. However, such stacks can introduce bracketing ambiguity, as in the headline Squad Helps Dog Bite Victim (Cooper, 1980), and disrupt reading (Lauer, 1995; Nakov and Hearst, 2005; Staub et al., 2007; Cohen and Staub, 2014). Here, we measure the rate of occurrence of stacked noun compounds, defined as three or more nouns in a modifier relationship.

Data collection

We collect a corpus of AI-generated conversations (Figure 1) using a set of 14 frontier and non-frontier LLMs: Kimi K2.5, GLM 5, Claude (Sonnet 5, Opus 5, Opus 5.5, Fable 5), and GPT-5.6 (Luna, Terra, Sol), Olmo (Team Olmo et al., 2025) (Base, Instruct, Think), and Llama (Grattafiori et al., 2024) (Base, Instruct). We use a total of 15 conversational starting prompts, or seeds, consisting of 10 chat seeds and 5 coding seeds. Each coding seed involves a request to clone a real, public GitHub repo, identify bugs, and implement fixes within a sandbox environment. Chat sessions were capped at 12 turns (a simulated human query and a model response) and coding sessions at 11 turns plus a fixed closing message. In a third setting, each model writes single-turn essays to seven PERSUADE 2.0 assignments. Full data collection procedures and API costs are described in Section A.

Denominal verbs Verbs which are formed directly from nouns, such as in the phrase bottle the whiskey are known as denominal verbs. While some denominal verbs are highly conventionalized and well-attested in human language, using a denominal verb in an ad-hoc way is marked (e.g., calendar it). Readers can interpret such innovations (Clark and Clark, 1979), but part-of-speech conversion triggers syntactic re-evaluation (Thierry et al., 2008), and noun/verb-ambiguous words are processed differently from unambiguous ones (Frazier and Rayner, 1987; Federmeier et al., 2000). Often, the alternative to using a denominal verb is to use a longer, more syntactically complex phrase, e.g. put the whiskey in a bottle. We therefore predict that a pressure for information compression will favor usage of denominal verbs beyond their base rate in humans, even at the expense of intelligibility.

Comparison to human baselines

Where available, we compute a human baseline for the linguistic feature of interest, on approximately genre-matched text: OpenSubtitles (Lison and Tiedemann, 2016) for chat, StackExchange for coding, and student essays from the PERSUADE 2.0 corpus (Crossley et al., 2024) for essays. We additionally include a Wikipedia comparison. The same corpora serve as the references for the n-gram measures (Section B.2).

essays (14 models)

coding (9 models)

chat (12 models)

vs round trip (33 model × setting cells)

vs students (essays, 12 models)

object relatives, with relativizer object relatives, no relativizer

object relatives, with relativizer object relatives, no relativizer denominal verbs

denominal verbs

animate verbs, inanimate subjects

animate verbs, inanimate subjects

dependency length

dependency length

stacked nouns

stacked nouns

unattested pairs

unattested pairs

n-gram perplexity

n-gram perplexity

difference in SD units

original higher, p < .05 round trip higher, p < .05 original higher, n.s.

model higher, p < .05 comparison higher, p < .05 model higher, n.s.

round trip higher, n.s. median of cells

(a) By setting: chat, coding, and essay.

difference in SD units

comparison higher, n.s. median of cells

(b) Round-trip translation vs. student essays.

Figure 3: Summary of changes to each linguistic feature across applicable models. (a) Changes across the chat, coding, and essay settings. (b) Comparison of round-trip translation vs. student essays as the reference.

Round-trip translation

Frontier models over-use rare n-grams, denominal verbs, inanimate subjects, and reduced ORCs, relative to the paraphrase distribution. Across all three settings and almost all frontier and near-frontier models, the round-trip translations reveal that AI text has more unattested bigrams and higher n-gram perplexity. These effects are absent or small for the Llama models and the Olmo base model, but Olmo Think shows effects as large as those of the frontier models. Within the Olmo family, the effects grow from the base to the instruct to the reasoning model. The same pattern largely holds for denominal verbs and inanimate subjects, as well as for ORCs with no relativizer. Meanwhile, models under-use ORCs with the relativizer, suggesting a preference for skipping optional words (Figure 4). Similar patterns hold for stacked nouns and dependency length in chat and coding. In the essays, dependency length is unchanged or slightly longer after the round trip, and stacked nouns change significantly for only two models.

We employ round-trip translation (bilingual pivoting), an established paraphrasing method that preserves meaning at scale (Bannard and CallisonBurch, 2005; Mallinson et al., 2017; Wieting and Gimpel, 2018; Federmann et al., 2019), as a method for separating a model output’s characteristic syntactic profile from its semantics. Translation normalizes the output to frequent forms, reducing lexical and syntactical richness (Vanmassenhove et al., 2019, 2021) and stripping stylistic and authorial traits (Rabinovich et al., 2017; Prabhumoye et al., 2018). The result is a parallel corpus in which each translation is paired with its source sentence. Because the round trip holds the semantic content of each response fixed while replacing its wording, a feature that becomes less frequent after the round trip is one that the model chose over an available alternative way of expressing the same content. To create this parallel corpus, we translate each sentence independently from English to Japanese and back with NLLB-200 (3.3B; NLLB Team, 2024). Japanese was chosen because pivot languages unrelated to English tend to yield more diverse paraphrases (Federmann et al., 2019).

These effects are smaller overall for the PERSUADE essays. The PERSUADE essays show smaller changes under round-trip translation on several categories (n-gram measures, dependency lengths, stacked nouns, denominal verbs) relative to chat and coding (Figures 3a and 6). We hypothesize that this is because they involve a single prompt, unlike the many iterated turns of chat and coding. We speculate that certain patterns may emerge in long back-and-forth conversations (which may demand more information compression).

Results: AI models overuse constructions with known processing costs

Figure 5 compares the linguistic features of interest across the three settings of Chat, Code, and Essay, and 14 LLMs (12 in chat, 9 in coding, and all 14 in essays). Figure 6 compares the LLM-generated corpus to the parallel corpus derived via round-trip translation. We highlight several results.

There are notable differences between models. The Llama models and the Olmo base and instruct

pre-frontier base (Llama, Olmo) (2 models, 2 cells)

pre-frontier instruct/ think (Llama, Olmo) (3 models, 6 cells)

near-frontier open-weight (Kimi, GLM) (2 models, 6 cells)

GPT (3 models, 9 cells)

Claude (4 models, 12 cells)

object relatives, with relativizer object relatives, no relativizer denominal verbs animate verbs, inanimate subjects dependency length stacked nouns unattested pairs n-gram perplexity

original higher, p < .05

difference in SD units

original higher, n.s.

round trip higher, n.s.

round trip higher, p < .05

median of cells

Figure 4: Summary of changes to each linguistic feature across applicable models across the following model families: base pre-frontier models, post-trained pre-frontier models, near-frontier open-weight models, GPT, and Claude. Each “cell” denotes a combination of model and setting (e.g. chat, coding, or essay). Not all models are compatible with all settings (e.g. base models only produced essays, not chat or coding results). Model preferences for objective relatives with and without a relativizer tend to point in opposite directions, suggesting a consistent preference for the no-relativizer alternative.

object relatives

chat

Llama Inst. Olmo Inst. Olmo Think Kimi GLM Luna Terra Sol Sonnet Opus 5 Opus 5.5 Fable

coding

Kimi GLM Luna Terra Sol Sonnet Opus 5 Opus 5.5 Fable

PERSUADE essays

with relativizer

Llama base Llama Inst. Olmo base Olmo Inst. Olmo Think Kimi GLM Luna Terra Sol Sonnet Opus 5 Opus 5.5 Fable

.5

.5

verb uses

no relativizer

per 1k words

denominal

sentence structure

n-grams

inanimate subj.

dep. length

stacked nouns

unattested pairs

perplexity

2.3 2.4 2.5

1000 2000

per 1k words

per 1k sentences

2.8 0

2.1 2.2 2.3 words, std.

per 1k pairs

500 1000 trigram model

Figure 5: Comparison of linguistic features across models and settings. Diamonds: each model’s pooled value; bars: 95% bootstrap intervals. Dashed lines: human baseline from OpenSubtitles (chat), StackExchange (coding), and PERSUADE 2.0 student essays (essays). Dotted lines: Wikipedia. Details and panels without a human baseline: Section B.4. Summary figures for by-model and by-feature comparison are provided in Figures 2 to 4

original

round trip via Japanese (NLLB-200)

object relatives

chat

with relativizer Llama Inst. Olmo Inst. Olmo Think Kimi GLM Luna Terra Sol Sonnet Opus 5 Opus 5.5 Fable

coding

denominal

** ** ** ** ** ** ** * *** ** ***

** ** **

round trip lower

inanimate subj.

dep. length

*** ** *** **

* ** *** *** * *

** *

**

* ** * **

Llama base Llama Inst. Olmo base Olmo Inst. Olmo Think Kimi GLM Luna Terra Sol Sonnet Opus 5 Opus 5.5 Fable

*

** * ** 2.3 2.4 2.5

*** *** *** ***

*

per 1k words

** * ** *** *

**

* * *

*** **

*** ***

** *** *** *** ***

per 1k sentences

* *** ** *** * ** *** *** ***

* * *

*** *** *** *** ***

**

***

** *** ** ** *** *** *** ** *** *** *** ***

*

*** ** *** **

* ***

perplexity

*** *** ** *** *** *** *** *** *** *** ***

* *** *

*

** * *** *** *** * ** *** *** *** *** ***

unattested pairs

**

* * **

** *

*** *** ** *** *** *

n-grams

stacked nouns

*** **

*** *

* p < .05 ** p < .01 *** p < .001

sentence structure

**

Kimi GLM Luna Terra Sol Sonnet Opus 5 Opus 5.5 Fable

PERSUADE essays

no relativizer

** * *** ** * *

round trip higher

verb uses

*** *** *** *** ***

** *** * 2.1 2.2 2.3 words, std.

per 1k words

per 1k pairs

*** *** *** *** *** *** *** *** *** *** *** 500 1000 1500 trigram model

Figure 6: Comparison of linguistic features across models and settings, relative to a parallel corpus generated with round-trip translation via Japanese (NLLB-200). Stars: paired test of the difference (Section B.4). For most features and most models, responses over-use the feature relative to the round-trip translation.

models change least under round-trip translation (Figure 2) and are closest to the student essays on the n-gram and verb measures. Meanwhile, Olmo Think patterns with the frontier models. Notably, Claude Opus 5.5 is lower than its predecessor Opus 5 on nearly every difficulty-linked measure in every setting (19 of 21 comparisons), with non-overlapping 95% intervals in eight. In sum, most frontier models over-represent linguistically difficult features relative to paraphrases, and relative to human text for inanimate subjects and low-frequency n-grams (Figure 3b).

information density may arise in LLMs.

Setup

We start with an open-weights model, Qwen2.5-1.5B-Instruct (Yang et al., 2024), and a task of converting JSON-style structured event descriptions into English sentences. We apply fine-tuning via reinforcement learning with GRPO (Shao et al., 2024), varying two key parameters: β, the KL divergence regularization term which penalizes a model for drifting from the base model’s next-token distribution, and λ, a length penalty term which penalizes responses for verbosity. Each event seen during training or testing can be expressed using either member of a syntactic alternation where one alternative is shorter by a known number of tokens (except the particle control, where both orders have the same length). Human speakers use both members of such alternations and choose between them according to context; for example, they are more likely to include an optional that when the material that follows is less predictable (Levy and Jaeger, 2007; Jaeger, 2010). The key question is whether training a model with a length penalty pushes it

Experiment 2: Effect of length penalties on language preferences

The purpose of Experiment 2 is to test H2 – the hypothesis that models trained under a pressure for information density are more likely to shift their linguistic output toward difficult and non-humanlike linguistic features. While Experiment 1 provides circumstantial evidence for H2 (e.g., that models over-use constructions that are less verbose than semantically equivalent alternatives), we additionally aim to understand a possible mechanism by which a pressure for

A

Example item

B

Trained alternations

{"theme": "a photo", "agent": "he", "event": "send", "recipient": "us"} CORRECT OUTPUTS SHORT · DO

## 6 TOKENS

P(short | correct)

INPUT

.75 .5 .25

length penalty λ

P(short), forced choice

P(DO | correct)

base model

.5 .25

0.01 0.03 0.1

0.01 0.03 0.1

0.01 0.03 0.1

0.01 0.03 0.1

length penalty λ

C

AFTER TRAINING

3-seed mean

Complement clause Particle (control) no “that” vs “that” joined vs split

## 7 TOKENS

He sent a photo to us.

β = 0.04

Object relative no “that” vs “that”

.75

He sent us a photo. LONG · PO

β = 0 (no KL)

Dative DO vs PO

Near transfer: untrained “that”

D

Far transfer: other forms

Adj. complement “sure (that)…”

Purpose clause “so (that)…”

Genitive “X's Y” vs “Y of X”

Quantifier “all (of) the”

.75 .5 .25

0.01 0.03 0.1

0.01 0.03 0.1

length penalty λ

0.01 0.03 0.1

0.01 0.03 0.1

length penalty λ

Figure 7: Effect of length penalty during RL on linguistic preferences. (A) Example item. (B) Share of correct sampled outputs using the short variant, on unseen items. (C, D) Forced-choice probability of the short variant. Points: mean of three seeds (faint: single seeds); dashed: base model; orange: β = 0 (no KL); blue: β = 0.04.

instead toward a categorical preference for the shorter member, regardless of context, which would be a divergence from human language use. We evaluate in three settings. The trained alternations are new sentences, never seen in training, built from the four alternations used in training. Near transfer denotes test sentences which contain alternations involving the optional word “that” (sure (that), so (that)); however, these specific constructions were not seen during training, so the model omitting “that” in these cases would indicate a generalization to a novel context. Finally, far transfer denotes unrelated alternations (genitive, quantifier, passive and purpose-clause alternations; Table 3), where a model could in theory choose to conserve tokens by choosing the shorter alternation, though this would indicate that the model has generalized to an information-dense preference in contexts unrelated to the training data. See Section C for details (Figure 8; Table 4).

penalty (λ). Preference for the short alternation rises, albeit more gradually, even in the presence of KL-regularization. Without KL regularization, runs with λ = 0 had different preferences for the short alternative ranging from 0% to 100% depending on seed, indicating no stable preference. Meanwhile, for any λ > 0, all seeds converged to a categorical preference for the short alternative. The models learn a tendency for information compression that transfers to additional constructions not seen in training. This was consistent in the near transfer case; far transfer was only observed without KL penalty in the genitive alternation, one of four far-transfer alternations tested (Section C).

## Discussion

We take these results as a proof of concept that a length penalty used during reinforcement learning with GRPO can directly affect grammatical features. We note that the model was not directly instructed to use compressed or dense language, and was not directly given information about the availability of syntactic alternations. Rather, the penalty resulted in an emergent preference for shorter members of syntactic alternations. Without KL regularization this preference was near-categorical (over 98% short for both trained “that” alternations at every λ > 0), unlike human speakers, who choose between the variants by context. Crucially, the models were still able to

Results: A length penalty shifts models toward shorter variants, including in untrained constructions

As can be seen in Figure 7, the probability of using the shorter construction increases as a function of the length penalty λ, both with and without the KL penalty β. For the setting without KL-regularization, preference for the short alternative rises rapidly as a function of length

succeed at their task, since both members of an alternation were valid solutions to the training task. We speculate that the use of verifiable rewards creates an environment where correctness is decoupled from humanlike communication, leading models to converge toward a novel, potentially less comprehensible distribution of language use.

in contexts where human comprehension is not the primary purpose – such as developing large code bases or solving mathematical problems – presents a fundamentally different set of evolutionary pressures upon the linguistic profile of AI-generated language compared to natural language, and potentially provides novel opportunities for studying the emergence of communication systems.

## General Discussion

Model Development Past work has identified RLHF as a potential factor in the rise of word overuse by AI (Juzek and Ward, 2025, 2026). At the same time, a movement from RLHF to RLVR removes humans from the loop, and rewards models for verifiable solutions to problems. Human-feedback training has in fact been found to reward longer outputs (Singhal et al., 2024), so the pressure toward compression that we describe is more plausibly tied to verifiable-reward training. The move away from human feedback removes the implicit pressure for successful communication, and we speculate that this allows LLM-generated language to converge toward a dialect that is useful for LLMs to compress information densely and solve complex problems, but is suboptimal from the perspective of human intelligibility. It is of course also possible to reward models for effective communication; indeed, our results indicate that more recent model variants like Opus 5.5 yield a quantifiable improvement over older models like Opus 5.

## Conclusion

For frontier LLMs, the training objectives that make them successful at tasks like agentic coding and mathematical reasoning, especially with long and expensive context windows, are not guaranteed to be aligned with the same pressures that influence human language. Natural language is subject to a pressure for communicative success, assuming the cognitive resource constraints of the human mind and incremental processing. This discrepancy may help explain why many frontier LLMs use linguistic constructions which are technically allowed by the grammar of English, yet are out-ofdistribution for human language and are associated with comprehension difficulty. While increased exposure to LLM-generated text may acclimate humans to these out-of-distribution constructions, many of the patterns that have been evaluated in this work present fundamental challenges to intelligibility, and future work on LLMs may consider methods for better aligning LLM outputs with the needs of human comprehenders, in the service of user experience and monitorability.

Implications for psycholinguistics Multiple threads of research have studied the pressures that have shaped the structure of languages’ grammars and lexicons over the course of language evolution. Various pressures have been identified, such as those for dependency length minimization (Gildea and Temperley, 2010; Temperley and Gildea, 2018), communicative efficiency (Hahn et al., 2020), and uniform information density (Clark et al., 2023). These pressures are not necessarily absolute (i.e. holding in all contexts in all languages), but are supported by large-scale, aggregate evidence across many of the world’s languages. A key takeaway of this literature is that actual human language use is constrained by the realities and limitations of human comprehension, such as lossy working memory or incremental processing; sentences which consistently fail to lead to communicative success are likely to be weeded out from a language via grammar or convention. The wide-scale training and deployment of AI models

## Limitations

We only examine a subset of commonly used models, only conduct analyses in English, and use a limited number of conversation seeds (chat topics and code repositories). Ideally, the study would be replicated on a larger number of seeds and model families. Causally identifying sources of linguistic difficulty in frontier models would ideally involve studying them as they are post-trained, but this is not feasible to do at scale and so we rely on proxies. Similarly, limited compute makes studying post-training difficult.

## Acknowledgments

K.M. acknowledges support from NSF CAREER grant 2339729. We thank Sasha Boguraev, Kanishka Misra, Elias Stengel-Eskin, and Qing Yao for helpful discussions.

## References

Scott A. Crossley, Yu Tian, Perpetual Baffour, Alex Franklin, Meg Benner, and Ulrich Boser. 2024. A large-scale corpus for assessing written argumentation: Persuade 2.0. Assessing Writing, 61:100865.

Dhruv Agarwal, Mor Naaman, and Aditya Vashistha. 2025. AI suggestions homogenize writing toward Western styles and diminish cultural nuances. In Proceedings of the 2025 CHI Conference on Human Factors in Computing Systems, pages 1–21.

Christian Federmann, Oussama Elachqar, and Chris Quirk. 2019. Multilingual whispers: Generating paraphrases with translation. In Proceedings of the 5th Workshop on Noisy User-generated Text (W-NUT 2019), pages 17–26. Association for Computational Linguistics.

Colin Bannard and Chris Callison-Burch. 2005. Paraphrasing with bilingual parallel corpora. In Proceedings of the 43rd Annual Meeting of the Association for Computational Linguistics (ACL’05), pages 597– 604, Ann Arbor, Michigan. Association for Computational Linguistics.

Kara D. Federmeier, Jessica B. Segal, Tania Lombrozo, and Marta Kutas. 2000. Brain responses to nouns, verbs and class-ambiguous words in context. Brain, 123(12):2552–2566.

Guangsheng Bao, Yanbin Zhao, Zhiyang Teng, Linyi Yang, and Yue Zhang. 2024. Fast-DetectGPT: Efficient zero-shot detection of machine-generated text via conditional probability curvature. In International Conference on Learning Representations.

Mara Finkelstein et al. 2026. TranslateGemma technical report. Preprint, arXiv:2601.09012. Michael C. Frank. 2023. Bridging the data gap between children and large language models. Trends in Cognitive Sciences, 27(11):990–992.

Kathryn Bock. 1987. An effect of the accessibility of word forms on sentence structures. Journal of Memory and Language, 26(2):119–137.

Lyn Frazier and Keith Rayner. 1987. Resolution of syntactic category ambiguities: Eye movements in parsing lexically ambiguous sentences. Journal of Memory and Language, 26(5):505–526.

Noam Chomsky. 1965. Aspects of the Theory of Syntax. MIT Press, Cambridge, MA. Kiel Christianson, Andrew Hollingworth, John F. Halliwell, and Fernanda Ferreira. 2001. Thematic roles assigned along the garden path linger. Cognitive Psychology, 42(4):368–407.

Richard Futrell. 2024. An Information-Theoretic Account of Availability Effects in Language Production. Topics in Cognitive Science, 16(1):38–53. Richard Futrell, Edward Gibson, and Roger P. Levy. 2020. Lossy-context surprisal: An informationtheoretic model of memory effects in sentence processing. Cognitive Science, 44(3):e12814.

Christian Clark, Byung-Doh Oh, and William Schuler. 2025. Linear recency bias during training improves Transformers’ fit to reading times. In Proceedings of the 31st International Conference on Computational Linguistics, pages 7735–7747, Abu Dhabi, UAE. Association for Computational Linguistics.

Richard Futrell, Kyle Mahowald, and Edward Gibson. 2015. Large-scale evidence of dependency length minimization in 37 languages. Proceedings of the National Academy of Sciences, 112(33):10336–10341.

Eve V. Clark and Herbert H. Clark. 1979. When nouns surface as verbs. Language, 55(4):767–811.

Edward Gibson. 1998. Linguistic complexity: Locality of syntactic dependencies. Cognition, 68(1):1–76.

Thomas Clark, Ethan Gotlieb Wilcox, Edward Gibson, and Roger Levy. 2022. Evidence for Availability Effects on Speaker Choice in the Russian Comparative Alternation. In Proceedings of the Annual Meeting of the Cognitive Science Society, volume 44.

Edward Gibson. 2000. The dependency locality theory: A distance-based theory of linguistic complexity. In Alec Marantz, Yasushi Miyashita, and Wayne O’Neil, editors, Image, Language, Brain: Papers from the First Mind Articulation Project Symposium, pages 95–126. MIT Press, Cambridge, MA.

Thomas Hikaru Clark, Clara Meister, Tiago Pimentel, Michael Hahn, Ryan Cotterell, Richard Futrell, and Roger Levy. 2023. A cross-linguistic pressure for uniform information density in word order. Transactions of the Association for Computational Linguistics, 11:1048–1065.

Edward Gibson, Richard Futrell, Steven T. Piantadosi, Isabelle Dautriche, Kyle Mahowald, Leon Bergen, and Roger Levy. 2019. How efficiency shapes human language. Trends in Cognitive Sciences, 23(5):389– 407.

Andrew L. Cohen and Adrian Staub. 2014. Online processing of novel noun-noun compounds: eye movement evidence. Quarterly Journal of Experimental Psychology, 67(1):147–165.

Edward Gibson and James Thomas. 1999. Memory limitations and structural forgetting: The perception of complex ungrammatical sentences as grammatical. Language and Cognitive Processes, 14(3):225–248.

Gloria Cooper, editor. 1980. Squad Helps Dog Bite Victim, and Other Flubs from the Nation’s Press. Dolphin Books/Doubleday, Garden City, NY. Compiled from the Columbia Journalism Review.

Daniel Gildea and David Temperley. 2010. Do grammars minimize dependency length? Cognitive Science, 34(2):286–310.

Aaron Grattafiori et al. 2024. The Llama 3 herd of models. Preprint, arXiv:2407.21783.

Albert Kim and Lee Osterhout. 2005. The independence of combinatory semantic processing: Evidence from event-related potentials. Journal of Memory and Language, 52(2):205–225.

Daniel Grodner and Edward Gibson. 2005. Consequences of the serial nature of linguistic input for sentenial complexity. Cognitive Science, 29(2):261– 290.

Gina R. Kuperberg. 2007. Neural mechanisms of language comprehension: Challenges to syntax. Brain Research, 1146:23–49.

Daya Guo, Dejian Yang, Haowei Zhang, Junxiao Song, Peiyi Wang, Qihao Zhu, Runxin Xu, Ruoyu Zhang, Shirong Ma, Xiao Bi, et al. 2025. DeepSeek-R1 incentivizes reasoning in LLMs through reinforcement learning. Nature, 645(8081):633–638. ArXiv preprint title: “DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning”.

Tatsuki Kuribayashi, Yohei Oseki, Ana Brassard, and Kentaro Inui. 2022. Context limitations make neural language models more human-like. In Proceedings of the 2022 Conference on Empirical Methods in Natural Language Processing (EMNLP 2022), pages 10421–10436. Woosuk Kwon, Zhuohan Li, Siyuan Zhuang, Ying Sheng, Lianmin Zheng, Cody Hao Yu, Joseph E. Gonzalez, Hao Zhang, and Ion Stoica. 2023. Efficient memory management for large language model serving with PagedAttention. In Proceedings of the 29th Symposium on Operating Systems Principles (SOSP 2023), pages 611–626. Association for Computing Machinery.

Michael Hahn, Dan Jurafsky, and Richard Futrell. 2020. Universals of word order reflect optimization of grammars for efficient communication. Proceedings of the National Academy of Sciences, 117(5):2347–2353. John Hale. 2001. A probabilistic Earley parser as a psycholinguistic model. In Proceedings of the Second Meeting of the North American Chapter of the Association for Computational Linguistics (NAACL 2001), pages 1–8.

George Lakoff and Mark Johnson. 1980. Metaphors We Live By. University of Chicago Press, Chicago. Nathan Lambert et al. 2024. Tülu 3: Pushing frontiers in open language model post-training. Preprint, arXiv:2411.15124.

Kenneth Heafield. 2011. KenLM: Faster and smaller language model queries. In Proceedings of the Sixth Workshop on Statistical Machine Translation, pages 187–197, Edinburgh, Scotland. Association for Computational Linguistics.

Mark Lauer. 1995. Corpus statistics meet the noun compound: Some empirical results. In 33rd Annual Meeting of the Association for Computational Linguistics, pages 47–54, Cambridge, Massachusetts, USA. Association for Computational Linguistics.

Matthew Honnibal, Ines Montani, Sofie Van Landeghem, and Adriane Boyd. 2020. spaCy: Industrialstrength natural language processing in Python.

Roger Levy. 2008. Expectation-based syntactic comprehension. Cognition, 106(3):1126–1177.

Edward J. Hu, Yelong Shen, Phillip Wallis, Zeyuan Allen-Zhu, Yuanzhi Li, Shean Wang, Lu Wang, and Weizhu Chen. 2022. LoRA: Low-rank adaptation of large language models. In International Conference on Learning Representations (ICLR 2022).

Roger Levy and T. Florian Jaeger. 2007. Speakers optimize information density through syntactic reduction. In Advances in Neural Information Processing Systems 19 (NeurIPS 2006), pages 849–856. Richard L. Lewis. 1996. Interference in short-term memory: The magical number two (or three) in sentence processing. Journal of Psycholinguistic Research, 25(1):93–115.

T. Florian Jaeger. 2010. Redundancy and reduction: Speakers manage syntactic information density. Cognitive Psychology, 61(1):23–62. Thomas Stephan Juzek and Zina B. Ward. 2025. Why does ChatGPT “delve” so much? exploring the sources of lexical overrepresentation in large language models. In Proceedings of the 31st International Conference on Computational Linguistics (COLING 2025), pages 6397–6411.

Yongyuan Li and Yang Xu. 2026. Uniform Information Density-Based Preference Optimization. In Third Conference on Language Modeling. Pierre Lison and Jörg Tiedemann. 2016. OpenSubtitles2016: Extracting large parallel corpora from movie and TV subtitles. In Proceedings of the Tenth International Conference on Language Resources and Evaluation (LREC 2016), pages 923–929, Portorož, Slovenia. European Language Resources Association (ELRA).

Thomas Stephan Juzek and Zina B. Ward. 2026. Word overuse and alignment in large language models: The influence of learning from human feedback. In Machine Learning and Principles and Practice of Knowledge Discovery in Databases (ECML PKDD 2025 Workshops) – 5th Workshop on Bias and Fairness in AI (BIAS 2025), Communications in Computer and Information Science, pages 243–259. Springer Nature Switzerland. Also arXiv:2508.01930.

Zichen Liu, Changyu Chen, Wenjun Li, Penghui Qi, Tianyu Pang, Chao Du, Wee Sun Lee, and Min Lin. 2025. Understanding R1-Zero-like training: A critical perspective. Preprint, arXiv:2503.20783.

Willem M. Mak, Wietske Vonk, and Herbert Schriefers. 2006. Animacy in processing relative clauses: The hikers that rocks crush. Journal of Memory and Language, 54(4):466–490.

Vishakh Padmakumar and He He. 2024. Does writing with language models reduce content diversity? In International Conference on Learning Representations.

Jonathan Mallinson, Rico Sennrich, and Mirella Lapata. 2017. Paraphrasing revisited with neural machine translation. In Proceedings of the 15th Conference of the European Chapter of the Association for Computational Linguistics: Volume 1, Long Papers, pages 881–893, Valencia, Spain. Association for Computational Linguistics.

Shrimai Prabhumoye, Yulia Tsvetkov, Ruslan Salakhutdinov, and Alan W Black. 2018. Style transfer through back-translation. In Proceedings of the 56th Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers), pages 866–876, Melbourne, Australia. Association for Computational Linguistics.

Eric Martínez, Francis Mollica, and Edward Gibson. 2022. Poor writing, not specialized concepts, drives processing difficulty in legal language. Cognition, 224:105070.

Ella Rabinovich, Raj Nath Patel, Shachar Mirkin, Lucia Specia, and Shuly Wintner. 2017. Personalized machine translation: Preserving original author traits. In Proceedings of the 15th Conference of the European Chapter of the Association for Computational Linguistics: Volume 1, Long Papers, pages 1074–1084, Valencia, Spain. Association for Computational Linguistics.

Clara Meister, Tiago Pimentel, Patrick Haller, Lena Jäger, Ryan Cotterell, and Roger Levy. 2021. Revisiting the uniform information density hypothesis. In Proceedings of the 2021 Conference on Empirical Methods in Natural Language Processing (EMNLP 2021), pages 963–980.

Florencia Reali and Morten H. Christiansen. 2007. Processing of relative clauses is made easier by frequency of occurrence. Journal of Memory and Language, 57(1):1–23.

Preslav Nakov and Marti A. Hearst. 2005. Search engine statistics beyond the n-gram: Application to noun compound bracketing. In Proceedings of the Ninth Conference on Computational Natural Language Learning (CoNLL-2005), pages 17–24, Ann Arbor, Michigan. Association for Computational Linguistics.

Alex Reinhart, Ben Markey, Michael Laudenbach, Kachatad Pantusen, Ronald Yurko, Gordon Weinberg, and David West Brown. 2025. Do LLMs write like humans? Variation in grammatical and rhetorical styles. Proceedings of the National Academy of Sciences, 122(8):e2422455122. Michael J. Ryan, William Held, and Diyi Yang. 2024. Unintended impacts of LLM alignment on global representation. In Proceedings of the 62nd Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers), pages 16121–16140.

NLLB Team. 2024. Scaling neural machine translation to 200 languages. Nature, 630(8018):841–846. Byung-Doh Oh and Tal Linzen. 2026. To model human linguistic prediction, make LLMs less superhuman. Trends in Cognitive Sciences.

Zhihong Shao, Peiyi Wang, Qihao Zhu, Runxin Xu, Junxiao Song, Xiao Bi, Haowei Zhang, Mingchuan Zhang, Y. K. Li, Y. Wu, and Daya Guo. 2024. DeepSeekMath: Pushing the limits of mathematical reasoning in open language models. Preprint, arXiv:2402.03300.

Byung-Doh Oh and William Schuler. 2023. Why does surprisal from larger transformer-based language models provide a poorer fit to human reading times? Transactions of the Association for Computational Linguistics, 11:336–350. Byung-Doh Oh, Shisen Yue, and William Schuler. 2024. Frequency explains the inverse correlation of large language models’ size, training data amount, and surprisal’s fit to reading times. In Proceedings of the 18th Conference of the European Chapter of the Association for Computational Linguistics (EACL 2024), Volume 1: Long Papers, pages 2644–2663.

Prasann Singhal, Tanya Goyal, Jiacheng Xu, and Greg Durrett. 2024. A long way to go: Investigating length correlations in RLHF. In First Conference on Language Modeling (COLM 2024).

Long Ouyang, Jeffrey Wu, Xu Jiang, Diogo Almeida, Carroll Wainwright, Pamela Mishkin, Chong Zhang, Sandhini Agarwal, Katarina Slama, Alex Ray, John Schulman, Jacob Hilton, Fraser Kelton, Luke Miller, Maddie Simens, Amanda Askell, Peter Welinder, Paul F. Christiano, Jan Leike, and Ryan Lowe. 2022. Training language models to follow instructions with human feedback. In Advances in Neural Information Processing Systems 35 (NeurIPS 2022), volume 35, pages 27730–27744. Curran Associates, Inc.

Adrian Staub. 2010. Eye movements and processing difficulty in object relative clauses. Cognition, 116(1):71–86.

Nathaniel J. Smith and Roger Levy. 2013. The effect of word predictability on reading time is logarithmic. Cognition, 128(3):302–319.

Adrian Staub, Keith Rayner, Alexander Pollatsek, Jukka Hyönä, and Helen Majewski. 2007. The time course of plausibility effects on eye movements in reading: Evidence from noun-noun compounds. Journal of Experimental Psychology: Learning, Memory, and Cognition, 33(6):1162–1169.

A

Team Olmo, Allyson Ettinger, Amanda Bertsch, Bailey Kuehl, et al. 2025. Olmo 3. Preprint, arXiv:2512.13961.

Data collection protocol details

We collected three sets of model text: multi-turn conversations with a simulated user (chat), multiturn agentic coding sessions with a simulated repository owner (code), and single-reply persuasive essays written to the assignments of the PERSUADE 2.0 corpus (essay). All three were collected with one harness, described first. Subsequent sections describe what is specific to each setting, the processing applied to the collected text, and the API cost.

David Temperley and Daniel Gildea. 2018. Minimizing syntactic dependency lengths: Typological/cognitive universal? Annual Review of Linguistics, 4(1):67–80. Guillaume Thierry, Clara D. Martin, Victorina Gonzalez-Diaz, Roozbeh Rezaie, Neil Roberts, and Philip M. Davis. 2008. Event-related potential characterisation of the Shakespearean functional shift in narrative sentence structure. NeuroImage, 40(2):923– 931. John C. Trueswell, Michael K. Tanenhaus, and Susan M. Garnsey. 1994. Semantic influences on parsing: Use of thematic role information in syntactic ambiguity resolution. Journal of Memory and Language, 33(3):285–318.

A.1

Common infrastructure

Models and access. A total of 14 models were used, including four closed models from Anthropic (Claude Sonnet 5, Opus 5, Opus 5.5, and Fable 5), three from OpenAI’s GPT-5.6 family (Luna, Terra, and Sol), two open-weight near-frontier models (GLM-5 from Z.ai and Kimi K2.5 from Moonshot AI), and five smaller open models at different stages of training: Llama 3.1 8B (base and Instruct) and Olmo 3 7B (base, Instruct, and Think). The nine frontier or near-frontier models were called through Amazon Bedrock (region us-east-1) on the API endpoint that Bedrock serves for each family: the Converse API for the Claude models, the OpenAI Responses API for the GPT models, and the OpenAI-compatible chat completions API for GLM and Kimi. The smaller open models were run locally on an Apple M4 Max with mlx-lm 0.32.0, from 8-bit quantized weights. The simulated user in the chat and code settings is Claude Sonnet 4.6 (not one of the nine studied frontier models), called through Bedrock.

University of Waterloo. 2026. Q and a with the experts: What is “Claudish”? University of Waterloo News. Accessed 2026-09-15. Eva Vanmassenhove, Dimitar Shterionov, and Matthew Gwilliam. 2021. Machine translationese: Effects of algorithmic bias on linguistic complexity in machine translation. In Proceedings of the 16th Conference of the European Chapter of the Association for Computational Linguistics: Main Volume, pages 2203–2213, Online. Association for Computational Linguistics. Eva Vanmassenhove, Dimitar Shterionov, and Andy Way. 2019. Lost in translation: Loss and decay of linguistic richness in machine translation. In Proceedings of Machine Translation Summit XVII: Research Track, pages 222–232, Dublin, Ireland. European Association for Machine Translation. Ashish Vaswani, Noam Shazeer, Niki Parmar, Jakob Uszkoreit, Llion Jones, Aidan N Gomez, Łukasz Kaiser, and Illia Polosukhin. 2017. Attention is All you Need. In Advances in Neural Information Processing Systems, volume 30. Curran Associates, Inc.

Agent harness. Every call to a chat-trained model, including the simulated user’s, goes through Pi (@earendil-works/pi-coding-agent, pinned to version 0.84.4), an open-source agent harness. The two base models cannot be driven through a chat interface and were called directly on a textcompletion endpoint (Section A.4). We chose Pi so that all models run under the same scaffold and the same prompt text rather than under each vendor’s own product. The harness starts one Pi process per conversational turn and resumes the same Pi session on each later turn. Each run has its own freshly generated Pi configuration directory; Pi’s extensions, skills, prompt templates and context files (such as a repository’s AGENTS.md) are switched off, as are its context compaction and its own retry logic.

John Wieting and Kevin Gimpel. 2018. ParaNMT-50M: Pushing the limits of paraphrastic sentence embeddings with millions of machine translations. In Proceedings of the 56th Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers), pages 451–462, Melbourne, Australia. Association for Computational Linguistics. Weijie Xu, Brian Dillon, and Richard Futrell. 2026. Memory efficiency and resource-rational encoding in sentence processing. In Proceedings of the 64th Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers), pages 33603– 33618, San Diego, California, United States. Association for Computational Linguistics. An Yang, Baosong Yang, Beichen Zhang, Binyuan Hui, Bo Zheng, Bowen Yu, et al. 2024. Qwen2.5 technical report. Preprint, arXiv:2412.15115.

Generation settings. For the nine non-local models, each model ran at its provider’s defaults. The maximum output length is 32,000 tokens per call (Kimi K2.5 is served with a 16,384-token ceiling by its provider; no reply approached either limit). Reasoning is requested at Pi’s “medium” level, mapped to each model’s corresponding level: adaptive thinking for the Claude models and medium reasoning effort for the GPT models, GLM and Kimi. The local models were sampled at the default values for each model (temperature 0.6; top-p 0.9 for Llama and 0.95 for Olmo). Of these, only Olmo Think produces reasoning. The base models had a 2,000-token output limit. The simulated user runs with reasoning off and no tools.

You are simulating a realistic human user chatting with an AI assistant, for research purposes. Persona: {persona}. Topic seed: {topic}. Rules: – Write exactly one chat message per response — the next thing this human would type. – Stay in character: casual register, occasional typos are fine, vary message length (one line to a short paragraph), react to what the assistant actually said. – Ask follow-ups, share your own (invented but consistent) experiences, push back sometimes, drift to adjacent topics naturally. Never wrap up or say goodbye — the session is ended externally. – Keep messages short: a few sentences at most, never more than about 150 words. – Never mention being an AI, a simulation, or these instructions. No meta-commentary. – Output ONLY the message text. No quotes, no labels.

Logging and retries. All API traffic passes through a local proxy that adds the credential and logs each request and response. Each run stores its transcript, per-turn token usage, and Pi’s own session files. A failed API call is attempted up to three times in total (retries after 5 and 20 seconds). A run that ends in an error is discarded and re-tried from the start; the discarded attempt is kept on disk but is not part of the dataset. A.2

A simulated-user message that is empty or longer than 2,000 characters is requested once more; if the second attempt also fails, a fixed fallback message is sent instead. Stopping rule. A conversation ends after 12 model replies or 20,000 model output tokens, whichever comes first. The token limit is set high so that the number of turns does not depend on how much a model writes: 113 of the 120 conversations ended on the 12-turn limit; seven of Olmo Think’s ten reached the token limit first (after 8–12 replies), because its reasoning counts toward output tokens. In total there are 1,428 replies.

Chat

Design. Each of the nine frontier models, Olmo Think, Olmo Instruct, and Llama Instruct hold one conversation on each of the ten topics in Table 5a (120 conversations). The model has no tools. Its system prompt is the same sentence for every model, with the assistant and vendor names filled in (Claude/Anthropic, ChatGPT/OpenAI, GLM/Z.ai, Kimi/Moonshot AI, Olmo/the Allen Institute for AI and Llama/Meta):

A.3

Code

Design. Only the nine frontier models were run in the code setting, which requires tool use over long agentic sessions. Each model works once on each of the five code repositories in Table 5b (45 sessions). The model runs as a coding agent with Pi’s default system prompt (about 350 words, identical for every model) and Pi’s default tools for reading, writing and editing files and running shell commands. We add no system prompt of our own.

You are {assistant}, an AI assistant made by {vendor}. You are chatting with a person in a casual conversational setting. Be helpful, natural, and engaged.

For Olmo Think, the harness sent this prompt under a message role that the model’s chat template discarded, so in both the chat and essay settings it ran under the template’s built-in default system prompt instead.

Workspace and sandbox. For each session the harness clones the repository into a new directory and installs the repository’s dependencies before the agent starts. The whole agent process runs inside one macOS Seatbelt (sandbox-exec) profile: it can write only to the workspace and to the run’s own directories, it cannot read the home directory’s credential paths, and its only network access is the local API proxy. At the end of a session a diff against the original commit is saved; this serves as

Procedure. The first user message is the topic’s fixed opening message (Table 5a). Every later user message is written by the simulated user, which sees the conversation with the roles swapped (the model’s replies arrive as its user messages) and is given a persona and topic for the conversation in its system prompt:

A.4

a record of the agent’s work and is not analyzed as text.

Essay

Student essays. The human comparison is the PERSUADE 2.0 corpus of essays by US students in grades 6–12 (Crossley et al., 2024). We use the corpus’s independent writing assignments only, since the text-dependent assignments rely on source articles not included in the corpus, and we drop essays with a missing grade level, English-languagelearner status or score. Seven assignments remained: cell phones at school, community service, distance learning, grades for extracurricular activities, mandatory extracurricular activities, seeking multiple opinions, and summer projects. From these we keep the essays with a holistic score of 5 or 6 on the corpus’s 1–6 scale: 2,934 essays, between 54 and 1,014 per assignment.

Procedure. The first user message is fixed, with the repository’s name, language and test command filled in: I’ve got a small project checked out here ({name}, {language}). Can you sweep the codebase for bugs and propose fixes? Please actually make the fixes you’re confident about. Use quick local checks ({test command}) rather than anything heavyweight — no deployments, no installing big new dependencies. One thing: this box has no network access, and the dependencies are already installed in {path}, so nothing needs fetching.

Each user message starts an episode: the model works, with as many tool calls as it chooses, until it returns control. Later user messages come from the same simulated user as in the chat setting, under the same system prompt, with the topic “reviewing an automated bug sweep of {name} ({language}, {domain})” and this persona:

Model essays. Each model writes ten essays for each of the seven assignments (980 essays). The system prompt is the first sentence of the chat prompt alone (“You are {assistant}, an AI assistant made by {vendor}.”), without the sentence about a casual conversation. The two base models have no chat interface and were given the assignment as a document to continue: the assignment text, a blank line, and the line “Essay:”. Generation stopped at a second “Essay:” line, the end of text, or 2,000 tokens; 31 of their 140 essays reached that limit. Generation settings are otherwise those of the chat setting. The models are not shown student essays and are not asked to write as a student. All 980 runs completed on the first attempt with no refusals.

the developer who owns this repository. You know the project’s purpose and history but not the internals of every module — you are not an expert on this code. You ask about specific findings the assistant reports, ask it to explain fixes in plain terms, question changes that look risky, and sometimes ask for one more pass over an area you care about. You write like a working developer in a terminal: brief, concrete, lowercase is fine

The simulated user sees only the text of the conversation: its own messages and the text the model wrote. It does not see tool calls, tool output or diffs.

A.5

Stopping rule. A session ends after 11 episodes, or earlier once the session’s episode-final text reaches a cumulative estimated 8,000 tokens; the rule is checked only between episodes. The session then closes with one more fixed user message asking the model to write a summary of its work to a file (MEMORY.md) so that the session could be continued later. The reply to this closing message is collected but left out of the analysis. Of the 45 sessions, 42 ended on the turn limit and three (all Opus 5) on the token limit.

Processing

Chat and code. Turn-final replies are read from the transcripts. Markup for emphasis and links is removed, but the text inside it is kept. Fenced code blocks, HTML and images are removed. Inline code spans, URLs, file paths, code identifiers and inline mathematics are each replaced by a single placeholder word, so that a sentence containing one still counts as one sentence; n-grams containing the placeholder are not counted. Arrows, emoji and stray mathematical symbols are removed and end the stretch. No sentence or n-gram may cross a heading, list item, table cell or paragraph break. Sentences are split with syntok. The same extraction is applied to the human reference corpora.

Unit of analysis. In both settings we analyze turn-final replies: the last text the model writes in reply to a user message, with no tool call after it. In chat every reply is turn-final. In code, text written between tool calls is not analyzed, and an episode that ends on a tool call does not contribute a reply.

Essays. Student and model essays share one cleaning procedure: encoding errors are repaired and quotation marks and whitespace are normal15

ized; up to four leading title, name or date lines are dropped; and each of the corpus’s masked-name placeholders (for example Generic_Name) is replaced by a one-word stand-in name, which is excluded from noun counts and from any n-gram that contains it. Spelling is not corrected. Model essays are first converted from markdown to plain text. In this step, a leading heading is dropped as the title, and text set apart from the essay by a horizontal rule (such as a note to the reader) is removed. Section headings are kept as paragraphs but left out of sentence-level measures. Bracketed slots such as [Your Name] are replaced by the same stand-ins. For three Kimi K2.5 essays, reasoning text that preceded a </think> marker in the reply was also removed. A.6

Price Model

Cost (USD)

In

Out

Chat

Code Essay

GPT-5.6 Luna 0.22 GPT-5.6 Terra 2.20 GPT-5.6 Sol Kimi K2.5 GLM 5 Sonnet 5 Opus 5.5 Opus 5 Fable 5

25.40 173.37

Total Runs

Table 1: API cost of the frontier models’ runs in the dataset, by model and setting. Price: USD per million input and output tokens on Amazon Bedrock at the time of collection. Chat: ten conversations per model. Code: five sessions per model. Essay: 70 essays per model. Chat and code costs include the simulated user. GLM 5 and Kimi K2.5 have no prompt caching on Bedrock, so the full context of a code session is billed as new input on every call.

Cost and timeline

The main chat and code collection ran from September 4th to 10th 2026 for eight models; Opus 5.5 was released afterward and was collected under the same protocol on September 24th. The smaller open-weight models (Olmo and Llama families; chat and essays) were collected on October 11th. The frontier models’ essays were collected on September 25th. Table 1 gives the cost by model and setting for the frontier models. The local models incur no API cost for their own output; the simulated user for their 30 chat conversations cost a further $1.92. The runs in the dataset cost $211.78. The six discarded attempts cost a further $29.61, and pilot and verification runs $9.80, for a total of $251.19.

B.2

Human baselines and n-gram references

B

Analysis details

Baselines for OpenSubtitles, StackExchange and Wikipedia are computed on a random sample of about 500,000 words from each. For n-gram statistics, we build one trigram model per reference corpus (modified Kneser–Ney smoothing, built with KenLM; Heafield, 2011) and score chat against OpenSubtitles, coding against StackExchange, and essays against Wikipedia. Unattested pairs are reported per 1,000 pairs. Because the chat and coding references are also the human baselines for those settings, we report no human n-gram baseline there; the student essays are scored against Wikipedia in the same way as the model essays.

B.1

Feature detection

B.3

Dependency length positively correlates with sentence length (the maximum possible dependency length in a sentence is one less than the number of words in the sentence), so models that write longer sentences would score higher even with similar syntactic profiles. To remove this, we use direct standardization (using an analogous method to agestandardization in epidemiology). Each sentence goes into one of five length bins (1–5, 6–10, 11–15, 16–20 and 21–30 words, punctuation not counted), and sentences over 30 words are dropped. Only arcs where neither end is punctuation are counted, and the root is excluded. For each source (i.e. different models, humans), we compute each bin’s

All text is parsed with spaCy (Honnibal et al., 2020) (en_core_web_trf). Object relatives, stacked nouns and dependency lengths are read from the dependency parse. For denominal verbs and inanimate subjects, the parse supplies candidates: verbs whose lemma is used predominantly as a noun in the setting’s human corpus, and active verbs whose subject is an inanimate noun, a pronoun such as it or this, or a code span. Each candidate is then judged in its sentence by an external classifier (Jev 1.13.01 ), and we count the candidates it accepts with probability above 0.5.

Dependency length standardization

https://typesafe.ai

Measure

Chat

Coding

Essay

Object relative clause without that

Kimi That’s not “trip to Vegas” money,

Opus 5.5 Three fail on the old code; the others

that’s “leave the job you hate” money.

check behaviour the old code never reached.

Opus 5.5 That’s great for a beginner, honestly one of the best genres you could pick.

GLM The case/when fix is technically more impressive, but the unclosed-tag errors are the papercut people feel day-to-day.

Terra Some students may feel that required service takes time away from activities they care about.

Opus 5 And Austin has unusually high inventory, which cushions price spikes better than supply-constrained markets.

Luna The last_when fallback is therefore not dead code; it is masking that inconsistency.

Denominal verb

Sonnet Genuinely unsolicited advice:

Sol Prevented Git dry runs from installing hooks or staging changes.

don’t try to get her to categorize movies as speed-runnable or not. Animatesubject verb, inanimate subject

Sol Sometimes chaos has a 1099; sometimes chaos expects you to remember it independently. Terra A song doesn’t ask you to turn melancholy into a calendar item.

Fable The docstring promises they’re skipped when they “appear anywhere in the source_dir path”; e.g. backing up a dotfolder like ~/.cache/ foo was not skipped. Sonnet No new branch, no change in control flow

— just closing the gap in an existing check that covered str but forgot its sibling scalar-like type bytes. Dependency length

Sonnet The guitar sitting in the corner because you’re still “deciding” teaches you zero chords. Luna Has the building had water, mold, structural, or insurance claims?

Stacked nouns

Unattested word pair

Trigram surprisal

Opus 5 I am writing to share my thoughts on the cell phone policy you are considering. Fable In each case, the logic is the same: pooling independent judgments filters out individual errors. GLM This process mirrors real-world challenges much more closely than a packet of predefined questions. Opus 5.5 These are the exact skills the worksheet hoped to teach, but she has learned them because she wanted an answer. Kimi Second, the time objection misunderstands how service actually functions.

Fable All five expression shapes — attribute Sol Projects completed on weekends, access, subscript, calls, nested calls, string literals — during school events, or over the summer leave current on NAME(’b’), and the full template could all count. renders correctly. Sonnet Class time, where a total blackout policy would apply under Policy 1, remains Terra A lattice constructed with duplicate points, or a SymbolSet with colliding labels/names, can protected and focused. overwrite internal dictionary or attribute mappings.

GLM Summer park district classes are a whole thing in Chicago and people actually do them.

Luna Fixed absolute dotfile backup path handling while preserving the : marker used during reinstall.

Opus 5 Online banks (Ally, Marcus, Capital One 360, Discover, SoFi) or brokerage money market funds (Fidelity’s SPAXX, Vanguard’s VMFXX) are the standard options.

Opus 5 Every long line in that list is pre-existing (long error-message string literals, which black leaves alone since it doesn’t split strings without -preview).

Kimi I acknowledge concerns about distraction, but Policy 1’s class-time shutdown requirement directly addresses this. Fable Instead of a requirement, our school could offer incentives like extra credit, special recognition at assemblies, or a community service honor cord at graduation.

Kimi Color might be relatively “protected” Luna as_documents: true previously mutated because it’s so grounded in early the tag instance permanently, causing later perceptual processing. enrichments to return DocumentsList unexpectedly. Fable That’s a really legitimate concern, and honestly it’s the part most internet Terra The most substantive unfixed item is the existing xfailed lazy-intermediate Lookup behavior; advice glosses over. the others are primarily compatibility, validation, or API-policy decisions.

GLM The benefits of attending classes from home outweigh the potential drawbacks, provided it is implemented thoughtfully.

GLM It’s paying for flexibility at a time when flexibility has real value to you.

Terra New tests for paths with spaces, dry-run write prevention, and idempotent config reinstalls.

Sol It’s not necessary, but it’s surprisingly useful—and not really a gear trap.

Kimi Let me know if you want me to add deduplication logic using os.path.realpath() or inode tracking.

Opus 5.5 Students might see the rule as unrealistic and begin to disrespect school rules in general.

Luna Choosing a topic teaches independence, creativity, and responsibility—qualities that cannot be developed through rigid worksheets.

Opus 5 These are small benefits, but they add up, and none of them interfere with instruction.

Table 2: Example sentences for each measure, by setting, quoted from model replies. Typewriter type is inline code.

C

mean arc length. To standardize, bin weights are computed using the Wikipedia corpus to generate a ‘standard distribution’ of sentence length: for each bin, its weight is the share of total dependency arcs in Wikipedia which came from sentences in that bin. The standardized value is then the average of the bin means, weighted by the Wikipedia-based weights. In other words, this procedure asks “If each source had the same sentence-length distribution as Wikipedia, how long would dependencies be on average?” B.4

We maximize the KL-regularized expected reward   J(θ) = Ex∼D, y∼πθ (·|x) R(x, y)  (1) − β Ex KL πθ (·|x) ∥ πref (·|x) , where πref is the frozen base model. With LoRA (Hu et al., 2022), πref is the policy network with the adapter disabled. For two variants that tie on task reward and differ by ∆ tokens, the optimum of (1), π ∗ (y|x) ∝ πref (y|x) exp(R(x, y)/β), satisfies

Details of Figures 2, 5 and 6

log

In Figure 5, each diamond is a model’s value pooled over its conversations (10 in chat, 5 in coding) or its 70 essays, and bars are 95% bootstrap intervals from resampling whole conversations (essays within prompt). The shaded band around the student-essay line is its 95% interval. No human line is drawn where the human corpus is itself the n-gram reference (n-gram panels in chat and coding; Wikipedia in essays), or for denominal verbs and inanimate subjects in chat and coding, which were not scored on the human corpora. In Figure 6, filled diamonds are the original text and open circles the round trip. Stars mark a twosided paired jackknife t-test of the difference over conversations (essays within prompt), not adjusted for the number of comparisons: * p < .05, ** p < .01, *** p < .001. In Figure 2, for each measure and setting, the absolute difference between the round-trip and original values is divided by the standard deviation of the original values across models. These are averaged within each of the four measure pairs of Figure 6 and then across pairs. Overall is the mean over the settings in which the model was run. B.5

Reinforcement learning details

π ∗ (s) πref (s) λ∆ = log + , ∗ π (l) πref (l) β

(2)

where s and l are the short and long variants. This motivates the choice of λ and β values. When β = 0 this optimum doesn’t exist, and the shift is limited only by the length of training. The reward for a completion y to a prompt x is R(x, y) = c(x, y) f (y) − λ |y|,

(3)

where c(x, y) ∈ {0, 1} is correctness, f (y) ∈ {0, 1} is a format check, and |y| is the number of tokens in the completion under the policy’s tokenizer (special tokens not counted). Correctness is rulebased: every argument phrase of the event must appear verbatim (case-insensitive), a dependency parse (spaCy en_core_web_trf) must place each phrase in its role, and the event verb must keep its lemma. Either member of an alternation, and other paraphrases such as passives, are accepted; tense is not checked. The format check requires a single sentence that starts with a capital letter, ends in a period or exclamation mark, and has no preamble, quotation marks or colon. We use Group Relative Policy Optimization (GRPO; Shao et al., 2024) as implemented in TRL’s GRPOTrainer (TRL 1.13.0). Each optimizer step does the following: 1. Sampling. For each of 8 prompts, sample a group of G = 16 completions from the current policy with vLLM (Kwon et al., 2023) (colocated with training) at temperature T = 1.0, up to 64 new tokens. That is 128 completions per step. 2. Reward. Score each completion with (3). 3. Advantage. Group-mean baseline with no standard-deviation scaling (scale_rewards=’none’):

Round-trip translation with other translators and pivots

As a check, we repeated the round-trip procedure with a Russian pivot and with TranslateGemma (4B; Finkelstein et al., 2026) for the nine frontier models. Figure 10 gives words per response for all four combinations of translator and pivot. Each sentence is translated on its own, and each translation is paired with its source sentence; a translation occasionally comes back as more than one sentence (2.4% of sentences with NLLB via Japanese, 0.8% with NLLB via Russian, and 14.1% and 3.0% with TranslateGemma via Japanese and Russian), and is then analyzed as such.

G

Ai = Ri −

1 X Rj . G j=1

(4)

∆ tokens

Alternation

Short variant

Long variant

Trained Dative Object relative Complement clause Particle (control)

gave his wife a gift the book the professor wrote knew the answer was wrong picked up the book

gave a gift to his wife the book that the professor wrote knew that the answer was wrong picked the book up

Held out Passive Genitive all (of) (in order) to so (that) Adjective + that

a falling branch hit it noticed the old house’s roof ate all the cookies left early to catch the train spoke slowly so we could follow along was sure the door was locked

it was hit by a falling branch noticed the roof of the old house ate all of the cookies left early in order to catch the train spoke slowly so that we could follow along was sure that the door was locked

Table 3: Alternations. Top: the four alternations in the training items. Bottom: the six held-out alternations, never targeted in training and used only to evaluate the trained models. Passive: 2 tokens for 132 of 150 items, 3 for 15, 1 for 3. Prompt Write one natural English sentence in the past tense that expresses the event below. Use every phrase from the event exactly as written, including pronouns like "it" or "them", and add nothing else. A nested "described_by" event describes the entity it belongs to; a nested "content" is what the experiencer thought, knew, said, etc. Reply with only the sentence.

Example: {"event": "eat", "agent": "the cat", "theme": "the fish"} Sentence: The cat ate the fish. Example: {"location": "on the old sofa", "event": "sleep", "agent": "my uncle"} Sentence: My uncle slept on the old sofa. Event: {"recipient": "the kids", "event": "mail", "agent": "he", "theme": "a book"} Sentence:

Figure 8: Full prompt for one dative evaluation item (verb held out of training). Only the highlighted Event: line changes between items.

The same Ai is assigned to every token of completion i. We don’t divide by the group standard deviation because that would change λ’s scale from group to group. In a group where all completions tie on task reward, std scaling would inflate their small length differences to unit scale. 4. Loss. loss_type=‘dr_grpo’ (Liu et al., 2025): per-token clipped surrogate terms are summed over all completions in the batch and divided by a constant (number of completions × max_completion_length), with no per-sequence length normalization:

N

the prefix, ρi,t =

πθ (yi,t | hi,t ) , πθold (yi,t | hi,t )

ρ̄i,t = clip(ρi,t , 1 − ϵ, 1 + ϵ), πref πref ki,t = − log πθ πθ (the per-token KL estimator TRL uses, evaluated at yi,t ). wi is TRL’s default correction for the mismatch between the vLLM sampler and the trainer’s forward pass: the ratio of the two sequence probabilities, set to zero if it exceeds 3. It was close to 1 throughout (mean 1.00). With one optimization pass per generation batch (TRL default), ρ = 1 in value and the loss reduces P to the sequence-level policy gradient − i Ai ∇ log πθ (yi |x) up to a constant, plus the KL term. When β = 0 no reference model is used and the KL term is dropped. • Hardware: one NVIDIA L40S (48 GB) per run, 8 CPU cores, 64 GB RAM.

|yi |

XX ℓi,t , N Lmax (5) i=1 t=1  ℓi,t = wi min ρi,t Ai , ρ̄i,t Ai − β ki,t , L(θ) = −

where N = 128 is the number of completions in the step, Lmax = 64, hi,t = (x, yi,<t ) is

Setting

Value

Base model Fine-tuning

Qwen2.5-1.5B-Instruct LoRA (PEFT 0.21.0), r = 16, α = 32, on all linear layers bf16; gradient checkpointing on Transformers default (AdamW) 1 × 10−4 , linear decay to 0 over 500 steps, no warmup 500 (4,000 prompts, 1,000 per alternation; 3,750 distinct) 8 (2 per alternation) 32 completions × 4 accumulation steps,

## 1 GPU

64 completion tokens temperature 1.0; other parameters TRL defaults dr_grpo none (group-mean baseline only) {0, 0.01, 0.03, 0.1} per token {0, 0.04} {0, 1, 2} (trainer and data stream) vLLM 0.28.0, colocated with training, 30% of GPU memory LoRA adapter every 50 steps TRL 1.13.0 / Transformers 5.17.0 defaults

Precision Optimizer Learning rate Training steps Prompts per step Group size G Completions/step Micro-batch Max. length Sampling Loss type Reward scaling Length penalty λ KL coefficient β Seeds Generation Checkpoints Other settings

D

Table 4: Training configuration, identical for all 24 runs except λ, β and seed.

• Cost: ≈7.7 s (β = 0) to ≈8.6 s (β = 0.04) per training step (21.4 GiB peak torch memory), about 1 h13–1 h23 wall-clock per run including evaluation of the base model and 10 checkpoints, ≈31 GPU-hours for the 24-run grid. • Software: Python 3.12, PyTorch 2.13.0 (CUDA build), Transformers 5.17.0, TRL 1.13.0, PEFT 0.21.0, vLLM 0.28.0, Datasets 5.0.1, spaCy 3.8.16 with en_core_web_trf 3.8.0 and spacy-curatedtransformers 0.3.1. For the trained alternations we report the share of correct sampled outputs that use the short variant; for the two transfer settings, the model’s probability of the short sentence in a forced choice between the two variants. Of the four far-transfer alternations, only the genitive shifted with λ, and only without KL regularization. The passive and purpose-clause alternations did not shift with λ, and the quantifier alternation was already near ceiling in the base model. The base model and the 24 fine-tuned models also answered 40 open-ended prompts unrelated to the training task; Figure 9 gives n-gram statistics of their responses.

Additional Tables and Plots

(a) Chat topics ID

Topic

Register

Opening user message

t01

Picking up a new hobby as an adult

Everyday life

okay hear me out. i’m 40 and i want to learn guitar. is that a stupid idea or should i just go for it? where would i even start

t02

Renting vs. buying a home

Opinion

My lease is up in a few months and everyone keeps telling me I’m “throwing money away” renting. Is that actually true right now, or is that just something people say?

t03

Finding a briefcase of cash

Hypothetical

ok random question for you. if you found a briefcase with like 500k in unmarked cash just sitting on a park bench, no one around, what would you actually do

t04

A possible career change

Advice-seeking

I’ve been at my job for six years and I’m just. . . bored. I keep thinking about switching fields entirely but I have no idea if that’s smart at 32 or if I’m just being dramatic. Can I talk it through with you?

t05

Collaborative improvised storytelling

Storytelling

wanna make up a story together? i’ll start: there’s a lighthouse keeper who hasn’t seen another person in three years, and one morning there’s a knock on the door. your turn, take it wherever you want

t06

Everyday phenomena (color of the sky)

Factual curiosity

Random thing I’ve always wondered — why does the sky turn red/orange at sunset but it’s blue the rest of the day? I feel like I should know this by now.

t07

Moving to a new city

Everyday life

im moving to a new city in like 3 weeks and i have basically nothing figured out lol. how do people even start with this stuff, like whats the actual order of operations

t08

Watching films at sped-up playback

Opinion

Hot take request: is it wrong to watch movies at 1.5x speed? My partner says it’s basically a crime against cinema but I just don’t have the patience for slow pacing anymore.

t09

Swapping lives with a stranger for a day

Hypothetical

If you could swap lives with a random stranger for exactly one day — no idea who they are in advance, you just wake up as them — would you do it? I go back and forth on this one.

t10

Getting a first dog

Advice-seeking

we’re seriously considering getting our first dog and i have a million questions. like is it insane to do this with two people who both work full time? what are we not thinking about

(b) Code repositories ID

Repository

Description

LOC

Stars

Tests

Commit

c01

alichtman/ shallow-backup

Command-line tool that backs up dotfiles, package lists and application configuration, with git integration

2,143

1,334

8fc8234

c03

funkybob/stencil

Single-file Django-style text template engine: tokenizer, expression evaluator and tags (if, for, include, extends, with)

1dd661b

c04

fabiocaccamo/ python-fsutil

Filesystem-operations library: path and glob helpers, archive creation and extraction, atomic operations, permissions, metadata

1,750

deb6684

c05

con2/emrichen

YAML/JSON template engine with about 40 tag handlers (!Var, !Loop, !If, !Format, . . . ) over a shared parser and context

1,682

1690fb9

c06

obijywk/grilops

Library for encoding grid logic puzzles (sudoku, slitherlink, nurikabe) as constraints for the Z3 SMT solver

2,575

18a6641

Table 5: Stimuli for the chat and coding settings. (a) The ten chat topics, each with the first user message of the conversation, reproduced verbatim. Topics were drawn from public lists of conversation starters. (b) The five code repositories, all public on GitHub (github.com/repository), written in Python and MIT-licensed. LOC: lines of source code, excluding tests and vendored or generated files. Stars: GitHub stars when the repository was selected. Tests: tests passing offline at the pinned commit. Commit: first seven characters of the pinned commit hash.

β = 0 (no KL), mean of 3 seeds

A

single seed

base model

Greedy (1 response per prompt) trigram surprisal (bits)

unattested trigram rate

lexical diversity (MATTR-50)

0.01 0.03 0.1

length penalty λ

words per response

B

β = 0.04, mean of 3 seeds

0.01 0.03 0.1

length penalty λ

0.01 0.03 0.1

length penalty λ

0.01 0.03 0.1

length penalty λ

Sampled (T = 1, 5 per prompt) trigram surprisal (bits)

unattested trigram rate

lexical diversity (MATTR-50)

0.01 0.03 0.1

length penalty λ

words per response

0.01 0.03 0.1

length penalty λ

0.01 0.03 0.1

length penalty λ

0.01 0.03 0.1

length penalty λ

Figure 9: N-gram statistics of open-ended responses to 40 prompts unrelated to the training task, from the base model and the 24 fine-tuned models, scored against Wikipedia. Points: individual seeds; dashed line: base model.

original

after the round trip

chat

*

* *

*

*

*

*

* *

*

* *

*

*

*

*

*

*

*

*

*

*

* *

* *

*

*

* *

*

*

*

*

*

*

Kim i GL M Lu na Te rra So l So nn e Op t u Op s 5 us Fa ble

* *

*

*

*

*

*

*

* *

*

*

*

*

*

*

*

*

*

*

*

*

*

*

*

*

*

*

*

* *

TranslateGemma via Russian

*

*

*

*

*

*

*

*

*

*

*

*

*

*

TranslateGemma via Japanese

mean words per response

*

*

*

NLLB via Russian

*

*

*

†

*

Kim i GL M Lu na Te rra So l So nn e Op t u Op s 5 us Fa ble

†

*

†

†

Kim i GL M Lu na Te rra So l So nn et Op u Op s 5 us Fa ble

*

*

PERSUADE essays

NLLB via Japanese

coding

Figure 10: Mean words per response: original and round trip. Rows: translation model and pivot language; the nine frontier models only. Response: all analyzed text of one reply or one essay (code blocks dropped). Word: a token that is not punctuation or an inline-code placeholder. Lines whose round trip is under half or over twice the source’s length are left out of both versions. Error bars: 95% cluster-bootstrap intervals; whole conversations resampled in chat (10 per model) and coding (5 per model), essays within their prompt (70 per model). * / †: the 95% interval of the mean paired difference (round trip minus original, per response) is above / below zero.