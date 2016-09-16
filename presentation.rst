.. role:: frag
   :class: fragment

.. role:: strike
   :class: kill

.. role:: hidden
   :class: hidden

.. role:: code-frag
   :class: code fragment

.. role:: code
   :class: code

Vagga
=====


Evo.company
===========

* 147 projects in gitlab
* 133 users in gitlab
* since november 2015


Vagga
=====

.. code-block:: console

    $ git clone git://github.com/.../foobar
    $ cd foobar
    $ vagga
    Available commands:
        build       Build static files
        run         Run nginx+app+redis
        build-docs  Build docs
    $ vagga build


Django
======

* :code-frag:`python manage.py runserver`
* :code-frag:`pip install req.txt`
* :code-frag:`python3 -m venv x; x/bin/activate`


Django
======

* :code:`python3 -m venv x; x/bin/activate`
* :code-frag:`apt-get install libxml2-dev`
* :code-frag:`apt-add-repository universe`


Dependencies
============

* :code-frag:`apt-get install postgres`
* :code-frag:`apt-get install mongodb`
* :code-frag:`apt-get install redis`
* :code-frag:`apt-get install memcached`


Containers to the Resque
========================


Vagga
=====

::

    vagga run

.. class:: fragment

    :frag:`vs`

    ::

        docker-compose up


Docker Compose
==============

::

    docker-compose up \
        --build --abort-on-container-exit


Vagga
=====

::

    git pull
    vagga run


:frag:`vs`

.. class:: fragment

    ::

        git pull
        docker-compose build --pull
        docker-compose up --abort-on-container-exit


:hidden:`Tree`
==============

::

   # docker tree
   -+= 00001 root systemd --system
    |-+- 10771 root docker -d
    | \--= 32029 root bash   << our process
    \-+= 30029 user tmux
      \-+= 10718 user -zsh     << our shell
        \--= 32021 user docker run -it --rm bash

::

   # vagga tree
   -+= 00001 root systemd --system
    \-+= 30029 user tmux
      \-+= 10358 user -zsh        << our shell
        \-+= 00940 user vagga bash
          \-+- 00941 user vagga bash
            \--= 00942 user bash  << our process


Docker Compose
==============

::

    docker-compose --force-recreate --remove-orphans


Tests
=====

.. class:: fragment

    ::

        vagga test


:frag:`vs`

.. class:: fragment

    ::

        docker-compose -p myproj_tests -f tests.yml \
            up --build --abort-on-container-exit


Vagga vs Compose
================

* pull vs build
* run, tests, doc, webpack...
* security model


CI System
=========

* container cache
* vagga test
* vagga deploy


Conventions
===========

.. code-block:: console

    $ vagga
    Available commands:
        run     Run the app with postgres and redis
        test    Run quick unit tests
        doc     Build docs with sphinx


Questions
=========
