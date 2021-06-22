---
title: Using Pipenv with Django
slug: using-pipenv-with-django
date_published: 2019-03-28T00:00:00.000Z
date_updated: 2021-02-22T17:18:29.000Z
tags: Python, Django
excerpt: Managing dependencies in Python projects used to be a huge pain, but it's a lot easier now with Pipenv
---

Managing dependencies in Python projects can be a a really painful experience.

Getting your virtual environments set up and installing dependencies under the correct version of Python are just two of the challenges that a newcomer to the ecosystem might face. As I've been working with Python more, I've definitely forgotten to activate my virtual environment or run into versioning issues, like trying to run Django 2.x but only having Django 1.x available in my environment.

Additionally, different development communities within the Python ecosystem tend to have their own way of managing environments and dependencies. So when I was learning data science, I used Anaconda for my environments and it would often conflict with virtualenv. I once updated the `requirements.txt` file for a Django project and included everything that comes with a fresh Anaconda environment (pandas, numpy, etc) and didn't realize for a couple of commits.

For someone coming from Ruby (bundler), PHP (composer), or JavaScript (npm), the process seems messy and unnecessarily complex. It also feels frustratingly error-prone.

## Pipenv

[`Pipenv`](https://pipenv.readthedocs.io/en/latest/) is the solution - it works like other bundlers and dependency managers (so like you'd expect it to work) and it works really well. `Pipenv` uses a `Pipfile` and `Pipfile.lock` so you can manage your dependencies (including development dependencies) and have deterministic builds. It still manages your dependencies in a virtual environment, but it makes creating and activating virtual environments easy and straightforward.

## Getting Started

The first step is to install `Pipenv`, which you can do with homebrew:

    brew install pipenv

Now that it's installed, you can use it to install modules and setup a virtual environment for a project. Let's create a Django project and manage our dependencies for it with `pipenv`.

Make a directory called `hello_django/` somewhere on your computer:

    mkdir hello_django
    cd hello_django

Now install Django, like so:

    pipenv install django

Notice that we started by installing a dependency and not by creating a new environment?

What's really great about `pipenv` is that it will automatically set up a new environment for you! When we run the above command, `pipenv` will create a virtual environment called `hello_django-twf5jxgT` where `hello_django` is the name of our directory and `twf5jxgT` is a hash.

This virtual environment will be created inside a `.virtualenvs/` directory at the root of your user directory.

## Working with Pipenv

Now that we have Django installed and our virtual environment setup, we can create our Django project:

    pipenv run django-admin startproject hello_django .

This is the command for creating a new Django project. We add `.` at the end of the command so that the project is created in our current directory (instead of a subdirectory).

Now if we want to start up our new app, we can do so with the following command:

    pipenv run python manage.py runserver

The `pipenv run` part of the above two commands is required, unless we run `pipenv shell` to activate our virtual environment:

    pipenv shell # activate virtual environment
    python manage.py runserver

## Working with Dependencies

We can install another package by using `pipenv install`:

    pipenv install psycopg2-binary

When we run `pipenv install`, the `Pipfile` gets updated automatically, just like with npm, composer, et al:

    [[source]]
    name = "pypi"
    url = "https://pypi.org/simple"
    verify_ssl = true
    
    [dev-packages]
    
    [packages]
    django = "*"
    +psycopg2-binary = "*"
    
    [requires]
    python_version = "3.6"

## Pipenv Scripts

One of the things that's great about npm and the `package.json` file it uses is the ability to create custom scripts for commonly performed tasks. This automation is a great way of speeding up your development workflow.

You can also do this with `pipenv`! All scripts go under a `[scripts]` heading. Each script needs a name and a string for a command to run:

    [scripts]
    start = "python manage.py runserver"

In this example, our script is `start` and our command is `"python manage.py runserver"`, which is the command for starting our Django server.

To run the above `pipenv` script, we do the following:

    pipenv run start

Where `start` is the name of the command we want to run.

## Conclusion

This feels easier than using virtualenvs on a few fronts. I've just covered setting up an environment and installing dependencies. But the `Pipfile` that `pipenv` creates makes managing dependences (and other things, like Python versions) a lot easier than `requirements.txt`. For instance, to install a dependency just for your development environment, you run `pipenv install --dev`. Notice the same simplicity of working with Node dependencies?

For a next step, I highly recommend checking out the [documentation](https://pipenv.readthedocs.io/). There are pages on [a basic `pipenv` workflow to follow](https://pipenv.readthedocs.io/en/latest/basics/#example-pipenv-workflow) and how to [migrate from a `requirements.txt` file](https://pipenv.readthedocs.io/en/latest/basics/#importing-from-requirements-txt). There are also some cool, advanced features like [automatically loading a `.env` file](https://pipenv.readthedocs.io/en/latest/advanced/#automatic-loading-of-env) and setting up [shell completion](https://pipenv.readthedocs.io/en/latest/advanced/#shell-completion) for `pipenv`.
