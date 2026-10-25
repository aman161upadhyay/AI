# Application-page contracts

These original templates adapt research 05. Supply actual facts, code, tokens and installed versions. No template has been run here. Replace authoring fields before execution.

## Pricing

```text
Design pricing for [product and technical buyer] using our supplied plan table.
Show monthly and annual options with actual annual charge and effective monthly
price. Normalize units, limits, overages, retention, support and cancellation.
Recommend from stated buyer needs, not dark-pattern preselection.
Include accessible comparison, selection confirmation and checkout failure.
Use existing tokens. Ask for missing facts. Invent no price, discount or scarcity.
Verify arithmetic and terms against the supplied table.
```

## Onboarding

```text
Design first-run onboarding for [team scheduling product].
Activation means creating one useful schedule. Use supplied roles and schema.
Ask only workspace name and timezone before the first schedule editor.
Allow skipping optional invitations and branding. Show meaningful remaining steps.
Explain calendar permission just before connection.
Include denial, failed import, resumable progress and no teammates.
Use actual import results. Deliver sequence, recovery and activation checks.
```

## Authentication

```text
Build sign-in for the existing app and supplied auth provider.
Use only supported flows. Give persistent labels, autocomplete, password-manager
and paste support, reveal-password control and pending feedback.
Include invalid credentials, expired link, rate limit, unavailable SSO and
recovery without revealing whether an account exists. Preserve email on retry.
Do not simulate sessions with localStorage flags.
Use visible focus and non-motion success. Ask before auth changes or real emails.
Verify keyboard, provider responses and recovery in an authorized test environment.
```

## Settings

```text
Design account/workspace settings using supplied capabilities and permissions.
Separate personal preferences from admin-only controls. Use grouped labeled
sections rather than a card for every field.
Specify autosave or Save changes for each section. Do not mix silently.
Show pending, confirmed and failed save. Warn before losing edits.
Separate destructive controls and explain consequences with proportional
confirmation. Include read-only, session expiry and server failure.
Use semantic tokens. Verify permission boundaries and retained input.
```

## Tables

```text
Create a customer list from supplied schema and records.
Choose identifier and columns for the renewal decision. Format locale/timezone.
Use native table semantics unless complete grid interaction is required.
Define sorting, filters, columns, pagination, row navigation, selection and
bulk scope. Preserve selection across pages or clearly explain its boundary.
Include loading, empty, no matches, stale and permission states.
Test keyboard and screen reader behavior. Virtualize only after demonstrating
need and checking accessibility. Do not invent live records.
```

## Forms

```text
Design the supplied customer-edit form with existing validation rules.
Group by task. Provide persistent labels, useful autocomplete and optional markers.
Explain unusual formats before errors. Validate at appropriate interactions.
Retain valid values after server failure. Associate errors with fields and use
an error summary after failed submission when useful.
Distinguish Save changes from Cancel and protect unsaved edits.
Include duplicate record, denial and retry. Do not invent business rules.
Verify correction and resubmission without data loss.
```

Acceptance: real rules, labeled controls, state truth, retained input and tested recovery. Common failures are hidden annual charges, fake auth and destructive settings without consequences.
