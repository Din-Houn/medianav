# Introduction #

A few design notes, mostly to myself.

# Overview #

Medianav consists of three parts:

  * A fileserver containing the actual media files (TV shows, Movies, etc)
  * An application server running Django to manage your media collection and provide web services
  * A python front-end that can play the media built on top of mplayer and uses web services to get meta information from the app server

All three components can run on separate servers or be combined. Multiple front-ends can also be used.


# Assumptions #

  * Media must be mounted locally on both app server and playback client. Should not matter which method is used, could be NFS mounted in linux or drive mappings in Windows.
  * Front end can run mplayer, Python and PyGame

# Program List #

Some other programs and packages to make it all work

## Common ##

  * [Python 2.5.4](http://www.python.org/download/releases/2.5.4/) - Python 2.5 was chosen because not many Linux distributions currently ship with anything higher. Python 2.6 should work, but no Python 2.6 specific functionality will used

## Server Side ##

  * [Django 1.1](http://www.djangoproject.com/download/) Web application server. The latest official version as of now. Any 1.x release should work because Django's API has been made [stable up until 2.0](http://code.djangoproject.com/wiki/BackwardsIncompatibleChanges) Previously 1.0.1 was required, but this has been changed to 1.1 as the annotate functions have been used.
  * ~~[South 0.5](http://south.aeracode.org/) Django schema migrations. I miss schema migrations from Rails, so lets give this a try~~ No longer used
  * ~~[django-rest-interface](http://code.google.com/p/django-rest-interface/) A Django REST interface to models. To provide web services (JSON) to the clients.~~ No longer used
  * [python-api-for-thetvdbcom](http://loopj.com/2009/05/06/python-api-for-thetvdbcom/) To get TV show information from thetvdb.com
  * [Video::Filename 0.35](http://search.cpan.org/~behanw/Video-Filename-0.35/lib/Video/Filename.pm) Perl module to parse filenames for information about the video. Could re-use some of the components and rewrite them in Python

## Client Side ##

  * ~~[cocos2d 0.3.0](http://cocos2d.org/) A 2D graphics framework for Python for the user interface, it is built on top of Pyglet~~ Using PyGame instead
  * ~~[Pyglet 1.1.3](http://pyglet.org/) a cross-platform windowing and multimedia library for Python. Cocos2D is built on top of Pyglet~~
  * [pygame 1.8.1](http://www.pygame.org/download.shtml) Another graphics library for Python.
  * [pyLirc](http://pylirc.mccabe.nu/) pyLirc is a module for Python that interacts with lirc to give Python programs the ability to receive commands from remote controls
  * [mplayer](http://www.mplayerhq.hu/design7/news.html) A cross platform media player that has native support for lirc and pretty much any video format.
  * ~~[python-rest-client 0.2](http://code.google.com/p/python-rest-client/) A python REST client that provides the HTTP layer to get the model objects from the app server~~ No longer used
  * [simplejson](http://code.google.com/p/simplejson/) A Python 2.4 and 2.5 compatible JSON parser
  * ~~[PyMT Loader Module](http://pymt.txzone.net/docs/api/api-pymt.loader.html) Part of the Python Multi touch UI toolkit, provides an asynchronous loader for images and sprites.~~

# References #

A question I asked on Stack Overflow regarding the architecture to get access to the models in Django from the client: http://stackoverflow.com/questions/1037376/remote-access-to-django-orm