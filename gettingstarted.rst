Getting Started
===============

Landscape works by connecting to your GitHub account and inspecting the code on every code push and
pull request made.

To get started, you will first need to log in to Landscape using your GitHub account and allow Landscape
access to your repositories. You can read more about :doc:`the permissions Landscape requires <githubperms>` here.

You will then be taken to the 'add repository' page to tell Landscape which of your repositories to check.
The filter on the right will let you switch between organisations, private or public repositories, show or
hide forks and so on.

Once you've selected which repositories to add, click 'Add Repositories' at the bottom of the page and you're
done!

The default branch (as set in GitHub) will be checked automatically to provide a first score. This may take some
time as for initial checkout and installation of dependencies - it will be faster for future checks results are
cached.


Private Repositories
--------------------

Landscape is free for open source, but for private repositories you will need a subscription. You can try
out Landscape for 14 days using `a free trial <https://landscape.io/start>`_.

If your organisation already has a subscription and you want to be able to see those repositories, you will
need to grant Landscape permission to view your private repositories on GitHub - you can do that on
`your preferences page <https://landscape.io/preferences/github>`_.

You can read more :doc:`about private repositories here <private-repositories>`.


That's it? What next?
---------------------

That is indeed it! Landscape will do its best to guess some sensible defaults based on your
project.

These defaults will hopefully be enough, but if you want to tweak the behaviour to be more
strict, for example, or to enforce full pep8, you can do this with the :doc:`configuration file <configuration>`.

You may also find it helpful to read though more about :doc:`how to get the best out of Landscape <using-landscape>`.
