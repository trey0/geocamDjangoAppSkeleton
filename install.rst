
Here are some guidelines for how to structure Django apps to fit the
GeoCam conventions.

We chose to base our design off the `django-app-skeleton`_ app generator.

.. _django-app-skeleton: http://opensource.washingtontimes.com/blog/2010/nov/28/app-centric-django-development-part-2-app-factory/

App directory/repo layout
~~~~~~~~~~~~~~~~~~~~~~~~~

 * ``geocamAwesome/``

   * ``README.rst`` -- what is this app? what does it do? in wiki-like reStructuredText_ format

   * ``setup.py`` -- ``setuptools``, probably with some custom commands to do cool stuff.

   * ``geocamAwesome/``

     * Django code (models, views, etc)

     * ``templates``, ``templatetags``

     * ``media/geocamAwesome``

       * ``images``, ``css``, ``javascript`` [should we split this up into further subdirs?]

     * ``tests``

   * ``bin/`` -- other things which don't belong with the web code, but need to be run or interact with the app.  Also, misc utilities.

   * ``doc_src/`` -- rst files for documentation about the app (For automatic, sexy, html documentation generation. Yes. Sexy.)

   * ``LICENSE`` - the NOSA 1.3 license

   * ``MANIFEST.in`` -- setuptools file. ignore.

.. _restructuredText: http://docutils.sourceforge.net/rst.html

Skeleton generation
~~~~~~~~~~~~~~~~~~~

Now that you know what one looks like, know that you don't have to make it yourself!  An app generator has been created to make the magic happen. Let's take the fictional app of ``geocamAwesome``.  You can create this bag of awesome-sauce in 5 easy steps:

1. Create the ``geocamAwesomeWeb`` repository.  On GitHub, you do this by clicking on ``Dashboard``, then ``New Repository``.

2. Clone your master repo locally::

    git clone git@github.com:$GITHUBUSER/geocamAwesomeWeb.git

3. Clone the `GeoCam Django app generator`_ from GitHub.  (It doesn't matter where you put it, you will only need the generator to create your app, then you can get rid of it.)::

    git clone https://github.com/geocam/geocamDjangoAppSkeleton.git

4. cd to the *parent* directory of your ``geocamAwesomeWeb`` checkout and fill in your blank repo by running::

    geocamDjangoAppSkeleton/create_app.py

  At the prompts, you want the app name to be ``geocamAwesomeWeb`` and the package name to be ``geocamAwesome``.  The author should be ``GeoCam Project``.

5. Profit!

Don't forget to commit the newly created little files of joy to the geocamAwesome git repo!

.. _GeoCam Django app generator: https://github.com/geocam/geocamDjangoAppSkeleton

Sites
~~~~~

Overall, we are dealing with a server that will be comprised of a bunch of Django applications.  These apps need to be put into one cohesive Django site that makes sense for the responders we are supporting. Structuring the Django apps in a consistent manner makes it easier to create the site in a standard way, but we still need to define the glue code.

Site Directory Layout
~~~~~~~~~~~~~~~~~~~~~

 * ``geocamSite/``

   * ``siteSettings.py`` -- default site settings, may override app-default settings

   * ``settings.py`` -- this checkout's local, overridden settings. (db setup, etc)

   * ``geocamApp1`` --(symlink)--> submodules/geocamApp1/geocamApp1

   * ``geocamApp2`` --(symlink)--> submodules/geocamApp2/geocamApp2

   * ``submodules/``

     * ``geocamApp1/`` -- submodule repo

     * ``geocamApp2`` -- submodule repo

   * ``README.rst`` -- what is this repo?  in wiki-like reStructuredText_ format

   * ``setup.py`` -- ``setuptools`` Python file (will probably setup the symlinks, etc)

Site skeleton generation
~~~~~~~~~~~~~~~~~~~~~~~~

There is to skeleton generation for sites yet, sorry!

| __BEGIN_LICENSE__
| Copyright (C) 2008-2010 United States Government as represented by
| the Administrator of the National Aeronautics and Space Administration.
| All Rights Reserved.
| __END_LICENSE__
