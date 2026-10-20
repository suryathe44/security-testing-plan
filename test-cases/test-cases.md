# Candidate Test-Case Register

All cases start as **Not Run**. Run only cases relevant to the signed scope. These are safe candidate checks, not proof that any vulnerability exists.

| ID | Objective | Safe method | Expected secure behaviour | Evidence | Status |
|---|---|---|---|---|---|
| ST-01 | Confirm target scope | Compare the base URL with signed scope; do not probe other hosts. | Exact match; otherwise stop. | Scope record, timestamp | Not Run |
| ST-02 | Observe transport security | Inspect browser URL/security indicator for the approved environment. | Correct HTTPS for production-like deployments; lab-only HTTP documented. | Redacted screenshot | Not Run |
| ST-03 | Observe security headers | Inspect response headers for a normal page load in developer tools. | Appropriate headers for deployment context. | Header list, no cookies/tokens | Not Run |
| ST-04 | Check protected route access | Visit one approved protected page while logged out. | Access denied or redirect to sign-in. | Route and result, no secrets | Not Run |
| ST-05 | Check logout/session invalidation | Sign in with a synthetic account, log out, revisit protected page. | Old session no longer grants access. | Redacted result | Not Run |
| ST-06 | Check role-based access | Compare two assigned synthetic roles against an approved test resource. | Access matches each role's permissions. | Role matrix and result | Not Run |
| ST-07 | Check input validation | Submit harmless invalid-format or boundary input in a non-destructive form. | Input rejected/handled safely; no unexpected side effects. | Input category and result; avoid sensitive values | Not Run |
| ST-08 | Check error disclosure | Use normal UI to cause a benign invalid request. | No stack trace, secret, or unnecessary internal details. | Redacted error text | Not Run |
| ST-09 | Check own-profile data exposure | Review only the tester's own synthetic profile/page source. | Only necessary data exposed to that account. | Redacted screenshot | Not Run |
| ST-10 | Review dependency/configuration info | Review supplied local package metadata or documented versions. | Risks identified for follow-up; coverage limits recorded. | File/version list | Not Run |
| ST-11 | Review logging privacy | Generate a test event and inspect only logs the tester is authorised to see. | Useful event details without passwords/tokens or excessive personal data. | Redacted event sample | Not Run |
| ST-12 | Verify remediation | Repeat only the original case after owner approval for retesting. | Original issue no longer reproduces under same conditions. | Before/after evidence IDs | Not Run |
