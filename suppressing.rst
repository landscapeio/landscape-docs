Turning Off Errors
==================

Landscape strives to be as useful and accurate as possible, and the underlying open-source tools
are all excellent. However, Python is a dynamic language and so static analysis is rarely completely
correct every time. This is why the best way to use Landscape is to concentrate on improvements rather 
than the absolute scores. However, it is often desirable to suppress an inaccurate error message.

Also, you may decide that some errors or warnings that Landscape finds are not interesting or relevant
to your project. 


Ignoring Errors of a Certain Type in the Whole Project
------------------------------------------------------

If you want to stop Landscape warning about a particular error, you can turn it off using a Landscape
configuration file.

For example, pylint will warn if you override a builtin function such as 'file'. If you don't care about
redefining builtins, you can tell Landscape to never warn like so::

    pylint:
      disable:
        - redefined-builtin

This requires knowing which tool created the message and the code of the message. You can find this out
by hovering over the message and looking at the popup:

.. image:: static/supressing/find-error-code.png
   :alt: How to find an error code
   :align: center

Here, the tool is `pylint` and the code is `redefined-builtin`. For more information, see the
:doc:`Landscape configuration reference <configuration>`.


Ignoring an Entire File or Directory
------------------------------------

Some files - for example, automatically generated code - are just not worth checking. In order to 
avoid checking them, you can use a Landscape configuration file. This is a YAML
file in your repository root and has two directives for ignoring files or directories::

    ignore-paths:
      - generated/
      - examples/broken.py
    ignore-patterns:
      - (^|/).*_test\.py(/|$)

These two directives allow you to ignore files by partial path match and by regular expression
respectively. 

For more information see the :doc:`Landscape configuration reference <configuration>`.


Ignoring a Single Error on a Line
---------------------------------

Landscape does not have a custom way to ignore errors but instead uses the mechanisms provided by the
static analysis tools used under the hood. This is so that you can still run these tools on your codebase
without needing to duplicate the ignoring directives. The idea is that running a tool on your codebase
should produce the same results as what you see in Landscape.

To completely ignore all errors on a line:

.. code-block:: python

    for file in get_files():  # noqa

The `noqa` style is used by most tools except pylint. Pylint has more nuanced directives, allowing you to
only suppress certain errors for a line but allow others to be raised. Note that Landscape manipulates the
tool output so that `noqa` will also suppress pylint errors.

If you want to only suppress that single pylint error but allow other errors through:

.. code-block:: python

    for file in get_files():  # pylint:disable=redefined-builtin

For pylint, the code can be a comma separated list of codes to ignore more than one error.

