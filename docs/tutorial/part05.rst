======================
How to create the API.
======================

Why the API structure
=====================

We decided to use APIs to fetch the data to make queries more effective, as sometimes queries get too big, we decided it was better to fetch the data in little chunks rather than one big request and that's what APIs allows us to do.

Explain the library
===================

In this project, we are using the rest_framework_ library because it has some simple non-limiting ways to implement an API structure, if you desire you can use any of your choosing, but the examples presented ahead will be based on the behavior of this specific library.

    .. _rest_framework: http://www.django-rest-framework.org/

Install the library
===================

Just run::

    pip install rest_framework

On your console and restart your Django server.

Create the views / endpoints
============================

We are going to need a couple different endpoints to make our application work, but for now, we will focus on one to explain the process of making them, we are going to be building the ``GetNodesData / nodes`` that will serve us to fetch the search matches nodes data. We'll be using a type of class-based view called ``APIView`` from the framework to make them, this will allow us to have an endpoint rather than a page view.

Clean your ``fetch_api/views.py`` file and add the following code::

    from rest_framework.views import APIView
    from rest_framework.response import Response
    from rest_framework import status

    class GetNodesData(APIView):
        def get(self, request):
            return Response(‘Temporary Data’, status=status.HTTP_200_OK)

Now on your ``fetch_api/urls.py`` add the endpoint to the urls::

    from django.conf.urls import url
    from .views import GetNodesData

    urlpatterns = [
        url(r’^nodes[/]?$’, GetNodesData.as_view(), name=‘get_nodes_data’),
    ]

Now on you can hit the endpoint with a method of your choosing, for this example, we are going to use curl, on your console:

``curl http://127.0.0.1:8000/fetch/nodes``

You should see:

``"Temporary Data"``

The other 5 endpoints with its classes/URLs respectively are :

GetNodesCount / count, to fetch the count of matches

GetNodeData / node, to fetch the info for a specific node

GetCountries / countries, to fetch the list of countries

GetJurisdictions / jurisdictions, to fetch the list of jurisdictions

GetDataSource / datasource, to fetch the list of data sources

When you finish your ``fetch_api/views.py`` file should look like this::

    from rest_framework.views import APIView
    from rest_framework.response import Response
    from rest_framework import status

    class GetNodesCount(APIView):
        def get(self, request):
            return Response(‘Temporary Data’, status=status.HTTP_200_OK)

    class GetNodesData(APIView):
        def get(self, request):
            return Response(‘Temporary Data’, status=status.HTTP_200_OK)

    class GetNodeData(APIView):
        def get(self, request):
            return Response(‘Temporary Data’, status=status.HTTP_200_OK)

    class GetCountries(APIView):
        def get(self, request):
            return Response(‘Temporary Data’, status=status.HTTP_200_OK)

    class GetJurisdictions(APIView):
        def get(self, request):
            return Response(‘Temporary Data’, status=status.HTTP_200_OK)

    class GetDataSource(APIView):
        def get(self, request):
            return Response(‘Temporary Data’, status=status.HTTP_200_OK)

And the ``fetch_api/urls.py`` should look like this::

    from django.conf.urls import url
    from .views import (
        GetNodesCount,
        GetNodesData,
        GetNodeData,
        GetCountries,
        GetJurisdictions,
        GetDataSource,
    )

    urlpatterns = [
        url(r'^count[/]?$', GetNodesCount.as_view(), name='get_nodes_count'),
        url(r'^nodes[/]?$', GetNodesData.as_view(), name='get_nodes_data'),
        url(r'^node[/]?$', GetNodeData.as_view(), name='get_node_data'),
        url(r'^countries[/]?$', GetCountries.as_view(), name='get_countries'),
        url(r'^jurisdictions[/]?$', GetJurisdictions.as_view(), name='get_jurisdictions'),
        url(r'^datasource[/]?$', GetDataSource.as_view(), name='get_data_source'),
    ]
