# Permission-Based Security Testing Plan

**Intern:** Surya Singh Chauhan  
**Intern ID:** 2418  
**Organisation:** RedKross Research Foundation  
**Assignment:** Security Testing Plan  
**Submission deadline:** 25 October 2026  
**Status:** Documentation package prepared; live testing not performed as part of this package.

## Project objective

Create a repeatable, permission-based security testing plan for a demo web application. The plan defines written authorisation, scope, exclusions, test windows, safe test methods, evidence handling, stop conditions, and reporting. It is designed for a local lab or a target explicitly authorised in writing.

## Deliverables

- `docs/security-testing-plan.md` — primary test plan and execution workflow.
- `docs/technical-report.md` — mandatory technical report, including methodology, findings status, limitations, recommendations, and references.
- `docs/methodology-and-references.md` — research rationale and reference notes.
- `templates/authorisation-and-scope.md` — permission and scope sign-off template.
- `templates/security-finding-report.md` — reusable finding/reporting template.
- `templates/test-execution-log.md` — execution record template.
- `test-cases/test-cases.csv` — test-case register with expected outcomes and safe boundaries.
- `test-cases/test-cases.md` — readable test-case table.
- `diagrams/testing-workflow.svg` — workflow diagram.
- `evidence/README.md` — evidence-handling instructions and blank evidence index.
- `video/explanatory-video-script.md` — suggested script and demonstration checklist.
- `technical-report.pdf` and `technical-report.docx` — rendered report copies (if included in this package).

## Important status and safety notes

- No real production system was tested for this project package.
- No test case is represented as passed, failed, or executed. Execution status remains **Not Run** until the intern records genuine evidence.
- Use a local lab such as OWASP Juice Shop or another intentionally vulnerable training application that you run yourself, or a target covered by explicit written authorisation.
- Do not scan, exploit, authenticate to, or access data on systems outside the approved scope.
- Stop immediately if testing affects availability, exposes real personal data, or reaches an out-of-scope asset.
- Do not commit passwords, API keys, tokens, private data, or sensitive evidence. Use synthetic accounts and redact screenshots.

## Suggested local lab

OWASP Juice Shop is an intentionally insecure training application. If you choose it, run your own local instance and keep it bound to localhost. The project is not a permission to test the public demo or any third-party deployment.

Example using Docker, only on your own computer:
```bash
docker run --rm -p 127.0.0.1:3000:3000 bkimminich/juice-shop
```
Then open `http://127.0.0.1:3000`. This command is provided as an optional lab setup example; it has not been run or validated as part of this report. If Docker is not installed, use the official OWASP Juice Shop setup documentation.

## How to use this repository

1. Review the test plan and complete the authorisation/scope template.
2. Obtain written approval before testing anything beyond your own local lab.
3. Select only relevant test cases and agree the test window and stop conditions.
4. Record every attempt in the execution log. Leave results as `Not Run` until performed.
5. Save only minimal, redacted evidence in `evidence/`.
6. Write findings using the reporting template and include reproduction steps safe enough for the approved environment.
7. Review remediation and retest only after authorisation is confirmed.
8. Replace the video placeholder below with the actual accessible video URL before final submission.

## Explanatory video

**Video URL:** https://youtu.be/kpup7Gll-tI

Do not submit this placeholder as a real video link. Record the explanation, upload it with viewing access, then update this line.

## Repository quality checklist

- [ ] Confirm intern details and task scope.
- [ ] Review and complete authorisation template for the selected lab/target.
- [ ] Run only approved test cases and record actual results.
- [ ] Add redacted evidence and findings, if any.
- [ ] Verify all citations and links.
- [ ] Record and upload explanatory video.
- [ ] Replace the video placeholder with a working URL.
- [ ] Verify repository visibility/access and final submission links.
- [ ] Enter Intern ID, name, repository URL, and video URL in the official submission tracker.
