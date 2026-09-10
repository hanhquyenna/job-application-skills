---
name: notion-linkedin-job-tracker
description: Read LinkedIn job URLs from a Notion tracking database and inspect the jobs in Chrome.
---

# Notion LinkedIn Job Tracker

Use this skill when the user wants to inspect or monitor job postings saved in a Notion job-tracking database through LinkedIn in Chrome.

## Run intent gate

- Before opening rows or LinkedIn pages, locate the exact Notion tracker and show its URL.
- If the request is ambiguous, ask the user to choose: **show the tracker**, **inspect/verify a job**, **update one job**, or **bulk reconcile selected rows**.
- State the selected scope, the matching row links, and whether the run is read-only or will update Notion. Do not infer permission to update from an open browser tab.
- Before any write, preview the target rows and properties, preserve non-empty user values, and identify the source URLs and timestamps.
- End every run with the tracker URL, row-to-LinkedIn mapping, processed count, changed fields, and unresolved rows.

## Workflow

1. Locate the user's Notion job-tracking page or database in the already-authorized browser session. Prefer the visible database table over guessing URLs.
2. Read the rows and collect the values from the `Link` property when they are LinkedIn job URLs. Preserve each job title, company, status, and URL.
3. Open the collected LinkedIn URLs in Chrome. Keep the original Notion page available so each LinkedIn page can be mapped back to its row.
4. Inspect only information visible on the job pages. Report unavailable, expired, login-gated, or removed postings clearly and continue with the remaining links.
5. When the user requests enrichment, update the existing row by property name and keep company research consolidated in `Company Information` rather than creating multiple company-fact columns. Include source URLs and research dates inside that property.
6. Before bulk updates, snapshot the target row IDs and existing values. Use idempotent updates, never overwrite non-empty user-entered fields without explicit instruction, and re-read changed rows to confirm the requested properties.
7. Do not apply to jobs, send messages, connect with people, upload files, or change Notion records unless the user separately asks for that specific action.

## Credentials and secrets

Never put a Notion token, LinkedIn credential, session cookie, or other secret in this skill, its supporting files, a prompt, or a plain-text log. If a credential is supplied, use an existing authorized session or ask the user to configure it through a secure credential mechanism. Do not repeat the secret in responses.

## Output

Return a compact mapping of job title, company, status, LinkedIn URL, and what was observed. If many rows are present, process them in batches and state which rows were checked.
