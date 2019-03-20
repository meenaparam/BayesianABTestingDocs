London Python Sprint -- Implement a Bayesian A/B testing framework (LPS-Bayesian)
=================================================================================

Table of contents
----------------
Introduction 

Technologies 

Launch





Introduction
---------

The LPS-Bayesian project describes to developers how to setup a Bayesian A/B testing project from scratch. This read me serves as a descriptive manual of the steps necessary to enable sprint participants to perform and implement Bayesian A/B testing (regardless of OS).

This README outlines the following:
Creation of a repository, unit tests and benchmarks
Source code and dependencies
Continuous integration and linting
Packaging


This document provides instructions for sprint users implementing Bayesian A/B Testing.


Technologies
------------



Launch
------


Additional elements such as: 

Illustrations
Scope of functionalities 
Examples of use
Project status 
Sources
Other information


Components to use for Bayesian A/B Testing
==========================================


////////////////////////////////////////////////


The following sections outline various files to download and repositories to
clone into your devinabox including:

- version control tools
- compiler
- CPython
- PEPs
- Devguide
- coverage.py





//Mercurial
---------




//A Compiler
-----------



.. _Visual Studio Community edition: https://www.visualstudio.com/en-us/products/visual-studio-community-vs.aspx

//CPython
-------


//PEPs
----

Clone the `PEP repository`_ and build it (use the venv you created to build the
CPython docs if necessary). This allows sprinters a local copy to reference
for a PEP and it allows using the easier-to-read HTML version.

No specific guidelines for building the PEPs are provided since there is only
a slim chance sprint participants will be editing a PEP.

.. _PEP repository: http://hg.python.org/peps


//Devguide
--------


.. _devguide repository: http://hg.python.org/devguide


//Coverage.py
-----------

#. Download coverage_ (need a special file that is not part of the normal
   distribution of coverage, so can't just use pip)
#. Build CPython: ``./build_cpython.py``
#. Create an venv: ``./cpython/python -m venv venv``
#. Extract coverage: ``tar -x -f coverage-*.tar.gz``
#. Install coverage in the venv: ``./venv/bin/python coverage-*/setup.py install``
#. Set PYTHONPATH to ``fullcoverage`` (need to change your directory to the venv):
   ``export PYTHONPATH=../coverage-N.N/coverage/fullcoverage``
#. ``unset CPPFLAGS`` in order to avoid using system Python header files
#. Run coverage from the venv: ``./bin/python -m coverage run --pylib -m test``
#. Unset PYTHONPATH: ``unset PYTHONPATH``
#. Generate coverage report: ``./bin/python -m coverage html --directory=../coverage_report -i --include="../cpython/Lib/*" --title="CPython test coverage report"``

Do be aware that this step takes a few **hours**. If you find report generation
is the bottleneck you can try using PyPy3 or your installed Python 3 interpreter
to generate the report.

.. _setuptools: https://pypi.python.org/pypi/setuptools
.. _coverage: https://pypi.python.org/pypi/coverage


//Helpful files for sprint participants
=====================================

Helpful files are included in order to make things a little bit easier for
you, the sprint leader, as well as sprint participants and new contributors.


//``index.html``
--------------

An HTML file with links to:

- documentation which you built previously
- the helper scripts


//``build_cpython.py``
--------------------

On UNIX-based OSs this file builds the CPython repository. On all platforms it
verifies that the expected CPython binary exists.

While the devguide includes instructions on how to build under UNIX, this
script simplifies the process for sprint participants by having a single
command to configure and build CPython. It also uses reasonable defaults
(e.g. all cores on the CPU).
