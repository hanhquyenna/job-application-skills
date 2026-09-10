---
name: cv-builder
description: Build a tailored CV from approved content in the exact user-approved format, then render and visually validate the final PDF or DOCX.
---

Use this skill after `cv-personalizer` and `cv-validator` have completed. It owns layout and production, not evidence selection or JD matching.

Do not start if the validator has not returned a passing result for the same job ID, JD snapshot, experience-bank snapshot, and CV text.

## Run intent gate

- Before creating or changing a file, identify the requested operation: **build DOCX**, **build PDF**, **build both**, **render/visually validate an existing artifact**, or **compare the artifact with the approved reference**.
- If the request is ambiguous, ask the user to choose the artifact and operation. Do not silently overwrite a reference CV or choose a format.
- Always show the Notion tracker link and target job-row link (when tracked), the job ID, validator result, JD snapshot, experience-bank snapshot, approved section order, and output destination.
- Preview the output filename and format before writing. Keep the polished reference unchanged and never submit the CV to an employer.
- End every run with artifact links, render/format checks, content-diff result, and any unresolved limitation.

## Inputs

- The approved CV content, exact section order, and formatting reference supplied by the user.
- The target JD and the evidence map from `cv-personalizer`/`cv-validator`.
- The polished reference CV or PDF when exact visual matching is required.

## Build rules

1. Preserve the approved section sequence, headings, typography, spacing, page margins, bullet style, date format, links, and visual hierarchy. Do not introduce a new layout convention.
2. Copy approved experience-bank wording exactly. Layout changes may move or wrap text but may not rewrite it.
3. Keep the document ATS-readable: selectable text, standard headings, consistent dates, simple bullets, and no text embedded only in images.
4. Produce the requested DOCX and/or PDF as a separate file; never overwrite the polished reference.
5. Render the output to page images and inspect every page for overflow, orphan lines, broken links, clipped text, inconsistent spacing, and accidental blank pages. Iterate until clean.
6. Run a final content diff against the approved CV text and report any difference before handoff.
7. Enforce production gates: all selected bullets must have evidence IDs; the text diff must show only approved selection/order/formatting changes; extracted PDF text must match the approved content; and every rendered page must pass visual inspection.
8. If any gate fails, do not hand off the file. Return the exact failure and keep the reference document unchanged.

## Production edge cases

- Treat the approved CV text as the content checksum. Any difference in extracted text must be classified as an approved selection/order change, a layout-only change, or a failure.
- Render and extract both DOCX and PDF when both are requested. Check Unicode characters such as en dashes, curly quotes, currency symbols, plus signs, and mathematical symbols; a replacement glyph or missing character is a failure.
- Check text order after parsing, especially when the reference uses tables, columns, text boxes, headers, footers, hyperlinks, or decorative elements. Visual similarity does not prove ATS readability.
- Check page count, margin overflow, clipped text, orphan headings, bullet wrapping, blank pages, inconsistent dates, broken links, missing contact details, and font substitution.
- Use deterministic filenames containing employer, job ID, artifact type, and version. Never overwrite the reference or a previously released artifact.
- Preserve document metadata only when it is intentional; remove stale author, tracked-change, comment, and hidden-text artifacts before release.
- If a layout constraint forces content removal, stop and return the exact omitted text. Do not silently shorten or rewrite an evidence bullet.
- Keep a release manifest containing the validator state, content hash, output hash, render-check result, and the exact output path.
- Handle scanned references and OCR text conservatively: do not copy OCR-corrupted names, dates, metrics, or symbols into the CV without source confirmation.
- Treat hyperlinks, QR codes, images, icons, and visual branding as supplementary. The employer, role, dates, skills, and achievements must remain selectable and present in extracted text.
- If a requested format cannot preserve the approved content or makes the document non-parseable, return the failure and offer the next supported format instead of silently degrading it.

## Output

Return the final artifact link, render/format validation result, and any unresolved limitation. Do not submit the CV to an employer.
