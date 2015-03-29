Prospector
==========

Prospector is the tool underlying the code inspection of Landscape. It is "command line Landscape" in a way
but also is built as an independent tool. One of the key aims is that you could use it as part of your own
CI servers or process and take any configuration work you have done with Landscape with you.

It pulls together the output of various static analysis tools as well as provides sensible defaults and
generally tries to make static analysis of Python code easier by prioritising important warnings over smaller
'picky' ones and including various lesser known tools.

The Landscape configuration file is actually almost identical to a Prospector "profile". These profiles give you
very fine-grained control over what tools run and what errors they omit, and are designed to be composable so you
can have a company-wide default and project-specific overrides. The
`prospector documentation site <prospector.readthedocs.org>` has more information.


Is Prospector open source?
--------------------------

Yes! Prospector is available under the GPLv2 license and is
`hosted on GitHub <https://github.com/landscapeio/prospector>`_.

Contributions are welcome!
