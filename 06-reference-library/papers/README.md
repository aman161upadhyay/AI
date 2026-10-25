# Papers

Full-text conversions of research papers, each with a hand-written summary at the top (claim, method, numbers, limits, what it changes for us) followed by the paper's own text. Converted from the PDF Aman supplied or from the open-access version; the source URL and date are at the top of each file.

| File | Paper | Why it is here |
|---|---|---|
| [2026-clark-martin-mahowald-why-is-ai-generated-language-so-hard-to-understand.md](2026-clark-martin-mahowald-why-is-ai-generated-language-so-hard-to-understand.md) | Clark, Martin, Mahowald (2026), "Why is AI-generated language so hard to understand?", arXiv:2610.29162 | The only corpus study we found that measures, across 14 models, how far model prose over-uses constructions that earlier psycholinguistic work tied to processing difficulty. It runs no human reading experiment of its own; the reader-cost claim rests on that earlier work. The writing agent's seven readability checks come from its Table 2, transcribed in full here; the example sentences are in `../figures/` |

Add a paper by converting it to Markdown (`pdftotext -layout` then clean the headers and footers), writing the summary block in the same shape, and adding a row to this table. Papers whose licence forbids redistribution get a summary file and a link only.
