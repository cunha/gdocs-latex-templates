# gdocs-latex-templates

## Instructions

This repository contains templates to allow you to use Google Docs to
edit research papers. For more information on how this works, see [How
to Use Google Docs To Write a Research
Paper](https://docs.google.com/document/d/1jp_z1cL3vtCdYa0ZPz6TR2JOtLi87Ur29O0nCSwJ3qA/)

## Modifying Paper

To make modifications to the paper, open the paper in Google Docs. You can create copies of one of the provided templates.

* [ACM submission](https://docs.google.com/document/d/1YJg3v-OKCr4KMZUlCs-z6hMgGwmJURUCiztmFF2Gce4/edit?usp=sharing)
* [ACM camera-ready](https://docs.google.com/document/d/17Yy8kO-9p3tjWJhKiZjVf-LUykfiuZRcdD40_bnnGMA/edit?usp=sharing)

## Compiling Paper for Working Drafts

When you're compiling for a draft, you may have missing figures or other
problems that prevent error free compilation. You can instruct LaTeX and
make to keep going whenever it encounters an error with the following
command:

``` {sh}
make clean && make MODE='"batch"' -i
```

What are those flags doing?

- `MODE='"batch"'` triggers the use of `--interaction=batchmode` for `pdflatex`, reducing the amount of output to the screen and also ensuring that `pdflatex` halts if there is an error (instead of asking for input).
- `-i` instructs make to keep going and complete all rounds of `pdflatex`

## Compiling Paper for Submissions

``` {sh}
make clean && make
```

Always use `make clean && make` so that any errors are clearly exposed.
The flag `--halt-on-error` is set for `pdflatex` by the `Makefile` to avoid annoying interaction prompts on failure

## Troubleshooting Compilation

By running `make clean`, you will force a new copy of the paper to be downloaded. You may want to always use `make clean && make` or `make clean && make MODE='"batch"' -i`

Line numbers for compilation errors refer to the `.tex` file built in by `make`, `pandoc`, and `sed`. Checking the final `.tex` file usually helps with debugging compilation breaks.

## What goes where?

Only changes to the bib, the template, and figures need to be committed.
All other changes are tracked by Google Docs.
