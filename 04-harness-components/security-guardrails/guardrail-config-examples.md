# Illustrative configuration, not installed protection

Snapshot: 2026-10-25. Validate the installed product's schema and managed-policy precedence before use. These fragments cover only part of the policy. No secret values appear here.

## Claude Code permissions

The inspected first-party strict settings example uses these permission keys. This local fragment requests review for shell execution and denies built-in web access:

```json
{
  "permissions": {
    "disableBypassPermissionsMode": "disable",
    "ask": ["Bash"],
    "deny": ["WebSearch", "WebFetch"]
  },
  "allowManagedPermissionRulesOnly": true,
  "allowManagedHooksOnly": true,
  "strictKnownMarketplaces": []
}
```

The managed-policy keys need the product's managed deployment mechanism. Do not assume a worker-writable project file makes them immutable. This fragment does not deny MCP network calls or all writes. Add a real sandbox and per-tool authorization. The upstream strict example also constrains sandbox network access and disables weaker nested sandboxing; reproduce only settings that the installed runtime supports and test them.

## Claude Code hook shape

The inspected first-party hook example documents a PreToolUse matcher and command hook. This is an integration sketch: `<APPROVED_POLICY_HOOK>` must be replaced by an independently reviewed absolute executable path before installation.

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "<APPROVED_POLICY_HOOK>"
          }
        ]
      }
    ]
  }
}
```

The hook must validate structured input, reject malformed requests and enforce its decision using the installed runtime's documented blocking protocol. The inspected example uses exit code 2 to block; its regex advice is not a security parser. Do not copy its fail-open handling for malformed input. Test hook crash/timeout behavior. A Bash-only matcher leaves other tools uncovered. Keep the hook outside worker-writable roots and enforce essential boundaries in the sandbox/dispatcher even if hooks fail.

## Codex sandbox settings

The inspected schema includes `read-only` and `workspace-write` modes. An inspected config test uses `on-request` approval. Start review-only:

```toml
sandbox_mode = "read-only"
approval_policy = "on-request"
```

For an explicitly approved disposable application worktree:

```toml
sandbox_mode = "workspace-write"
approval_policy = "on-request"

[sandbox_workspace_write]
network_access = false
exclude_slash_tmp = true
exclude_tmpdir_env_var = true
```

Workspace-write grants more than application-specific edits. Protect control files independently. The workspace-write subsection applies only to that mode. Verify actual network denial and approval behavior on the deployed platform. Local sandbox settings do not contain remote MCP operations, and a requested approval must not become automatic escalation.

## MCP policy data

This YAML is a proposed dispatcher schema, not a native MCP client configuration:

```yaml
default_decision: deny
servers:
  approved_read_connector:
    manifest_digest: "<REVIEWED_MANIFEST_DIGEST>"
    allowed_origin: "<APPROVED_HTTPS_ORIGIN>"
    tools:
      search_public_records:
        actions: [read]
        resource_scope: "<APPROVED_DATASET>"
        max_results: 20
        credentials: none
    on_manifest_or_origin_change: require_independent_approval
token_passthrough: deny
egress:
  allow_only_configured_origins: true
  deny_private_and_metadata_addresses: true
  validate_each_redirect_and_resolution: true
approval:
  bind: [principal, operation, resource, argument_hash, destination, expiry]
```

The 20-result limit is an illustrative local cap, not a vendor default. Implement the evaluator before treating these keys as controls. Test OAuth discovery SSRF, changed manifests, token audience, and tool-description instructions that request sibling privileges.

Source pins and reviewed paths are in `sources.md`. No proprietary Claude Code runtime or upstream hook implementation is vendored here.
