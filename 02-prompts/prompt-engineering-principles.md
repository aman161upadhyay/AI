# Applying prompting principles to task templates

Use the canonical [evidence-ranked principles](../00-foundations/prompt-engineering/principles-ranked-by-evidence.md) for the ranking, evidence, and model-specific limits. Do not maintain a second ranking here.

For each task template, specify the input fields, expected artifact, source requirements, and refusal or abstention conditions. Keep policy separate from user-supplied documents.

Put the template's fixtures and scoring rubric beside it. Include a missing-evidence case and an instruction-injection case where external text is accepted. Record the model/version, cost, and observed failures before accepting a revision.

For software consumers, bind the output contract to the supported native schema and validate it outside the model. For human readers, require only the structure that the task needs.

Adapted Fabric patterns retain provenance beside each pattern. Their inactive originals are reference data, not instructions to execute. Check the rewrite against the task fixtures rather than assuming upstream popularity establishes effectiveness.
