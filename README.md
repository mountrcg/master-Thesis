# Sophisticated LaTeX Thesis Template

[![Build Status](https://github.com/tubav/Thesis/workflows/test/badge.svg)](https://github.com/tubav/Thesis/actions)

from https://git.tu-berlin.de/tub-ngn-av/Master-Bachelor-Thesis/

## Abstract

During their studies most students will be faced to the decision whether
to use LaTeX or an other word processor to write a thesis. Since there are a
number of strong reasons to use the former the next step is to start
writing a LaTeX document.

Sooner or later the student will face issues or implements features that
are very common while writing a thesis in LaTeX. This is why several
instructions and even more tips are available in the Internet about
writing Theses using LaTeX.

Although one can find many minimal examples and multiple small templates, there
is no sophisticated community maintained template (i.e. everyone can collaborate)
available that demonstrates all useful features. This project aims to fill this gap by
providing a complex but stil easy to understand template. It should contain all
necessary and nice to have features someone might need writing a thesis.

So please checkout the template (for both, a thesis and a paper), test it, spread the word, and contribute.

## Main Features

* PDF support: hyperlinks, ToC, annotations, metadata, linearlization, digital signatures, PDF/A2-b
* Language support: UTF8 encoding, support for CJK and German
* Integration: buildbot, TeXlipse, graphviz, gnuplot, R, plantuml, optipng, pdfopt, ...
* Validation: orthography (incl. project dictionary), hyphens, commas, references, todos, best practices, l2tabu, chklatex, latex/bibtex warnings
* Preface: title with logo, affidavit, dedication, acknowledgements, abstract, Zusammenfassung
* Tables: content, figures, listings, tables, per chapter
* Content: examples for (multiple) images, equations, tables, listings, acronyms (with references and footnotes)
* Appendix: acronyms, glossary, index
* Bibliography: multiple files and types, link to the source page, show unreferenced items
* Other: side notes, line numbering, chapter thumbs

## Quick Start

Assuming you've already a complete LaTeX installation (at least TeX Live version 2020 - on older Ubuntu installations follow [this intruction](https://tex.stackexchange.com/questions/540429/tlmgr-in-ubuntu-20-04-local-tex-live-2019-is-older-than-remote-repository-2/545502#545502)):

```bash
git clone --recursive https://github.com/tubav/Thesis.git
cd Thesis
make clean full
make # to show all options
```

Next, open [https://github.com/tubav/Thesis](https://github.com/tubav/Thesis) for further details. Also check out [https://github.com/tubav/Paper](https://github.com/tubav/Paper).

## Installation

### Ubuntu

```bash
# Installs all TexLive packages and tools (aspell graphviz gnuplot r-base plantuml)
make deps-lin
```

### macOS

#### Minimal installation (400 MB)

```bash
brew install basictex
tlmgr install texliveonfly biber collection-fontsrecommended IEEEtran xindy
make deps
```

#### Full installation (5.5 GB)

```bash
# Installs complete TexLive and tools (aspell graphviz gnuplot r-base plantuml)
make deps-mac
```

## All make targets

```text
* clean     : Delete temporary files
* all       : Create the PDF file (run everything needed)
* full      : Create the PDF file (run LaTeX and BibTeX only)
* quicker   : Update the PDF file (just run LaTeX twice)
* quick     : Update the PDF file (just run LaTeX once)
* bib       : Update the bib file (just run BibTeX/biber once)
* bibchk    : Run some checks (e.g. biber, bibtex-check)
* verify    : Run some checks (e.g. l2tabu)
* spell     : Check for spelling errors (aspell)
* eval      : Run evaluation scripts (e.g. R)
* generate  : Generate images (gnuplot, R, dot/graphviz, ...)
* deploy    : Deploy the PDF file to a directory (e.g. for automated builds)
* update    : Get the latest sources (incl. latest library)
* open      : Opens the output file using 'open'
* ci        : Continuous Integration - watch for changes an rebuild everything
* rename    : Rename project
* unicode   : Find incompatible unicode characters
* optimize  : Optimize output (e.g. optipng)
* sign      : Sign the PDF using an X.509 certificate
* preflight : Test for PDF/A and PDF/X compatibility
```

## Proven

The template and build environment is proven to work
with a reasonable large document (250 page, 450 references),
without showing a single (unfiltered) warning message:

```bash
$ time make clean full verify bibchk
Cleaning up...done
Sorting acronyms...done
Running LaTeX...done
Running LaTeX...done
Running Index...done
Running BibTeX and Glossary...done
Running LaTeX...done
Running LaTeX...done
Running LaTeX...done
File created: thesis.pdf
Pages: 250
Running chktex...
Checking for duplicated/repeated words...
Checking config...
Checking todos...
Checking orthography...
Checking abstract...
Checking introduction...
Checking references...
Checking latex (l2tabu)...
Checking commas...
Checking hyphens...
Checking for common mistakes...
Checking for common mistakes 2...
Checking bibtex...

real	10m47.507s
user	9m0.911s
sys	0m35.007s
```
