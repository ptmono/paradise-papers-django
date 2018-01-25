==============================================
How to query the Neo4j database with Neomodel.
==============================================

Intro.
======

I assume that you know how to create a django project and how to init and setup a django app inside this project.
If you don’t have a clue of what I said, I recommend to come back after reading the django intro tutorial and start
again from part one of this tutorial: https://docs.djangoproject.com/en/1.11/intro/

At this point of the tutorial you should have already created and setup the paradise_paper_search django project and
the fetch_api django app(:doc:`Part 1 <part01>`). Also you learned how to integrate the Neomodel OGM into the django project(:doc:`Part 2 <part02>`).
And at :doc:`Part 3 <part03>` you learned the way a Neo4j Graph Database is modeled using Neomodel and ended with a serie of python
classes definitions that represent the nodes, properties and relationships of the Paradise Paper Graph Database(PPGDB).

Current project structure::

    paradise_papers_search/
    ├── paradise_papers_search/
    │   └── +
    ├── fetch_api/
    │   ├── __init__.py
    │   ├── admin.py
    │   ├── apps.py
    │   ├── migrations/
    │   │   └── __init__.py
    │   ├── models/
    │   │   ├── __init__.py
    │   │   ├── Address.py
    │   │   ├── Entity.py
    │   │   ├── Intermediary.py
    │   │   ├── Officer.py
    │   │   └── Other.py
    │   ├── tests.py
    │   ├── urls.py
    │   └── views.py
    └── manage.py

Now, how you actually query a graph database inside your django project or apps?

Using the your model definitions
===================================

Using your model definitions is pretty standard. You usually just import the ones you need and use them.
For example in your django views. Before we get to that we need to learn the Neomodel Query API,
this API will allow us to express queries to the database without having to write them in plain Cypher.

We will learn to query using the Paradise Paper model definitions we did before. To do that we will first use an instance of the
python interpreter.

The project python interpreter:
---------------------------------------

Let's open the python interpreter through our django project ``manage.py`` which will
import our project settings(remember you set the DATABASE_URL in there, this is needed to connect to the db).
Also it will try to use ipython or bpython if available.

First let’s start opening the console, if necessary.

Then make sure you are at the ``paradise_papers_search`` root directory
where you created the django project(where you ``manage.py`` module is).

Run the command::

        python manage.py shell


Now in order to use our model definitions we need to import them.
Here all the model entities we will import: Entity, Intermediary, Officer, Address and Other.
Each entity maps to a specific structure of a node label, property keys and relationship types in the PPGDB.

Run the following python import commands::

    from fetch_api.models import Entity
    from fetch_api.models import Intermediary
    from fetch_api.models import Officer
    from fetch_api.models import Address
    from fetch_api.models import Other

Okay, now we are actually ready to start exploring the Paradise Paper Graph Database through the Neomodel Query API.

..  todo::
    Put screenshot image of the console here.

Neomodel Query API
==================
Each of your model definitions have a set of...


Exploring the Paradise Paper Graph Database
-------------------------------------------




