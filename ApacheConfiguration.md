# Introduction #

Use this in your VirtualHost section to configure MediaNav to run under mod\_python


# Details #
```

    <Location "/medianav">
        SetHandler python-program
        PythonHandler django.core.handlers.modpython
        PythonPath "['/opt/medianav',] + sys.path"
        SetEnv DJANGO_SETTINGS_MODULE settings
        PythonDebug Off
    </Location>

    Alias /medianav/media/ "/opt/medianav/media/"
    <Location "/medianav/media/">
        SetHandler None
    </Location>
    Alias /medianav/admin/media/ "/usr/lib/python2.5/site-packages/django/contrib/admin/media/"
    <Location "/medianav/admin/media/">
        SetHandler None
    </Location>

```