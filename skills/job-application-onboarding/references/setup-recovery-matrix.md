# Setup recovery matrix

The onboarding agent must handle each dependency independently. The response examples are interaction requirements, not text that must be copied verbatim.

| Dependency or failure | Tell the user | Continue with | Block until restored |
|---|---|---|---|
| Workspace profile missing | “I’m starting a new workspace.” Explain that setup will be saved once. | Empty profile and Explore mode | Nothing; personalised actions remain limited |
| Profile malformed or old schema | “Your saved setup needs a small migration.” Preserve a backup and explain the version. | Read-only inspection of recoverable fields | Actions depending on ambiguous fields |
| No CV supplied | “I can search jobs, but I cannot claim CV fit yet.” Explain upload, Drive, or local-path options. | Job discovery and preference matching | Evidence match, CV tailoring, CV validation, document build |
| CV unreadable, scanned, or OCR-corrupted | “I can see the file but cannot trust its text.” Explain how to provide a clearer PDF/DOCX. | Search and non-CV tracking | Experience approval and CV output |
| Several CVs with no authority | “I found multiple possible source CVs.” Show filenames and ask which is authoritative. | Continue non-document setup | Format profile and application CV build |
| No format reference | “No personal CV format is selected.” Offer a system ATS-safe default and label it. | Experience and job setup | Exact-format build until approved |
| Format reference cannot render | “The reference opens but its visual format could not be inspected.” Explain the supported DOCX/PDF alternatives. | Text-only experience import | Exact-format build |
| Experience bank missing | “Your source CVs are available, but the reusable evidence bank is not approved.” | Preference search and tracking | Evidence-based tailoring and validation |
| Experience bank conflict | “Two approved records conflict.” Show source paths and ask which record wins for this run. | Unaffected records and job discovery | Conflicting evidence selection |
| Notion not connected | “Notion is not connected.” Tell the user to choose Connect Notion and authorize the intended workspace. | Local database and queued sync | Notion writes and Notion-specific row mapping |
| Notion OAuth cancelled or denied | “The connection was cancelled, so no Notion data was changed.” Offer retry or local mode. | Local database | Notion operations |
| Notion workspace has no accessible database | “The connection works, but no permitted tracker database was found.” Explain how to share the database with the integration. | Local database and setup | Notion sync |
| Notion schema mismatch | “The tracker is reachable, but required properties are missing or ambiguous.” Show the property names and proposed mapping. | Read-only inspection | Writes to affected properties |
| Notion rate limit or transient failure | “Notion is temporarily unavailable.” Give the retry status and keep the local run manifest. | Local queue and read-only work | Immediate Notion write |
| Chrome extension unavailable | “The Broods browser bridge is not connected.” Explain how to install/enable it or use public sources. | Local jobs and permitted public sources | Browser actions |
| Chrome session expired | “LinkedIn needs you to sign in again.” Tell the user to log in in the visible Chrome tab. | Non-LinkedIn sources and local data | LinkedIn verification |
| MFA, CAPTCHA, or rate limit | “LinkedIn requires a user check.” Pause and hand control to the user. | Other sources and saved jobs | Automated LinkedIn step |
| Target tab closed or changed | “The saved tab is no longer the same page.” Ask the user to reopen the requested page. | Other jobs and sources | That page's verification |
| Drive not connected | “Drive is not connected.” Explain Connect Drive and folder selection. | Local CV paths and existing bank | Drive scan |
| Drive permission denied or folder empty | “I cannot read the selected folder.” Explain permission or folder correction. | Existing local files | Drive import |
| Claude/API unavailable | “The AI service is unavailable or out of credits.” Explain that no output was fabricated. | Deterministic parsing, tracking, and saved data | AI enrichment, matching, and drafting |
| GitHub unavailable | “The repository is not reachable.” Explain that local files remain safe. | Local work and export | Git sync |
| No search results | “No roles matched this exact brief.” Show the queries and offer controlled broadening. | Broadened search only after user choice or declared fallback | High-priority recommendations |
| Conflicting preferences | “Your preferences conflict.” Show the conflict and ask which rule wins. | Unaffected searches | Priority ranking and tailoring |
| Work authorisation unknown | “I do not have your work-authorisation rule.” Explain where to set it. | Search and factual job capture | Visa-fit recommendation |
| Source job closed or unverifiable | “The listing cannot be confirmed as active.” Preserve the URL and reason. | Company research and other jobs | Active-job recommendation |

## Recovery invariants

- Preserve user-entered data and approved evidence.
- Never replace `Unknown` with an inference.
- Never retry a failed external write without re-reading the target.
- Never ask for secrets in chat.
- Never claim a connection is healthy without a current read-only check.
- Always show the next useful action and the affected capability.

