# Expressive Resume format reference

Source repository: https://github.com/thehale/expressive-resume

Expressive Resume is an MIT-licensed LaTeX template pair for resumes and cover letters. Its README describes a declarative, ATS-oriented workflow with a matching `ExpressiveCoverLetter` document class. Use the template only when the user selects it or their approved format profile names it.

## Minimal cover-letter shape

```tex
\documentclass{ExpressiveCoverLetter}

\begin{document}

\coverletterheader{Full Name}
    {\email{you@example.com}}{\linkedin{username}}
    {\phone{123-456-7890}}{\location{City, Country}}

\vspace{0.25in}
\today
\vspace{0.15in}

Dear Hiring Manager,

First paragraph.

Second paragraph.

Best,

Full Name

\end{document}
```

The template's supported contact helpers include `\email{}`, `\phone{}`, `\linkedin{}`, `\github{}`, and `\location{}`. The README also documents optional inline `\tech{}` highlights, but a cover letter should use them sparingly and only for skills supported by the evidence map.

## Build rules

- Keep the letter as ordinary paragraphs separated by blank lines. Do not use a table, text box, column layout, or decorative image for the body.
- Escape LaTeX-sensitive characters in user text (`&`, `%`, `$`, `#`, `_`, `{`, `}`, `\\`) while preserving visible wording.
- Keep contact fields sourced from the approved CV/profile. Omit unknown fields instead of adding placeholders.
- Compile with the repository's documented VS Code devcontainer when a local LaTeX toolchain is unavailable. Render the resulting PDF and inspect every page before delivery.
- Treat the template as a presentation layer. The active JD, evidence map, and no-invention rules remain authoritative.
