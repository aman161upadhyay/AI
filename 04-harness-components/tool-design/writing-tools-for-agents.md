# Write tools for realistic tasks

Tool quality depends on whether the agent completes the intended task with correct scope. Anthropic recommends prototyping tools, evaluating realistic work and refining descriptions with agents.

## Choose operations

Start from a task, not an inventory of API endpoints. Expose a coherent operation with explicit arguments and useful reusable identifiers. Avoid overlapping names that require hidden knowledge to distinguish. Namespace tools by service.

Anthropic favors useful task-level operations. The inspected MCP-builder skill also values comprehensive endpoint coverage and atomic tools. Treat this as a design tradeoff: compare an atomic catalog with a workflow-level tool on held-out tasks. Comprehensive coverage is not a reason to expose every endpoint in the active context.

Separate read and write operations when that clarifies approval. A “search and publish” tool mixes discovery with an external side effect and should need a staged confirmation design.

## Describe arguments and results

Define types, required fields, bounds and allowed values. Specify timezone, units, resource scope and identifier format. State which defaults are safe. Use Zod or Pydantic when those libraries match the implementation stack; inspect installed versions before copying an SDK example.

Return actionable identifiers, concise relevant fields and explicit pagination. Provide detailed output only when requested. Include truncation metadata and a next cursor rather than silently dropping results. Keep full artifacts outside prompt context where appropriate.

Errors should identify the failed precondition and a safe next action. Distinguish invalid input, denied scope, missing resource, rate limit, timeout and uncertain write outcome. Do not turn an error into an empty successful list.

## Implement the boundary

Authenticate in the runtime. Validate authorization for the resource on every call. Never trust a model-supplied tenant ID as proof of access. Define idempotency and receipts for side effects. Reconcile uncertain outcomes before retry.

MCP-builder recommends output schemas and structured content where supported. Its annotations include `readOnlyHint`, `destructiveHint`, `idempotentHint` and `openWorldHint`. These are hints, not enforcement. The server must implement the actual policy.

The inspected builder recommends TypeScript for broad client support, Streamable HTTP for remote servers and stdio for local integrations. Verify the current SDK and client instead of treating this as a permanent protocol rule.

## Evaluate behavior

Use stable tasks with independently known answers and realistic data. Track task success, tool selection, argument errors, denied actions, latency, output tokens and duplicate calls. Keep held-out cases during description refinement.

The MCP-builder skill proposes ten independent, read-only, verifiable questions that require multiple calls. Add write-specific sandbox tests separately. Read-only questions cannot establish that retries or approvals for writes are safe.

Compare concise versus detailed responses without changing the model at the same time. Inspect traces for broad searches and repeated calls. Anthropic's reported concise-result example used about one-third the tokens of detailed output, but that is not a universal saving.
