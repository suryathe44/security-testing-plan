# Final Submission Checklist — Intern ID 2418

**Deadline: 25 October 2026**

This checklist separates prepared documents from items that still require the intern's real-world action. Do not submit placeholders as completed work.

## A. Review the package
- [ ] Read `README.md`, `docs/security-testing-plan.md`, and the technical report.
- [ ] Confirm the intern name, ID, assignment, and deadline.
- [ ] Check the references and the assignment instructions.
- [ ] Complete `templates/authorisation-and-scope.md` for the chosen lab/target before testing.
- [ ] Do not mark a test as run unless it was genuinely performed.

## B. If you conduct a lab test
- [ ] Use your own local lab or a target explicitly authorised in writing.
- [ ] Record the test case, timestamp/time zone, action, actual observation, and status.
- [ ] Use synthetic accounts/data; stop if unexpected sensitive data or availability impact occurs.
- [ ] Store only redacted, public-safe evidence in this repository.
- [ ] Update the technical report with actual results, not assumptions.

## C. Create the GitHub repository
1. Sign in to your own GitHub account.
2. Create a new repository named `security-testing-plan-2418`. Choose public only if you have checked that every committed file is safe to share; otherwise keep it private until reviewed.
3. Extract this ZIP on your computer.
4. Open a terminal in the extracted `security-testing-plan-2418` folder.
5. Run the following commands, replacing the URL with the actual repository URL shown by GitHub:

```bash
git init
git add .
git status
git commit -m "Add permission-based security testing plan"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/security-testing-plan-2418.git
git push -u origin main
```

Before `git add .`, review the folder and make sure no secret or raw sensitive evidence is present. If Git asks for identity, configure your own name/email locally. Never paste a password or token into this repository.

If Git is not installed, install it using the official documentation for your operating system or upload the extracted files through GitHub's web interface.

## D. Record and publish the explanatory video
- [ ] Use `video/explanatory-video-script.md` as a guide.
- [ ] Record a 5–7 minute explanation in your own words.
- [ ] Show the repository, workflow, test-case register, report, evidence template, and limitations.
- [ ] Do not claim unperformed tests or show personal data/secrets.
- [ ] Upload to YouTube as Unlisted or to Google Drive with viewing access enabled.
- [ ] Test the link in a private/incognito window.
- [ ] Update the `Video URL` line in `README.md` with the real URL and push the README change.

## E. Final submission tracker
Use the official tracker supplied by RedKross:
https://docs.google.com/spreadsheets/d/1GuQMagtgPgLGukcVJYkpmrvW2-GZ1C7b/edit?usp=sharing&ouid=112302172111518396510&rtpof=true&sd=true

Enter only your own row and verify:
- Intern ID: `2418`
- Name: `Surya Singh Chauhan`
- Repository URL: actual repository URL
- Video URL: actual accessible video URL

Do not edit another intern's row. Confirm the repository contains the technical report and all task deliverables before submitting.

## Current honest status
- Documentation package: prepared.
- Technical report: prepared.
- Candidate test register: prepared; every test is initially `Not Run`.
- Actual lab execution: not performed as part of preparing this package.
- GitHub repository publication: not completed by this package.
- Explanatory video: script prepared; recording/upload still required.
- Tracker submission: still required after repository and video links are real.
