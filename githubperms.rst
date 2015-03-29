
GitHub Permissions
==================

Public Repositories Only
------------------------

Landscape tries to request as little access as possible for users of the free, open-source version.
No write access to code is required. The following GitHub permissions are requested:

``read:org``
    This allows Landscape to see all organisations you belong to, even if your membership to those organisations
    is not public. This is so that you can see repositories for that organisation which are being checked by
    Landscape.

``user:email``
    Landscape requests your email address in order to send you notifications about checks once they run, and
    whether code quality improved or not.

``admin:repo_hook``
    GitHub sends notifications to Landscape via HTTP hooks which inform Landscape when a new commit has
    been pushed. In order to create these automatically, Landscape requires admin (create and delete)
    permissions for hooks.

``repo:status``
    This allows Landscape to post updates to pull requests using GitHub's
    `status API <https://github.com/blog/1227-commit-status-api>`_. This includes
    permissions to update the status of private repositories, but does not allow
    access to private code. GitHub does not have a public-repository-status only
    permission at this time.


Private Repositories
--------------------

For users with private repositories, complete read and write access is requested. GitHub does not have nuanced
permissions for private repositories.

One problem is that you can only give Landscape access to *all* private repositories. If you belong to multiple
organisations, this can be difficult as perhaps not all will want to allow that.

In this case, you can ask the administrator of the organisations to enable
`approved applications <https://github.com/blog/1941-organization-approved-applications>`_ - this means that the
organisation administrator can create a whitelist of which applications are allowed to see their private
repositories. It is not enabled by default.