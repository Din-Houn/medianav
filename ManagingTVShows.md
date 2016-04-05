# Introduction #

Managing TV Shows with MediaNav


# Details #

MediaNav assumes all your TV Shows are in the following format:

[path\_to\_tv\_shows](path_to_tv_shows.md)/[Name](Show.md)/s##e## filename.avi

If you have a single file covering more than one episode number then the format is something like this:

s01e01-02 Pilot.avi

(Some paths are currently hardcoded, this will be fixed up, everywhere you see /data/tv, replace this with where your TV shows are.

Configure the TV Show pattern, in the django admin interface

TV - Video File Patterns, add a new entry:

re:
```
^(?:(?P<name>.*?)[\/\s._-]+)?(?:s|se|season|series)[\s._-]?(?P<season>\d{1,2})[x\/\s._-]*(?:e|ep|episode|[\/\s._-]+)[\s._-]?(?P<episode>\d{1,2})(?:-?(?:(?:e|ep)[\s._]*)?(?P<endep>\d{1,2}))?(?:[\s._]?(?:p|part)[\s._]?(?P<part>\d+))?(?P<subep>[a-z])?(?:[\/\s._-]*(?P<epname>[^\/]+?))?$
```
priority: 100
description: TV Show Support - SssEee or Season\_ss\_Episode\_ss - from Video::Filename Behan Webster

(Credit to Behan Webster for this regex from his perl Video::Filename library)

Next, add some tv shows to your database

Shows are added by their thetvdb.com ID

To find an ID for a TV show, use the following command:

python manage.py tv\_getshowname "TV Show Name"

It will return a list of show names matching and the tvdb id

Then run the following command replacing id with the id:

python manage.py tv\_importshow id

That will populate the database with the show details, including episodes.

Do this for all your TV shows.

Next, run the following command:

python manage.py tv\_scanall

That will scan through all your video files and try to link them to episodes, complaining when it can't find a match.

If your directory name does not match the name of the show on TheTVDB, you also need to add an alternative name for the show, in the admin interface

Add a new entry via the admin interface, TV, Alternate Show Names.

To keep your TV