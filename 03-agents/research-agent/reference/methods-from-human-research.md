# Human methods adapted for agents

Use these methods to make evidence checks explicit. The operational formats below are repository proposals. Human studies do not establish that an LLM prompt reproduces their benefits.

| Method | Agent procedure | Evidence and limit |
|---|---|---|
| SIFT | Stop before accepting an unfamiliar claim. Investigate its source laterally. Find better coverage. Trace the assertion to original context. Record the origin family. | [University of Chicago guide](https://guides.lib.uchicago.edu/c.php?g=1241077&p=9082322), crediting Mike Caulfield, undated. The original post could not be fetched in the research phase. |
| Lateral reading | Leave the page long enough to check ownership, expertise, and independent descriptions. Return to read the relevant passage only after those checks. | [Stanford Report](https://news.stanford.edu/stories/2017/10/fact-checkers-outperform-historians-evaluating-online-information), 2017-10-24, reports Wineburg and McGrew's comparison of fact checkers, historians, and students. This is not an LLM performance result. |
| CRAAP | Check currency for this topic, relevance to the question, authority for this claim, accuracy of evidence, and purpose or incentives. | [CSU Chico checklist](https://library.csuchico.edu/sites/default/files/craap-test.pdf), 2010-09-17. The numeric credibility rubric here is an adaptation, not part of the checklist. |
| Hypothesis tree | List plausible explanations, predicted observations, supporting evidence, contrary evidence, and the next discriminating search. Drop a branch only with a recorded reason. | [CIA Tradecraft Primer](https://www.cia.gov/resources/csi/static/Tradecraft-Primer-apr09.pdf), 2009, provides assumptions checks and competing-hypothesis methods. The tree schema is local policy. |
| Premortem | Assume the recommendation failed in six months. Name the mistaken assumption and the observation that could reveal it now. Use the result to choose a check. | [Gary Klein](https://hbr.org/2007/09/performing-a-project-premortem), 2007-09. The research capture was partial. The exact agent procedure is proposed rather than quoted. |
| Steelmanning | State the strongest evidence-backed alternative under the same decision criteria. Identify where it beats the leading option and what would reverse the choice. | Local review norm informed by CIA alternative analysis and Klein's dissent framing. No reviewed source establishes this exact LLM procedure's effectiveness. |
| Superforecasting calibration | For a resolvable question, record probability, resolution date, rule, and evidence updates before the outcome. Score resolved forecasts with mean `(p-y)^2`. | [Mellers et al.](https://web.stanford.edu/~knutson/jdm/mellers15.pdf), 2015, concerns human forecasting. Qualitative confidence in a report is not calibrated probability. |

Use a worked challenge note for a consequential recommendation:

```text
Recommendation and claim IDs:
Strongest supported alternative:
Assumption most likely to fail:
Contrary evidence and source locators:
Next discriminating observation:
Decision if that observation occurs:
Remaining uncertainty and owner:
```

Do not force symmetry when evidence clearly rejects an alternative. Do not label an unresolved claim false merely because it has low support. Use a proper scoring rule only when an outcome can be resolved independently.
