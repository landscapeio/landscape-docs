The Configuration File
======================


Landscape aims to have sensible defaults which will be appropriate for most code
bases. In the perfect world, Landscape will just work for you out of the box. In
the real world, of course, that may not be true, so there are several configuration
options available to you. To configure Landscape and to change the default behaviour,
create a ``.landscape.yml`` file in the root of your repository.

There are several basic options which control behaviour at a high level, but if you
really want to dive into the nitty gritty and configure everything on a very fine-grained
level, see :doc:`the advanced usage section <advanced>`.


An Example File
```````````````

Here is a simple example of what a configuration file might look like::


    doc-warnings: true
    test-warnings: false
    strictness: veryhigh
    max-line-length: 120
    uses:
      - django
      - celery
      - flask
    autodetect: true
    requirements:
      - deps/core.txt
      - deps/test.txt
    ignore-paths:
      - docs
      - mypackage/vendor
    ignore-patterns:
      - ^example/doc_.*\.py$
      - (^|/)docs(/|$)
    python-targets:
      - 2
      - 3



Basic Options
`````````````

``strictness <veryhigh, high, medium, low, verylow>``
-----------------------------------------------------

`Prospector <https://github.com/landscapeio/prospector>`_, the tool which
does the code analysis, can be configured to be more or less strict. The default setting
used by Landscape is 'medium' but you can adjust this up or down if you want harsher
or more relaxed checking.

``python-targets <2, 3>``
-------------------------
This is a list of which major python versions your project supports.

If you specify both 2 and 3, then Landscape will run primarily in Python 3 mode.

If this is not specified, Landscape looks for a ``setup.py`` file in the root
of the repository, and if found, searches for
`trove classifiers <http://python-packaging-user-guide.readthedocs.org/en/latest/distributing/#classifiers>`_
indicating which versions of Python the package supports.

If neither ``python-targets`` nor a ``setup.py`` is found, then Python2 is assumed.

``pep8``
--------

The default behaviour does not enforce full PEP8, but rather a subset based on the
strictness settings. To enable full PEP8, you can add a ``pep8`` section to the config
file like so::

    pep8:
      full: true

To completely ignore all pep8 warnings::

    pep8:
      none: true



``doc-warnings <bool>``
-----------------------

This setting controls whether or not Landscape should include warnings about missing
documentation and the format of documentation strings. This is false by default. If
enabled, `PEP257 <https://www.python.org/dev/peps/pep-0257/>`_ will be enforced. The
value can be ``true`` or ``false``.


``test-warnings <bool>``
------------------------

This setting controls whether or not Landscape should include warnings about tests.
The default is to ignore unit tests and anything in a package named 'tests'. The
value can be ``true`` or ``false``.


``max-line-length <int>``
-------------------------

The maximum line length to allow. A warning will be generated for any lines which have more
characters than this value. If not specified, a default will be used depending on strictness
(80 for very high, 100 for high, 160 for medium and below). This setting allows you to
have a specific value of your own choosing.


``requirements <list>``
-----------------------


Landscape will install your project requirements along with your code, as this improves
inference and figuring out if the usage of libraries is correct. It will try to automatically
find requirements in ``requirements.txt`` or ``setup.py`` and similar (see
the `requirements detector <https://github.com/landscapeio/requirements-detector>`_
project for exact details on how this works).

If your requirements are not found, you can specify the paths to files in a list. This file
must be in standard pip 'requirements.txt' format.


``uses <list>``
---------------

`Prospector <https://github.com/landscapeio/prospector>`_ has various plugins which
enable it to better understand code which uses certain other libraries. For example, there is
a Django plugin which prevents warnings which are incorrectly raised about missing 'objects'
member on Django models and so on.

Landscape tries to automatically detect project dependencies by scanning ``setup.py``
and ``requirements.txt`` files, so if you have a standard way of declaring dependencies,
you should not need to add any additional information. The ``uses`` setting is to tell
Landscape explicitly what plugins to load if autodetection does not work.

The currently supported frameworks are ``celery``, ``django`` and ``flask``.


``autodetect: <bool>``
----------------------

The default behaviour is to autodetect dependencies in order to augment the code analysis. This
setting can be used to turn off autodetection completely. The default value is ``true``, unless
``requirements`` has been defined. The value can be 'true' or 'false'.


``ignore-paths`` and ``ignore-patterns <list>``
-----------------------------------------------

Landscape will do its best to figure out which files and directories to ignore - for example,
directories beginning with a ``.``, test directories and so on. However, this will
probably not suit every project, so you are able to define additional directories to ignore.

``ignore-paths`` is a list of paths to ignore *relative to the repository root*.
It can be a directory, in which case the directory contents and all subdirectories are ignored,
or it can be a specific file. For example, ``docs`` would ignore a directory in the
repository root called "docs", while ``mypackage/vendor`` would ignore anything in the
directory at "mypackage/vendor". Note that glob syntax (for example ``docs/ex*``) is not currently
supported.

``ignore-patterns`` is a list of regular expressions. The relative path of files and
directories is *searched* for each regular expression, and ignored if any matches are found.
If the expression matches a directory, the directory contents and all subdirectories are ignored.
For example, ``^example/doc_.*\.py$`` would ignore any files in the "example" directory
beginning with "doc\_". Another example: ``(^|/)docs(/|$)`` would ignore all directories
called "docs" in the entire repository.

Note that in both cases, directories are separated using a forward slash ``/`` (i.e. the
POSIX path separator).
