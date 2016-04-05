# Overview #

Medianav consists of three parts:

  * A fileserver containing the actual media files (TV shows, Movies, etc)
  * An application server running Django to manage your media collection and provide web services
  * A python front-end that can play the media built on top of mplayer and uses web services to get meta information from the app server

All three components can run on separate servers or be combined. Multiple front-ends can also be used.

# Status #

The source code is available, but no pre-packaged version is available yet. The database structure and interfaces are still changing too much. Once everything is stable a 1.0 version will be released.

  * 2009-10-17 : Basic support added to allow PopcornHour media player to be used as a front-end
  * 2009-10-08 : Been a while since the last update, but marking TV episodes as watched and switching between user favorite profiles is working now
  * 2009-09-09 : Various updates to backend related to movies, searching, media info, directory renaming, etc
  * 2009-08-31 : Added movie support to python front-end
  * 2009-08-20 : Added movie management app and integration to TheMovieDB
  * 2009-08-12 : Basic Django server for TV Management and PyGame client checked into SVN

Read the DesignNotes for more information.

# Screenshots #

Everyone always loves screenshots. Here are some of the Web interface of svn [r95](https://code.google.com/p/medianav/source/detail?r=95)

## MediaNav Web Interface ##

![http://medianav.googlecode.com/files/screenshot_medianav_r95_tv_shows_list.png](http://medianav.googlecode.com/files/screenshot_medianav_r95_tv_shows_list.png)

![http://medianav.googlecode.com/files/screenshot_medianav_r95_tv_shows_detail.png](http://medianav.googlecode.com/files/screenshot_medianav_r95_tv_shows_detail.png)

![http://medianav.googlecode.com/files/screenshot_medianav_r95_movie_search.png](http://medianav.googlecode.com/files/screenshot_medianav_r95_movie_search.png)

![http://medianav.googlecode.com/files/screenshot_medianav_r95_movie_detail.png](http://medianav.googlecode.com/files/screenshot_medianav_r95_movie_detail.png)

## MediaNav Popcorn Hour Interface ##

![http://medianav.googlecode.com/files/screenshot%20medianav%20r95%20popcornhour%20movielist.jpg](http://medianav.googlecode.com/files/screenshot%20medianav%20r95%20popcornhour%20movielist.jpg)
