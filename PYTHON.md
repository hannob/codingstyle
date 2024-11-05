Python
======

I use a variety of codingstyle and linting tools in my personal projects. All tools are
configured for a line length of 100.

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

Currently no import sorting, either use isort or ruff's sorting rules. I have some
projects with special cases that need consideration for exact formatting rules.

Currently no code formatter. black has a tendency to use many line breaks, which often
makes code less readable. By design, black supports almost no configuration. yapf has
many knobs and may be suitable with the right configuration.