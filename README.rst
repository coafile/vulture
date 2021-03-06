vulture - Find dead code
========================

.. image:: https://travis-ci.org/jendrikseipp/vulture.svg?branch=master
   :target: https://travis-ci.org/jendrikseipp/vulture

Vulture finds unused code in Python programs. This is useful for
cleaning up and finding errors in large code bases. If you run vulture
on both your library and test suite you can find untested code.

Due to Python's dynamic nature, static code analyzers like vulture are
likely to miss some dead code. Also, code that is only called
implicitly may be reported as unused. Nonetheless, vulture can be a
very helpful tool for higher code quality.


Features
--------

* fast: static code analysis
* lightweight: only one module
* tested: tests itself and has complete test coverage
* complements pyflakes and has the same output syntax
* sorts unused classes and functions by size with `--sort-by-size`
* supports Python 2.6, 2.7 and 3.x


Installation
------------

::

  $ pip install vulture  # from PyPI
  $ pip install .        # from cloned repo


Usage
-----

::

  $ vulture myscript.py  # or
  $ python3 -m vulture myscript.py
  $ vulture myscript.py mypackage1/ mypackage2/
  $ vulture myscript.py mywhitelist.py

The provided arguments may be Python files or directories. For each
directory vulture analyzes all contained `*.py` files.

After you have found and deleted dead code, run vulture again, because
it may discover more dead code.

**Handling false positives**

You can add false positives (used code that is marked as unused) to a
Python module and add it to the list of scanned paths. We collect
whitelists for common Python modules and packages in
``vulture/whitelists/``. Pull requests are welcome.


How does it work?
-----------------

Vulture uses the ``ast`` module to build abstract syntax trees for all
given files. While traversing all syntax trees it records the names of
defined and used objects. Afterwards, it reports the objects which have
been defined, but not used. This analysis ignores scopes and focuses
only on object names.


Sort by size
------------

When using the ``--sort-by-size`` option, vulture sorts unused classes
and functions by their lines of code. This helps developers prioritize
where to look for dead code first.


Similar programs
----------------

* vulture can be used together with *pyflakes*
* The *coverage* module can find unused code more reliably, but requires
  all branches of the code to actually be run.


Participate
-----------

Please visit https://github.com/jendrikseipp/vulture to report any
issues or to make pull requests.

* Changelog: `NEWS.rst <https://github.com/jendrikseipp/vulture/blob/master/NEWS.rst>`_
* Roadmap: `TODO.rst <https://github.com/jendrikseipp/vulture/blob/master/TODO.rst>`_
