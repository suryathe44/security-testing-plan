# Security Testing Plan
**Project:** Permission-Based Security Test Plan for a Demo Web Application  
**Prepared by:** Surya Singh Chauhan — Intern ID 2418  
**Organisation:** RedKross Research Foundation  
**Version:** 1.0 | **Prepared:** 20 October 2026 | **Deadline:** 25 October 2026

## 1. Purpose

This plan provides a controlled, repeatable process to assess the security posture of a demo web application. It prioritises authorisation, clear boundaries, safe verification, evidence minimisation, and actionable reporting. It is a plan, not a claim that tests have already been executed.

## 2. Objectives

1. Confirm written permission and an unambiguous test scope before testing.
2. Identify selected web-application security weaknesses using low-impact methods.
3. Record observations in a reproducible, evidence-based way.
4. Communicate risk and remediation clearly.
5. Verify fixes only after approval for retesting.

## 3. Scope and assumptions

**Target:** To be completed before execution. Preferred target is a local instance controlled by the intern, such as OWASP Juice Shop.  
**Environment:** Isolated local lab or explicitly authorised test environment.  
**Test accounts/data:** Synthetic accounts and non-sensitive sample data only.  
**Testing window:** Must be agreed in advance and recorded in the authorisation form.  
**Assumption:** No production or third-party target is in scope unless the owner explicitly authorises it in writing.

### In scope only when approved
- Application pages and routes explicitly listed in the signed scope.
- Basic configuration observations visible from the approved test environment.
- Authentication and session behaviour using assigned test accounts.
- Input validation and access-control checks using harmless, controlled test data.
- Security headers and transport-security observations where applicable.

### Out of scope unless separately approved
- Denial-of-service, stress/load testing, destructive payloads, persistence, malware, social engineering, phishing, credential harvesting, or password spraying.
- Accessing or downloading real user data.
- Testing third-party services, identity providers, payment processors, or infrastructure not named in the scope.
- Exploiting a finding beyond the minimum proof needed to confirm it.
- Public internet scanning or testing the public OWASP Juice Shop demo.
- Any action that changes data irreversibly or could disrupt service.

## 4. Roles and responsibilities

| Role | Responsibility |
|---|---|
| Intern/tester | Follow the approved plan, minimise impact, maintain logs, stop when required, and report accurately. |
| System owner/authoriser | Approve target, test methods, accounts, timing, exclusions, emergency contact, and data handling. |
| Reviewer/supervisor | Review scope, prioritisation, evidence redaction, and report quality. |
| Application maintainer | Assess findings, plan fixes, and approve retesting. |

One person may hold multiple roles in a personal lab, but the authorisation and scope record must still be completed honestly.

## 5. Methodology

The workflow follows common planning, testing, analysis, and reporting principles described in NIST SP 800-115 and the OWASP Web Security Testing Guide.

1. **Prepare:** Define objective, target, owner, written authorisation, test window, accounts, and emergency contact.
2. **Validate scope:** Confirm hostnames/URLs, allowed routes, rate limits, exclusions, and stop conditions. Verify the target is the intended lab.
3. **Baseline:** Record application version (if known), environment, date/time/time zone, browser/tool versions, and normal behaviour.
4. **Test:** Perform selected low-impact cases one at a time. Use synthetic inputs. Avoid broad automated scanning unless specifically authorised.
5. **Observe:** Record request/response details only as needed. Redact session tokens, passwords, personal information, and secrets.
6. **Analyse:** Separate observed facts from hypotheses. Assign severity based on impact, exploitability, and context; explain uncertainty.
7. **Report:** Document evidence, affected component, impact, remediation, and limitations.
8. **Close:** Stop testing, remove temporary test data if approved, securely store evidence, notify the owner, and record the final status.
9. **Retest:** Retest only with renewed/continued authorisation and record whether the specific fix worked.

## 6. Safe test categories and example cases

The full register is in `../test-cases/test-cases.csv`.

| ID | Category | Safe check | Expected secure behaviour |
|---|---|---|---|
| ST-01 | Scope and reachability | Confirm the exact approved base URL and environment without probing other hosts. | Target matches signed scope; otherwise stop. |
| ST-02 | HTTPS/configuration | Observe whether the approved environment uses HTTPS and whether browser warnings occur. | Production-like deployment uses correctly configured HTTPS; local HTTP is documented as lab-only. |
| ST-03 | Security headers | Inspect response headers in browser developer tools for a normal page load. | Relevant headers are present and appropriate to deployment context. |
| ST-04 | Authentication | With an assigned synthetic account, verify that a protected page requires sign-in. | Unauthenticated access is denied or redirected appropriately. |
| ST-05 | Session handling | Log out of a synthetic account and revisit a protected page in the same browser. | Session is invalidated and protected content is not accessible through the old session. |
| ST-06 | Access control | Compare access to a test resource using two explicitly assigned synthetic roles, if available. | Users can access only resources permitted by their role. |
| ST-07 | Input validation | Submit a harmless boundary string or invalid format into a non-destructive form. | Input is validated and errors are handled safely without exposing internals. |
| ST-08 | Error handling | Trigger a benign invalid request within the app's normal interface. | No stack trace, secret, or unnecessary internal detail is exposed. |
| ST-09 | Sensitive-data exposure | Inspect only the tester's own synthetic profile and page source for accidental disclosure. | Only necessary data is exposed to the authorised user. |
| ST-10 | Dependency/configuration review | Review documented dependency versions or local package metadata if supplied. | Known issues are assessed and updates are tracked; no claim of exhaustive coverage. |
| ST-11 | Logging/privacy | Check whether a test event creates logs, without accessing other users' logs. | Logs are useful but avoid passwords, tokens, and unnecessary personal data. |
| ST-12 | Remediation retest | Repeat only the previously failed case after the owner confirms the fix and retest permission. | Original issue no longer reproduces under the same safe conditions. |

These are candidate checks, not evidence that a vulnerability exists. Select only applicable cases within the approved scope.

## 7. Risk rating

Use a qualitative model and explain the rationale rather than relying on a number alone.

| Rating | General guide | Response |
|---|---|---|
| Critical | Plausible severe compromise of core systems or broad sensitive-data exposure. | Stop affected testing, notify owner immediately, preserve minimal evidence. |
| High | Significant access-control failure or meaningful compromise with limited barriers. | Prompt owner notification and prioritised remediation. |
| Medium | Meaningful weakness with constraints or narrower impact. | Planned remediation with an agreed due date. |
| Low | Limited impact, defence-in-depth gap, or minor information exposure. | Address through routine hardening. |
| Informational | Observation without demonstrated direct security impact. | Record for context; avoid overstating risk. |

Final severity must consider the real context, privileges required, exposure, business impact, and confidence. Do not claim a CVSS score unless it is calculated with a stated version and rationale.

## 8. Evidence handling

- Collect the minimum evidence required to support the observation.
- Prefer synthetic accounts, test records, and redacted screenshots.
- Never store passwords, session cookies, API keys, private keys, or real personal data in the repository.
- Use neutral evidence IDs such as `EV-001`; record date/time and test-case ID.
- Restrict access to evidence; keep sensitive raw evidence outside a public repository.
- Hash files when integrity tracking is useful, and record the algorithm used.
- Delete temporary data only as agreed with the owner; document the action.
- If sensitive data is unexpectedly encountered, stop, do not copy it, and notify the owner through the agreed channel.

## 9. Stop conditions and incident response

Stop testing immediately if:
- The target does not match the approved scope.
- Written authorisation is missing, unclear, expired, or revoked.
- The service becomes unstable or an unexpected availability impact occurs.
- Real personal data, credentials, or confidential records are exposed.
- A test would require an excluded technique or affect a third party.
- The owner or emergency contact requests a stop.

After stopping: cease further requests, preserve only minimal safe metadata, do not explore further, notify the owner, and document the reason and time.

## 10. Reporting and closure

Each finding should include:
- ID, title, affected component, date, tester, and test case.
- Status (`Observed`, `Not Reproduced`, `Not Run`, or `Retest Pending`).
- Severity and rationale.
- Preconditions and safe reproduction steps.
- Evidence references and redaction notes.
- Security impact and limitations/uncertainty.
- Recommended remediation and verification steps.
- Owner, due date, and retest status.

Close the engagement with a summary of scope, cases run/not run, key findings, limitations, and recommended next steps. A test plan or a passing test does not prove that an application is completely secure.
