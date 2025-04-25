# Heudiasyc PhD Thesis LaTeX Template (Unofficial)

[![License: GPL v2](https://img.shields.io/badge/License-GPL%20v2-blue.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)

This repository provides an unofficial LaTeX template designed for PhD students writing their theses at the **Heudiasyc laboratory (UMR CNRS 7253)**, affiliated with the **Université de technologie de Compiègne (UTC)**.

## Overview

This template builds upon the excellent **"A Classic Thesis Style"** ([original repo](https://bitbucket.org/amiede/classicthesis/src/master/)) by **André Miede**. It has been reorganized, customized, and extended by **Mathieu Cocheteux** to align with the specific requirements, formatting guidelines, and common practices within the Heudiasyc laboratory.

The goal is to provide a clean, professional, and user-friendly starting point, allowing students to focus on the content of their research while adhering to expected thesis presentation standards.

## Features

*   **Heudiasyc-specific Customizations:** Tailored title page, potential logo integration (check `hdsthesis-config.tex`), and structural adjustments.
*   **Classic Thesis Style:** Inherits the elegant and readable typography of the original style.
*   **Structured Template:** Pre-defined sections for all standard thesis components (Abstract, Publications, Acknowledgements, Chapters, Bibliography, etc.).
*   **Configurable:** Easily customize personal details, document options, and loaded packages via `hdsthesis-config.tex`.
*   **Organized:** Clear directory structure for chapters (`chapters/`), preliminary materials (`prelims/`), bibliography (`bibliography/`), and figures (`images/`).
*   **Modern Bibliography:** Uses `biblatex` with `biber` for flexible and powerful bibliography management.
*   **Helper Tools:** Includes configurations for `latexindent` (`latexindent.yaml`) and a `.gitignore` file optimized for LaTeX projects.

## Prerequisites

Before using this template, ensure you have:

1.  **A Recent LaTeX Distribution:**
    *   **TeX Live:** Recommended for Linux/macOS/Windows ([https://www.tug.org/texlive/](https://www.tug.org/texlive/)). Usually includes `biber`.
    *   **MiKTeX:** Common on Windows ([https://miktex.org/](https://miktex.org/)). Make sure `biber` is installed or install it via the package manager.
2.  **Biber:** Required for processing the bibliography with `biblatex`. It's typically included with TeX Live and can be installed with MiKTeX.
3.  **LaTeX Editor (Recommended):** An editor like [VS Code](https://code.visualstudio.com/) with the [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) extension, [TeXstudio](https://www.texstudio.org/), or [Overleaf](https://www.overleaf.com) (by uploading the template) can simplify the compilation process.
4.  **(Optional) `latexmk`:** A Perl script for automating the build process.
5.  **(Optional) `latexindent`:** For automatically formatting your `.tex` source files according to `latexindent.yaml`.

## How to Use

1.  **Clone or Download:** Get a copy of this template repository.

2.  **Configure `hdsthesis-config.tex`:**
    *   Open `hdsthesis-config.tex`.
    *   **Section 1:** Review and adjust template style options (e.g., `drafting`, `tocaligned`, `eulerchapternumbers`). Consult comments and the original Classic Thesis documentation for details.
    *   **Section 2:** **Crucially, update all `\newcommand` definitions with your personal information** (thesis title, your name, supervisors, faculty, university, defense date, etc.).
    *   **Section 3 onwards:** Add/remove necessary LaTeX packages for your specific needs.

3.  **Write Your Content:**
    *   **Chapters:** Place your chapter `.tex` files in the `chapters/` directory (or its subdirectories like `chapters/INTRO/`).
    *   **Preliminary Sections:** Edit the content of files in `prelims/` (e.g., `Abstract.tex`, `Acknowledgments.tex`).
    *   **Bibliography:** Add your references to the `.bib` file(s) in the `bibliography/` directory. Ensure the `\addbibresource` command(s) in `HDSThesis.tex` point to your file(s).
    *   **Figures:** Place image files in the `images/` directory and reference them using relative paths (e.g., `images/my_figure.pdf`).

4.  **Compile the Thesis:**

    *   **Main File:** The main document to compile is `HDSThesis.tex`.
    *   **Using `latexmk` (Recommended):**
        *   Simply run `latexmk -pdf HDSThesis.tex` in your terminal from the project root.
        *   `latexmk` should automatically detect the need for `biber` and run the necessary compilation steps (`pdflatex` -> `biber` -> `pdflatex` -> `pdflatex`).
        *   If `latexmk` doesn't use `biber` automatically, you might need a `.latexmkrc` file in the project root with the following content:
          ```perl
          $pdf_mode = 1;
          $bibtex_use = 2; # Use biber
          $out_dir = 'build'; # Optional: Output auxiliary files to a build directory
          # Ensure pdflatex is used
          $pdflatex = 'pdflatex %O %S';
          ```
        *   To clean up auxiliary files: `latexmk -c`
    *   **Manual Compilation (using `pdflatex` and `biber`):**
        Run these commands in sequence in your terminal:
        1.  `pdflatex HDSThesis.tex`
        2.  `biber HDSThesis` (Note: use the base name, not `HDSThesis.bcf`)
        3.  `pdflatex HDSThesis.tex`
        4.  `pdflatex HDSThesis.tex` (A final run ensures all cross-references are updated).

## Directory Structure

```plaintext
.
├── HDSThesis.tex           # Main LaTeX file - orchestrates includes
├── hdsthesis-config.tex    # ★ Your main configuration file ★
├── hdsthesis.sty           # Core style definitions (modify with caution)
├── bibliography/           # Directory for .bib bibliography files
│   └── bibliography.bib    # Example bibliography file
├── chapters/               # Directory for main thesis chapters (.tex files)
│   ├── INTRO/              # Subdirectory for Introduction chapter(s)
│   │   └── Introduction.tex
│   ├── CONTRIBUTIONS/      # Subdirectory for Contribution chapter(s)
│   └── CONCLUSION/         # Subdirectory for Conclusion chapter(s)
├── prelims/                # Directory for preliminary sections (.tex files)
│   ├── Abstract.tex
│   ├── Acknowledgments.tex
│   ├── Contents.tex        # Generated by LaTeX - Do Not Edit Manually
│   ├── Publications.tex    # List your publications here
│   ├── Titleback.tex       # Back side of the title page (colophon)
│   └── Titlepage.tex       # Defines the title page layout
├── images/                 # Suggested directory for figures and images
├── .gitignore              # Standard LaTeX ignores for Git
├── latexindent.yaml        # Configuration for the latexindent tool
├── LICENSE                 # Copy of the GPL v2 License
└── README.md               # This file
```

## Visual Preview

*(Optional: Consider adding a screenshot of the title page or a sample chapter page here.)*

## Contributing

While this is an unofficial template, suggestions for improvements that align with Heudiasyc's general practices are welcome. Please feel free to open an issue or submit a pull request.

## Reporting Issues

If you encounter bugs or issues with the template itself (not general LaTeX problems), please report them using the GitHub issue tracker.

## License

This template inherits the license from "A Classic Thesis Style", which is the **GNU General Public License v2.0 or later**. A copy of the license should be included in the file `LICENSE`. The original copyright notices are preserved in the relevant `.tex` and `.sty` files.

## Acknowledgements

*   **André Miede:** For the foundational "A Classic Thesis Style".
*   **Mathieu Cocheteux:** For adapting and tailoring this version for Heudiasyc.
