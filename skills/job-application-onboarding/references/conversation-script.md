# Live onboarding smoke-test script

Use this script as a dry-run with a new or reset workspace. It tests the conversation and routing without writing to Notion or submitting applications.

## Scenario A — empty workspace

**User:** “Set up the job-application skills for me.”

**Expected agent response:**

> I’ll set up your job-application workspace. I can keep your experience evidence, find and verify internships, enrich selected companies, tailor and validate CVs, build the final DOCX/PDF, and track applications. I do not see an approved workspace profile yet.
>
> We’ll do this in stages. First, choose the CV files or Drive folder that contain your real experience. Then we’ll approve the experience bank, set your role and location preferences, connect your tracker, check your Chrome session, and inspect the polished CV that controls the format. I’ll save the setup once and remember it.

The agent must ask only for the source-CV location next, explain the upload/Drive option, and not ask for API keys.

## Scenario B — CVs supplied, connections missing

**User:** “Use these two CVs. I want finance internships first, then AI, in Amsterdam.”

**Expected agent response:**

> I found two source CVs. I’ll extract their evidence into the experience bank without rewriting the source wording, then show you which records are approved. I’ll search Amsterdam and Netherlands roles with English and Dutch query variants, while keeping English as the job-language preference unless you change it.
>
> Next I need to check your tracker and browser. Choose **Connect Notion** to authorize the intended workspace; after that I’ll discover the databases and map properties by name. Then open the signed-in Chrome profile and choose **Check browser session**. You never need to paste a Notion token or LinkedIn cookie here.

The agent must report partial progress if either connection is unavailable.

## Scenario C — reference CV and format conflict

**User:** “Use my polished Soda CV as the format.”

**Expected agent response:**

> I inspected the selected reference CV. It is a one-page serif layout with a centered name/contact line, uppercase section headings with rules, right-aligned dates, and compact bullets. Its visible order is Education → Skills → Experience → Projects.
>
> Your workspace preference says Name and personal information → Skills → Experience, with Projects only when selected. I’m keeping both records and leaving the format profile for your confirmation before the first CV build.

The agent must load this profile into `cv-builder` in inspect-only mode and must not silently choose an order.

## Scenario D — ready handoff

**Expected agent response after confirmation:**

> Your workspace is configured. The experience bank is approved, your search brief prioritizes finance, then AI, then communications, and English/Dutch searches are enabled for Amsterdam and the Netherlands. Notion and Chrome are connected and checked. The approved CV format is version 1.
>
> You can now ask me to find internships, verify a job, enrich selected companies, tailor a CV, validate the match, or build the final document. I’ll show the scope and approval state before any write.

The smoke test passes only when the profile is `Ready`, the unresolved list is empty, and agent writes remain disabled until explicitly enabled.
