# Job Application Skills

Reusable skills for evidence-first internship and early-career applications.

These skills cover:

- conversational onboarding and connection recovery
- experience-bank maintenance
- LinkedIn/browser job sourcing and verification
- Notion job-tracker reconciliation
- JD-to-CV personalisation and fit validation
- CV document building and render QA
- truthful cover-letter and motivation-letter building

The package includes a generic `cover-letter-builder` with optional Expressive Resume LaTeX output, plus the personalised `kien-cover-letter` skill.

## Safety and privacy

Keep candidate CVs, experience-bank data, tracker exports, Notion contents, credentials, browser cookies, and workspace profiles outside this repository. Configure connections through secure host mechanisms. The skills are designed to fail closed when a JD, evidence source, or approval is missing.

## Use

Load `skills/job-application-onboarding/SKILL.md` first for a new workspace. Then route the request to the relevant skill. Each specialised skill defines its evidence rules, intent gate, approval boundary, and output checks.
