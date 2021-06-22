---
title: Managing Settings in a Large Django Project
slug: managing-settings-in-a-large-django-project
date_published: 2021-01-08T00:00:00.000Z
date_updated: 2021-02-22T17:17:44.000Z
tags: Programming, Python, Django
excerpt: Exploring three ways to manage Django's configuration settings when the your project gets large and complex.
---

For as easy as Django makes building web applications, it does not make it easy to manage your settings. This it leaves entirely up to you. In the last year, I’ve worked on 10 large Django projects, each with their own unique requirements, and each with their own way of managing configuration settings and environment variables. In this article, I’ll cover some of the better ways I’ve seen to do this.

## The WordPress Approach

If you’re familiar with how most WordPress projects manage settings (in the codebase, not the dashboard), then this will look familiar with you. The average `wp-config.php` doesn’t get customized very much - typically just the database information. That makes managing the settings a little easier and what you’ll often see is just a big `if`/`elseif` block for the different environments.

We can implement this pattern in Django’s `settings.py` file too:

    ENV = os.environ.get("ENV", "DEVELOPMENT")
    
    if ENV == "PRODUCTION":
    	# Production settings
    elif ENV == "TESTING":
    	# Testing/Staging settings
    else:
    	# Development settings or defaults

This works if you don’t have too many settings with different values for different environments. For small applications or when you’re first getting started, this approach is great because it’s lightweight and it’s really easy to customize setting values. It starts to break down when you’re managing a lot of settings with different values across different environments. In my experience with Django, that tends to exclude larger projects.

## Environment Variable with Default

One of the simplest ways to manage settings is to leverage the fact that `os.environ.get` allows you to provide a default value if the environment variable you’re looking for isn’t available on the system. So, in production and staging, you can pull values from environment variable and in development, you can us the default.

That would looks something like this:

    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.postgresql',
            'NAME': os.environ.get("DB_NAME", "local_dev_db"),
            'USER': os.environ.get("DB_USER", "postgres"),
            'PASSWORD': os.environ.get("DB_PASSWORD", "postgres"),
            'HOST': os.environ.get("DB_HOST", "postgresdb"),
            'PORT': os.environ.get("DB_PORT", 5432)
        }
    }

This approach is really simple and clean and is the best option or most projects. It will work with as many environments as you need, so long as you set your environment variables appropriately.

If you have settings that you’re only using in a single environment, then you will still have to put those in a conditional. But now you only have to manage a couple of settings that way. If you find yourself mixing these approaches with a lot of settings, then you should consider using a settings module.

## Settings Module

For really big Django projects with a lot of settings and specifically with a lot of settings that don’t apply to every environment, the above approach can get really unwieldy. What ends up being a better approach is to create a settings module.

Getting started with a settings module is as simple as creating a `settings/` directory with an `__init__.py` file in it. How you managing your settings within a module will require some thought.

A simple variation of this approach is to use your `__init__.py` to import the settings that apply across all environments from a `base.py` file and then to import the environment specific settings from an `<environment>.py` file (like `production.py` or `development.py`). Your `__init__.py` file will look something like this:

    # __init__.py
    import * from base
    
    ENV = os.environ.get("DJANGO_ENV", "DEVELOPMENT")
    
    if ENV == "PRODUCTION":
    	import * from production
    elif ENV == "STAGING":
    	import * from staging
    else:
    	import * from development

If you’re refactoring to this approach, this is a good starting point. But it will quickly become unwieldy. You don’t want to manage the same settings across two or three different files.

The best implementation of the settings module that I’ve seen used this approach with a mix of the previous one and broke up configuration settings by topic, rather than environment. In that project, this meant having a `base.py`, `redis.py`, `postgres.py`, `celery.py`, as well as a few others.

## Parting Thoughts

While managing Django’s settings can be tricky, pne of the three approaches described above will be good for most projects. In addition to the three approaches described above, I’ve heard good things about [`django-split-settings`](https://github.com/sobolevn/django-split-settings) and [`django-environ`](https://django-environ.readthedocs.io/en/latest/), though I haven’t had the chance to use either yet. If you’ve got tips on managing settings, I’d love to hear them! The best way to reach me is on [Twitter](https://twitter.com/ZFleischmann).
