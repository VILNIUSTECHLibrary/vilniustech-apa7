# VILNIUS TECH – APA 7th edition for LaTeX

Official VILNIUS TECH entry point for using the APA 7th edition citation and reference style in LaTeX.

## Design

This package is intentionally a thin wrapper around the standard [`biblatex-apa`](https://ctan.org/pkg/biblatex-apa) implementation. It does **not** copy, fork, or modify the APA 7 formatting rules.

Architecture:

`VILNIUS TECH – APA 7th edition` → `biblatex-apa` → `APA 7`

The package does not contain VILNIUS TECH-specific citation or bibliography formatting rules.

## What the package provides

Loading `vilniustech-apa7` loads:

- `csquotes`, required by `biblatex-apa`;
- `biblatex` with `style=apa`;
- the `biber` backend, required by `biblatex-apa`.

The installed/current version of `biblatex-apa` is used. This package does not pin a particular `biblatex-apa` version.

The APA style itself supplies its own data model and APA language mappings. No APA `.bbx`, `.cbx`, `.dbx`, or `.lbx` files are copied into this package.

## Requirements

Install the current versions of:

- LaTeX;
- `biblatex`;
- `biblatex-apa`;
- `csquotes`;
- Biber.

The current CTAN release of `biblatex-apa` requires `csquotes >= 4.3`, `biblatex >= 3.4`, and Biber. See the package documentation for details.

## Basic use

```tex
\documentclass{article}
\usepackage[american]{babel}
\usepackage{vilniustech-apa7}
\addbibresource{references.bib}

\begin{document}

A parenthetical citation \parencite{example}.

A narrative citation \textcite{example}.

\printbibliography

\end{document}
```

Compile with LaTeX and Biber, for example:

```text
pdflatex main
biber main
pdflatex main
pdflatex main
```

On Overleaf, select Biber as the bibliography processor if it is not selected automatically.

## Options

Options supplied to `vilniustech-apa7` are passed through to `biblatex`, so normal `biblatex` options remain available. The wrapper itself fixes the citation/reference style to `apa` and the backend to `biber`.

For example:

```tex
\usepackage[sorting=nyt]{vilniustech-apa7}
```

Do not use another `biblatex` style with this package: the purpose of this package is specifically to provide the APA 7 entry point.

## Languages

`biblatex-apa` provides the APA localization files. The wrapper does not replace or modify them. Choose the document language using the normal LaTeX language mechanisms such as `babel` or `polyglossia`.

For example:

```tex
\usepackage[english]{babel}
\usepackage{vilniustech-apa7}
```

## Compatibility

The package is intended to work wherever the required LaTeX, `biblatex`, `biblatex-apa`, `csquotes`, and Biber versions are available, including:

- Overleaf;
- TeX Live;
- MiKTeX;
- Windows;
- macOS;
- Linux.

## Relationship to VILNIUS TECH reference-manager styles

The package is the LaTeX counterpart of the VILNIUS TECH APA 7th edition style used in reference-management software. It intentionally delegates the actual APA citation and bibliography rules to the standard `biblatex-apa` implementation.

It is independent of Zotero, Mendeley, and EndNote.

## License

The wrapper code in this repository is released under the LaTeX Project Public License, version 1.3c. See `LICENSE`.

`biblatex-apa` is a separate dependency distributed under its own LPPL 1.3c license. This repository does not redistribute its source code.

## Development

A minimal regression test is provided in `test/`. It is compiled with LaTeX and Biber to verify that the wrapper loads the APA style and produces a bibliography.

## CTAN

The intended CTAN package name is `vilniustech-apa7`.

The CTAN submission should contain this package's files only; `biblatex-apa` remains an external dependency.
