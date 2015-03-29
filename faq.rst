Frequently Asked Questions
==========================


About Landscape
---------------

What is Landscape?
    Landscape is a code quality inspector for Python codebases.
    It inspects your code to find errors, possible problems, security issues.


How does it work?
    Every time you push code to your repository, Landscape will check it out and
    run various Python code quality tools, such as pylint, over it. It accumulates
    and filters the output of all of these tools in order to give you a high-level
    overview of the state of your code base.


How much does it cost?
    Landscape is free for open-source repositories - that is, for publicly
    available GitHub repositories. There are paid plans for private
    repositories and for organisations - see our `pricing page <https://landscape.io/plans>`_.


I found a bug - how should I report it?
    Please report bugs on the `issue tracker <https://github.com/landscapeio/landscape-issues/issues>`_,
    including a screenshot of the bug if possible. Thanks!



Features
--------

Do you support BitBucket?
    Not yet, but it is on the roadmap. If you have a burning desire for BitBucket
    support, `send me a messages <mailto:carl@landscape.io>`_ or
    `add a ticket <https://github.com/landscapeio/landscape-issues/issues>`_.


What if I host my code myself?
    Landscape is currently only built to deal with GitHub, however a future
    feature will be the ability to attach to any git repository via SSH or HTTPS,
    at which point you will be able to use your own code host.


Do you support private repositories?
    Yes, we support private GitHub repositories. This requires a paid subscription - you can
    `see the pricing and features <https://landscape.io/plans>`_, and each plan comes with
    a 14-day free trial so you can try it first.


Troubleshooting
---------------

Does Landscape work with Python3?
    Unfortunately not yet. This is a heavily requested feature however and so development
    is underway!

My repository doesn't show up!
    If your repository is not in the list on the 'add a repository' page, this could be for
    two reasons. First, if you only recently added it to GitHub, Landscape may not have
    synced your account yet. You can do that on the right-hand-side of your dashboard. The
    other possibility is that GitHub has classified the language of your repository as something
    other than Python. You can show these additional repositories using the filter on the
    left side of the 'add repository' page and select "Language: Everything".


Prospector
----------

What is Prospector?
    Prospector is the tool underlying the code inspection of Landscape. You can
    read more on :doc:`the prospector page <prospector>`.