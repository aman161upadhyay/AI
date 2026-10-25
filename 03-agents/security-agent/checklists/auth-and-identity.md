# Authentication, sessions and authorization

Use ASVS 5.0.0 V6 Authentication, V7 Session Management and V8 Authorization as the baseline. Adjacent token checks come from V9 Self-contained Tokens and V10 OAuth and OIDC. These are chapter-level essentials, not a claim that every requirement is covered.

| Area | Control | Test |
|---|---|---|
| V6 password storage | Argon2id minimum 19 MiB, two iterations, parallelism one; unique salts | Inspect hash metadata and benchmark stronger settings; verify no plaintext in logs |
| V6 enrollment/recovery | Comparable proof for lost-factor recovery; administrator MFA | Attempt factor replacement with only an old session; replay expired reset links |
| V6 abuse | Generic errors and bounded login/reset attempts | Compare responses for known and unknown accounts; test account and source limits |
| V10 OAuth/OIDC | Exact redirect URI, bound state and nonce, PKCE S256 where supported | Swap state between sessions; replay nonce; alter redirect; omit verifier; require rejection |
| V9/V10 token purpose | ID tokens are not general API access tokens | Send a correctly signed ID token to an access-token endpoint; require purpose/audience denial |
| V7 cookies | Secure, HttpOnly, suitable SameSite; `__Host-` where compatible | Inspect deployed HTTPS cookies, including recovery and refresh paths |
| V7 lifecycle | Rotate at login and reauthentication; revoke old sessions | Replay old token after login, logout, role revocation and password change |
| V7 expiration | Server-side idle and absolute expiry | Advance fixture clock and request protected data; require reauthentication |
| V7 CSRF | Protect cookie-authenticated mutations; never mutate on GET | Submit a cross-origin form without a valid token/origin; verify unchanged database |
| V8 object policy | Check subject, action, object and tenant close to data | Change object IDs and role claims across every server entry point |
| JWT | Pin algorithms and trusted keys; verify signature, iss, aud, exp and nbf | Reject unsigned, wrong-audience, wrong-key, expired and future tokens |
| JWT keys/data | No attacker-controlled key URL; define revocation; no confidential plaintext claims | Alter key-location metadata; inspect egress; revoke fixture session; decode for accidental secrets |

CORS does not authenticate non-browser clients. SameSite alone does not establish complete CSRF protection for every deployment. Mature identity SDKs do not implement the application's object-level policy. Exact current Auth.js defaults were not verified; test actual behavior.
