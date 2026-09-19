# Kien output profile

## FORMATTING SPEC

- **Length:** 250–320 words is the target zone, 400 is the hard ceiling, fits one page. A tight 250–300 words with real specificity outperforms a padded 400. If a letter is running long, cut a supporting proof point before cutting the main anecdote; a thesis line is optional and should be the first structural sentence removed when it sounds manufactured.
- **Layout:** block format, flush left, no indentation. Single-spaced within paragraphs, one blank line between paragraphs and between header/greeting/body/sign-off.
- **Header (for the docx/print version only — omit if delivering as an email body):**
  1. Name, city, email, phone — pulled from the CV provided this session
  2. Blank line
  3. Today's date
  4. Blank line
  5. Recipient's name/title and company name, if known — otherwise omit this block rather than guessing
- **Greeting** — adapt to company size/culture (per the recruiter source):
  - Hiring-manager/addressee name explicitly identified + traditional/corporate JD tone → "Dear [Name],"
  - Posting contact name only, with no indication they are the addressee → use "Dear Hiring Manager,"
  - Name unknown + traditional/corporate tone → "Dear Hiring Manager,"
  - Small company / startup with informal JD tone → "Hi [Team/Company] Team," is acceptable
  - Never "To Whom It May Concern," never "Hey"
- **Sign-off** — match the same register as the greeting: "Best," or "Sincerely," for traditional/corporate; "Best," or a first-name-only sign-off is fine for informal startup contexts. Followed by the typed name pulled from the CV.
- **Font/style:** Arial. If generating a .docx, use the same Google-Docs-safe font-embedding fix as any Arial-based docx build (post-process styles.xml so no style falls back to a substituted font).
- **ATS-safe:** no images, no text boxes, no tables for the body text (a header block may use a borderless 2-column table if a right-aligned date is wanted), no decorative elements. Plain extractable text throughout.
- **File naming:** `[FirstName]_[LastName]_[Company]_[Role]_CoverLetter.docx`, using the name from the CV provided.

---

## OUTPUT

Always deliver both:
1. **Plain text in chat** — the final text after the single `humanizer` pass, ready to paste into an email body or application portal text box.
2. **A matching .docx file** — built with docx.js + JSZip, Arial throughout, Google-Docs-safe (font-embedding fix, no tab stops for date alignment, DXA table widths if a header table is used). If `docx` and `jszip` aren't already installed in the build environment, install them first:
   ```bash
   mkdir -p /tmp/coverletter_build && cd /tmp/coverletter_build && npm install docx jszip
   ```
   Build the header block, body paragraphs (plain `Paragraph`/`TextRun`, no bullets needed for a cover letter), and sign-off, then run the same `injectFontsIntoStyles` post-processing step so the file renders identically in Word, Preview, and Google Docs.

---
