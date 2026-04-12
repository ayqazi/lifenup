1. Do not change legal content. All clauses, wording, punctuation, numbering, names, dates, addresses, defined terms, and schedules must remain word-for-word identical to the provided source text. The only permitted non-style content edits are strictly corrective rendering fixes (for example, replacing a literal currency symbol with a robust macro that renders correctly).
2. Make the document look like a conventional printed legal document in England and Wales: plain, conservative, and dense. Use a well-known serif font, small base font size, modest leading, and restrained headings.
3. Ensure currency renders correctly in the final PDF. Do not rely on literal “£” rendering. Use `\textsterling` wherever sterling amounts appear (including bold amounts).
4. Use pdfLaTeX-compatible settings by default: `fontenc` T1, `inputenc` utf8, and a symbol package that provides `\textsterling`.
5. Avoid visual “blog” styling. Do not use sans-serif body fonts. Do not use oversized titles. Do not use colored headings. Keep hyperref link styling unobtrusive.
6. Keep margins suitable for printed legal docs on A4. Keep page numbering centered in the footer. Remove decorative header rules.
7. Keep lists compact with consistent indentation. Keep section and subsection styles conservative and not oversized.
8. Preserve the existing document structure (sections, schedules, tables) and do not reorganize content. Only adjust formatting commands and packages to enforce the style.
9. Output a complete standalone LaTeX document that compiles with Tectonic/pdflatex without errors and produces correct glyphs for sterling amounts.

---

## LaTeX template (no comments)

```latex
\documentclass[10pt,a4paper]{article}

\usepackage[a4paper,margin=2.2cm]{geometry}

\usepackage[T1]{fontenc}
\usepackage[utf8]{inputenc}
\usepackage{textcomp}

\usepackage{newtxtext}
\usepackage{newtxmath}

\usepackage{microtype}
\usepackage{setspace}
\usepackage{parskip}
\usepackage{enumitem}
\usepackage{longtable}
\usepackage{array}
\usepackage{booktabs}
\usepackage{tabularx}
\usepackage{hyperref}
\usepackage{fancyhdr}
\usepackage{titlesec}
\usepackage{xcolor}

\hypersetup{
    colorlinks=true,
    linkcolor=black,
    urlcolor=blue,
    pdftitle={DOCUMENT TITLE},
    pdfauthor={AUTHOR}
}

\setstretch{1.05}

\pagestyle{fancy}
\fancyhf{}
\fancyfoot[C]{\thepage}
\renewcommand{\headrulewidth}{0pt}

\titleformat{\section}{\normalsize\bfseries}{\thesection.}{0.6em}{}
\titleformat{\subsection}{\normalsize\bfseries}{\thesubsection.}{0.6em}{}

\setlist[itemize]{leftmargin=1.8em, itemsep=0.2em, topsep=0.4em}
\setlist[enumerate]{leftmargin=1.8em, itemsep=0.25em, topsep=0.4em}

\newcolumntype{Y}{>{\raggedright\arraybackslash}X}

\newcommand{\GBP}[1]{\textsterling #1}

\begin{document}

\begin{center}
{\Large\bfseries DOCUMENT MAIN HEADING}\\[0.35em]
{\normalsize DOCUMENT SUBHEADING}
\end{center}

\vspace{0.6em}

CONTENT_GOES_HERE

\end{document}
```

Use this template by replacing:
- `DOCUMENT TITLE`, `AUTHOR`, `DOCUMENT MAIN HEADING`, `DOCUMENT SUBHEADING`
- `CONTENT_GOES_HERE` with the full legal text, preserving it word-for-word, and replacing every sterling amount with `\textsterling` (or `\GBP{...}` if you prefer a single macro), including inside `\textbf{...}`.
