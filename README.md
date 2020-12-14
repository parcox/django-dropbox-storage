
# django-dropbox-storage

> A Dropbox Storage for your Django apps

## Disclaimer 
This is a relatively old project that I edited according to my needs (e.g. File path issue on Windows, see [this issue](https://github.com/zuck/django-dropbox-storage/issues/1) for details). 

This project was previously worked on by:

* **Andres Torres** [django-dropbox](https://github.com/andres-torres-marroquin/django-dropbox)
* **Emanuele Bertoldi** [django-dropbox-storage](https://github.com/zuck/django-dropbox-storage)


## What

`django-dropbox-storage` allows Django apps to use Dropbox as a storage backend for file uploading.

## Installing

Create a virtual environment and activate:
```
$ python -m venv myenv
$ cd myenv/Scripts
$ activate
```

Install the package:
```
$ pip install git+https://github.com/zahidtokur/django-dropbox-storage.git
```

Then open the `settings.py` of your project and include it to your `INSTALLED_APPS`:

```
INSTALLED_APPS = (
    ...
    'django_dropbox_storage',
    ...
)
```

If you want to use `django_dropbox_storage` as default storage for all file uploads, you need to adjust `DEFAULT_FILE_STORAGE` too:

```
DEFAULT_FILE_STORAGE = 'django_dropbox_storage.storage.DropboxStorage'
```

If you just want to use it on a single model field, you can simply import it:

```
from django_dropbox_storage.storage import DropboxStorage

DROPBOX_STORAGE = DropboxStorage()

photo = models.ImageField(upload_to='photos', storage=DROPBOX_STORAGE ...)
```

In order for the package to work properly, you must set the next settings:

```
DROPBOX_ACCESS_TOKEN = 'xxx'
```

If you don't have `DROPBOX_ACCESS_TOKEN` you can create one after creating a Dropbox app at [Dropbox for Developers](https://www.dropbox.com/developers).
If you have your Dropbox `App key` and `App secret`, you can set `DROPBOX_CONSUMER_KEY` and `DROPBOX_CONSUMER_SECRET` settings in `settings.py`, then run:

```
$ python manage.py get_dropbox_token
```

And follow up on screen instructions, finally set the `DROPBOX_ACCESS_TOKEN` in your `settings.py` module.

You can also set default root folder setting the value of `DROPBOX_ROOT_FOLDER`:

```
DROPBOX_ROOT_FOLDER = '/Public'
```

By default it's set to `'/'` (root folder).

For example usage, refer to [zahidtokur/django-dropbox-example](https://github.com/zahidtokur/django-dropbox-example)
