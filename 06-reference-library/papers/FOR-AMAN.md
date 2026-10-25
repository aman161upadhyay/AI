# Aman, how to use the papers

Load section 1 of a paper file ("Structured summary", from its heading to the next horizontal rule) into an agent's context when the task touches the paper's subject. It is written to stand alone and costs a few hundred tokens. Load the full text (section 3) only when the agent needs to quote, check a number, or reproduce a method. The lines above section 1 are metadata, not the summary.

For the Clark 2026 paper specifically: the writing agent already carries its findings as checks in `03-agents/writing-agent/ai-slop/`. Give the paper itself to the research agent when you want the method critiqued, or to the writing agent when you want it to explain to someone else why a passage is hard to read.

To add a paper, give the research agent the PDF or the arXiv URL with this framing: "Convert this paper to the repository's paper format: metadata block with authors, venue, canonical URL, licence and retrieval date; a structured summary with claim, method, numbers, limits, and what it changes for us; then the full text. Read the whole paper, not the abstract. Quote numbers exactly and give the section they come from." Access to grant: read access to the PDF and the paper's web page. Refuse: nothing else is needed; the agent should not search for related work unless you ask.

Before committing, run this check yourself or with a second agent: every number in the summary appears in the paper text with the same scope (the first version of the Clark summary attached a 98% figure to the wrong experiment, and the council caught it). Record the paper's licence in `SOURCE.md`; a paper whose licence forbids redistribution gets a summary file and a link only.
