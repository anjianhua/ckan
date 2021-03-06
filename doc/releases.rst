=============
CKAN Releases
=============

CKAN follows a predictable release cycle so that users can depend on stable
releases of CKAN, and can plan their upgrades to new releases.
The :ref:`changelog` documents the main changes in each release.

Each release has a version number of the form ``M.m`` (eg. 2.1) or ``M.m.p``
(eg. 1.8.2), where ``M`` is the **major version**, ``m`` is the **minor
version** and ``p`` is the **patch version** number. There are three types of
release:

Major Releases
 Major releases, such as CKAN 1.0 and CKAN 2.0, increment the major version
 number.  These releases contain major changes in the CKAN code base, with
 significant refactorings and breaking changes, for instance in the API or the
 templates.  These releases are very infrequent.

Minor Releases
 Minor releases, such as CKAN 1.8 and CKAN 2.1, increment the minor version
 number. These releases are not as disruptive as major releases, but
 backwards-incompatible changes *may* be introduced in minor releases. The
 :ref:`changelog` will document any breaking changes. We aim to release a minor
 version of CKAN roughly every three months.

Patch Releases
  Patch releases, such as CKAN 1.8.1 or CKAN 2.0.1, increment the patch version
  number. These releases do not break backwards-compatibility, they include
  only bug fixes and non-breaking optimizations and features.
  Patch releases do not contain:

  - Database schema changes or migrations
  - Function interface changes
  - Plugin interface changes
  - New dependencies
  - Big refactorings or new features in critical parts of the code


---------------
Release Process
---------------

.. _beta.ckan.org: http://beta.ckan.org
.. _Transifex: https://www.transifex.com/projects/p/ckan

When the development is ready to start the process of releasing a new version
of CKAN, we will:

#. Create a new release branch from the master branch, named ``release-v*``
   where ``*`` is the release's version number.

#. Deploy the release branch on `beta.ckan.org`_ for testing.

#. During the next two-three weeks, we'll allow changes on the release branch
   only to stabilize the code, update translations and documentation, etc.
   (new features are usually not added on the release branch).

#. During the final week before the release, we'll only allow critical bug
   fixes to be committed on the release branch.

At some point during the beta period a **strings freeze** will begin.
That means that no changes to translatable strings are allowed on the release
branch (no new strings, or changes to existing strings). This will give
translators time to update the translations on Transifex_. We'll publish a
**call for translations** to the ``ckan-dev`` and ``ckan-discuss`` mailing
lists, announcing that the new version is ready to be translated.

At some point before the final release, we'll announce an **end of
translations** after which no new translations will be pulled into the release
branch. At this point we'll deploy the translations to `beta.ckan.org`_ and
we'll put out a request for people to test CKAN in their languages.

Release branches are not merged back into master. All changes on a release
branch are cherry-picked from master (or merged from special branches based on
the release branch).

To ensure that the release guidelines are enforced one of the CKAN core
developers will act as **Release Manager**. They have the final say on what is
merged into the release branches.

Detailed release process instructions for CKAN Developers can be found in the
:doc:`release-process` document:

.. toctree::
   :maxdepth: 1

   release-process

.. include:: ../CHANGELOG.rst
