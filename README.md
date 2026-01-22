# Jaime Travesedo's PhD thesis source

LaTeX source for my thesis **“Precision spectroscopy and control of individual nuclear spins in the solid state”** performed in the Quantronics group between 2022 and 2026. The document uses the [kaobook class](https://github.com/fmarotta/kaobook).

- Main entry point: `main.tex`
- Bibliography: `bibliography.bib` (compiled with **biber** via `biblatex`/`kaobiblio`)
- Index: enabled via `makeindex` (`\makeindex` / `\printindex`)

## Build

### Requirements

- A LaTeX distribution (TeX Live recommended).
- `latexmk`
- `biber` (for the bibliography)
- `makeindex` (for the index)
- The [`kaobook` class](https://github.com/fmarotta/kaobook) (the document uses `\documentclass{kaobook}`).
  - If it’s not available in your TeX distribution, follow the installation instructions in the kaobook repository.

### Compile to PDF

From the project root:

```bash
latexmk -pdf -interaction=nonstopmode -file-line-error main.tex
```

This should produce `main.pdf`. With a standard `latexmk` setup, `biber` will be invoked automatically when needed.

### Index (if it doesn’t update automatically)

If the index is missing or not updating, run:

```bash
makeindex main
latexmk -pdf -interaction=nonstopmode -file-line-error main.tex
```

## Clean

Remove intermediate files:

```bash
latexmk -c
```

## Project layout

- `main.tex`: master document (includes front matter, chapters, appendix)
- `preamble.tex`: packages/macros
- `bibliography.bib`: BibLaTeX/Biber database
- `frontmatter/`: abstract/acknowledgements and other front matter
- `chapter*/`: individual chapter sources
  - `chapter*/figures/`: per-chapter figures
- `appendix/`: appendix source