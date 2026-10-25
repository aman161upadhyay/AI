# System-design references

Use original authors and first-party operational docs for design decisions. Do not replace source reading with anonymous book-summary repositories.

| Reference | Author/org; date | Maintenance status as of 2026-10-25 | What to study and limit |
|---|---|---|---|
| [SRE Workbook monitoring](https://sre.google/workbook/monitoring/) | Google SRE, 2018 | Foundational book with accessible first-party web page | Percentiles, alert quality, monitoring configuration; actual SLOs depend on the product |
| [Twelve-Factor Config](https://12factor.net/config) | Twelve-Factor project, undated classic | Foundational accessible first-party page | Deploy-specific configuration outside code; environment variables still require secret controls |
| [Well-Architected pillars](https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html) | AWS, living framework | Current first-party reference | Operational excellence, security, reliability, performance efficiency, cost optimization, sustainability; provider guidance is not a reason to add AWS services |

For DDIA summaries, write short independent notes around a named project decision with an original citation and uncertainty. Do not copy reconstructed chapter summaries or paid diagrams. A note should state the relevant invariant, rejected alternative, and verification experiment.

Use the [system-design agent](../../03-agents/system-design-agent/README.md) to turn a reading into requirements, contracts, ADRs, and a security-review packet. References do not establish production readiness by themselves.

System Design Primer was removed from the active table; see [superseded.md](superseded.md).

## Pending: not yet inspected

- [DDIA second-edition announcement](https://martin.kleppmann.com/2026/03/24/designing-data-intensive-applications-2e.html), Martin Kleppmann, 2026-03-24: search-only; full fetch unavailable as of 2026-10-25. Not an admitted recommendation or evidence for edition-specific chapter claims.
- [DDIA](https://dataintensive.net/), Martin Kleppmann and Chris Riccomini: the fetched homepage described the older edition; substantive book text was not inspected as of 2026-10-25. Inspect an authorised edition before admitting chapter-level guidance. Do not redistribute book text.
