# Specific case of Linux shell scripts

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)

First I have almost only experience with Linux, not Unix.
So I am talking about the former below.

## Writing good shell script is easy and hard at the same time

Writing good shell scripts is not harder than in any other programming language, but because it is
sometime only seen as [glue code](https://en.wikipedia.org/wiki/Glue_code), developer tends to
overlook at their language's documentation, and just copy-paste from example, thus staying
beginners for a very long part of their career.

I recommend starting with [bash](https://www.gnu.org/software/bash/), which is widespread or
compatible with most Linux shells. Its documentation is well written, and it has some of the
string functions that so many beginners lack compared to
[POSIX](https://en.wikipedia.org/wiki/POSIX) shells.

The syntax is half common, half very specific. So there is a small learning curve, but the payoff
is huge (I think).

## It's dawn hackable, and the best move for simple prototyping or glue code

Shell script are at the range of a beginner: just open it and start messing with its code, then
run it again… that's it.  
Most sysadmins I know have debuted like this.

## It's almost portable everywhere (even in Microsoft Windows now !)

Because a shell is installed by default in all *Linux* flavors (and also *Windows* now), you can run
your script without having to install anything (except the other programs it might run).

## Test suite is reusable for other implementations

There is a good test suite called [shUnit2](https://github.com/kward/shunit2/).  
The big advantage over many other languages, it that it can be re-used to run other implementations
of the program in other languages (compiled or interpreted).

## Fewer quality tooling: no quality metrics, but some static analysis tools

The downside of *Linux* shell scripts is that the tooling around is a little bit restricted, but you
already have the following which might be enough :

- [shellcheck](https://www.shellcheck.net/): a linter with static analysis
- [bashcov](https://github.com/infertux/bashcov): only supports *Bash* (written in *Ruby*)
- [kcov](https://github.com/SimonKagstrom/kcov/blob/master/INSTALL.md): only supports *Bash* too
- [shfmt](https://github.com/mvdan/sh): a static analysis tool to format *Bash* scripts

I regret the lack of code quality tool. May be some exists, let
[me](mailto:mica.devel@gmail.com) know.


## About this document

### License: CC-BY-SA

[![License: CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/80x15.png)](https://creativecommons.org/licenses/by-sa/4.0/)  

Copyright © 2020-2021 Michael Bideau, France  
This work is licensed under a
[Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).

### Author: Michael Bideau

Michael Bideau, France

### Production: 0.5 hour

It took me about **0.5 hour** to write that document, from version 1 to the one you see now.

If you value that work, think about saying thank you, giving feedback, and sharing it.

### Made with: Formiko and Vim, plus some helpers/linters

I started with [formiko](https://github.com/ondratu/formiko), then used [vim](https://www.vim.org/)
with linters to help catching mistakes and badly written sentences:

- [mdl](https://github.com/markdownlint/markdownlint)
- [proselint](http://proselint.com/)
- [write-good](https://github.com/btford/write-good)
