# Introduction #

STILL IN PROGRESS

Steps to install MediaNav server on Ubuntu 10.04

First add the repository for mediainfo:

```
sudo add-apt-repository ppa:shiki/mediainfo
sudo apt-get update
```

Install the packages:

```
sudo apt-get install mysql-server
sudo apt-get install python-django # Needs at least v1.1
sudo apt-get install python-mysqldb python-imaging
sudo apt-get install mediainfo # This is in the launchpad PPA repository https://launchpad.net/~shiki/+archive/mediainfo
```

Install the latest IMBbPy from source. The one shipped with Ubuntu (4.5) and the latest packaged version (4.6) does not work due to changes on IMDB's site.

```
sudo apt-get install mercurial
sudo apt-get install python-setuptools python-sqlalchemy python-lxml
sudo apt-get install python-dev
hg clone http://imdbpy.hg.sourceforge.net:8000/hgroot/imdbpy/project/
cd project
sudo python setup.py install
```

To update your version of imdbpy after initial installation:

```
cd project
hg pull -u
sudo python setup.py install
```

# Details #

  * Configure your database, example below for MySQL (database must be UTF8):
  * from the mysql shell:
```
CREATE DATABASE medianav CHARACTER SET utf8 COLLATE utf8_general_ci;
```
  * Create a user and give access rights
```
mysqladmin grant all privileges on medianav.* to '<username>'@'localhost' identified by '<password>';
```
  * copy settings.py.example to settings.py
  * Edit settings.py
  * Change DATABASE settings to match the above:
```
DATABASE_ENGINE = 'mysql'
DATABASE_NAME = 'medianav'
DATABASE_USER = '<username>'
DATABASE_PASSWORD = '<password>'
```

  * Edit
```
MEDIA_ROOT = '/opt/medianav/media/';
MEDIANAV_TV_MEDIA = '/opt/medianav/media/img/tv';
MEDIANAV_MOVIES_MEDIA = '/opt/medianav/media/img/movies';
```

  * After editing the settings.py file, run the following commands to create the tables and initial admin user:

```
python manage.py syncdb
python manage.py migrate

```

  * You can now test if the webserver works
  * In another window, run python manage.py runserver 0.0.0.0:8000 (assuming you have port 8000 free)
  * Then open a browser to http://yourmachine:8000/medianav/ And see if it opens a page

# Configuration #

  * In the admin interface (http://yourmachine:8000/medianav/admin, it will ask you to login with the credentials you just created), go to the Sites heading. Replace the example.com entry with one appropriate for your setup, this would be the yourmachine:8000

# Importing your movies #

  * Scan movie directories and associate imdb id's
```
python manage.py movie_scan_dir all
python manage.py movie_imdb_assoc all
```

  * Finally, import movie details (plot, year, actors, genre, etc) posters and backdrops:

```
python manage.py movie_import_imdb all
python manage.py movie_import_tmdb all
```