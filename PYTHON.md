Python
======

I use a variety of codingstyle and linting tools in my personal projects. All tools are
configured for a line length of 100.

I currently run the CI with Python 3.12 and 3.x (latest GitHub-supported branch), and I
usually do not put extra effort into supporting extremely old Python versions.

pycodestyle
-----------

Disabled rules:

* E203 causes false positives, see https://github.com/PyCQA/pycodestyle/issues/373
* W503 (line break before binary operator) is incompatible with W504 (line break after
  binary operator)

`pycodestyle --max-line-length=100 --ignore=W503,E203 [files]`

pyupgrade
---------

Usually use it with the latest python version.

Unfortunately, pyupgrade has no "check only" mode.

`pyupgrade --py313-plus [files]`

pyflakes
--------

Finds unused imports and other issues.

`pyflakes [files]`

dlint
-----

Security tool, implemented as ruleset for flake8.

Disabled rules:

* DUO107: Obsolete XML API warnings
* DUO131,DUO123: Warnings about disabled TLS certificate validation

`flake8 --select=DUO --ignore=DUO107,DUO123,DUO131 [files]`

isort
-----

Sorts imports alphabetically.

Note: Execute within directory to properly detect first party imports.

pylint
------

Very extensive, but comes with long list of rules I don't want.

See [pylint rules disabled permanently](python/pylint-disable.txt) and [pylint rules
disabled that I might reconsider](python/pylint-reconsider.txt).

Currently, not all my code is compliant, should be fixed ASAP.

ruff
----

Very extensive, enable ALL rules and selectively disable modules and rules.

See [ruff rules disabled permanently](python/ruff-disable.txt) and [ruff rules disabled
that I might reconsider](python/ruff-reconsider.txt).

future
------

Currently no code formatter. black has a tendency to use many line breaks, which often
makes code less readable. By design, black supports almost no configuration. yapf has
many knobs and may be suitable with the right configuration.
