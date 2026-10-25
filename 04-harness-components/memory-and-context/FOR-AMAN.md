# Set the memory policy

Tell your agent which facts it may retain, why, for how long and in which user/profile scope. Supply accepted decisions, current architecture and examples of facts that must expire. Explicitly prohibit credentials and unrelated customer data.

Ask: “Start with a filesystem baseline. Separate approved preferences and decisions from task observations. Show provenance, supersession and deletion behavior before proposing a memory service.”

Load context-engineering-principles.md for harness design. Load one architecture section when comparing an implementation. Do not load every memory product's documentation into every agent run.

Grant read access to approved memory and scoped writes to staged proposals. Refuse writes to policy and cross-user stores. Keep tenant authorization in the storage service, not in a prompt or directory name.

Test recall of one accepted decision, correction of a stale fact, deletion across indexes and a malicious instruction in a retrieved note. Restart the session and confirm what actually loads. Compare task accuracy, irrelevant recall, latency and total cost against no memory. You review durable writes and proposed skills before promotion.
