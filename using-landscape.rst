Getting the Most out of Landscape
=================================

Aim for Incremental Changes
---------------------------

Although your code is given a score as a percentage, that does not mean that aiming for 100% is useful
or necessary. The numeric value is given to show changes up or down, rather than to provide an absolute
value.

Many large codebases will have a lot of warnings issued by Landscape, and in addition, some of those warnings
will not be accurate. Therefore it makes more sense to think in terms of incremental changes - if you commit
code, is the overall code quality going up or down? When you create a new feature, have you added lots of
new errors?

This approach helps you start by staying on top of any technical debt you have. If your codebase gets a score
of 50%, that does not mean it's time to spend a month focusing only on fixing warnings. It just means that you
should pay a little extra attention so that every week your score improves and so your overall code quality
improves.


Use Feature Branches
--------------------

`Feature branches are a great development method <http://blog.landscape.io/use-feature-branches-for-everything.html>`_
for separating out features and bug fixes into smaller manageable chunks. It also means that, using GitHub's
Pull Requests, Landscape can check and individually comment on a particular feature.

For example, if you create a new feature in a feature branch, then create a pull request, Landscape will comment on
it to inform you of changes to the number of errors and warnings introduced by the PR. This is not only helpful to
see if you have added any new problems, but in general for the whole project as it breaks down the process of
fixing and improving code quality into smaller manageable chunks.

You can configure this for an entire organisation via `your preferences page <https://landscape.io/preferences>`_
and also override these settings per-repository on the repository settings page (small cog icon at the top-right
of a repository page).


If Using Django
---------------

Landscape has several Django-specific behaviours which will be turned on if it detects that you are using
Django. This will prevent generating warnings such as 'MyModel has no member called objects' and similar, which
are caused by the metaprogramming Django does.

This behaviour will be turned on by default but it is possible that Landscape does not figure out that you
are using Django. Dependencies are determined by parsing ``setup.py`` or ``requirements.txt``, but if they
cannot parsed, they are in a non-standard location, or if you don't specify dependencies in your project, then
you will have to manually tell Landscape to use Django plugins.

To do this, you will need a :doc:`.landscape.yaml configuration file <configuration>`, and include the following::

    uses:
        - django

If Using Flask
--------------

Similarly, Landscape has Flask-specific behaviours thanks to the awesome
`pylint-flask plugin <https://github.com/jschaf/pylint-flask>`_.


What Next?
----------

* :doc:`Learn all the options for configuring Landscape <configuration>`
