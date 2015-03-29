Advanced Configuration
======================

The Landscape configuration file is actually the same as a Prospector profile, with one or two small additions.
This means that anything you can do with Prospector, you can do in Landscape, and vice versa. Prospector will
be able to use your ``.landscape.yml`` file to give you the same output on the command-line.

`Full documentation for Prospector profiles <http://prospector.readthedocs.org/en/master/profiles.html>`_ is
available on the Prospector documentation site, and so will not be duplicated here. Instead, here are several
examples of advanced configuration of Landscape.


Globally Disable Messages
-------------------------

The most common desire is to turn off messages for the entire project::

    pylint:
      disable:
        - eval-used

    pep8:
      disable:
        - E711
        - E712


Adding or Removing Tools
------------------------

It is possible to turn a tool off entirely::

    pylint:
      run: false

There are also some `optional additional tools <http://prospector.readthedocs.org/en/master/supported_tools.html>`_
which are not enabled by default as they can be less useful. You can enable them like so::

    pyroma:
      run: true


Existing Configuration
----------------------

If you already have configuration for static analysis tools, such as a ``.pylintrc`` file or
directives for ``pep8.py`` in a ``setup.cfg`` file, Landscape will pick this up automatically
and use them. You should see the same output from Landscape as when you run the tools on your
local codebase or CI server.

Note that Landscape will still run all tools, including ones that you do not have configuration
for. If you have configuration for ``pep8.py`` and ``pyflakes``, Landscape will use that *but also
run pylint with its defaults*.


Just run ``flake8``
-------------------

There is a special profile in Prospector which will configure it to mimic the behaviour of
``flake8``. This is not a particularly useful feature for Prospector itself (after all, why
not just use flake8 in the first place!) but if you want to get Landscape to just essentially
``flake8``, you can use a ``.landscape.yml`` file with the following single line::

    inherits: [flake8]

You can then of course add any additional behaviour.
