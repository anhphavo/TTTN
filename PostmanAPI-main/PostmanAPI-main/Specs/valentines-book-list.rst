**************************
Valentine's Book List API
**************************

This API allows you to view the books that Valentine has read or plans to read.

The API is available at ``https://valentines-book-list.glitch.me``

.. contents:: **Endpoints:**
   :depth: 4
   :local:
   :backlinks: top
.. sectnum::
   :depth: 2

Status
======

``GET /status``

Returns the status of the API. Example response:

.. code:: json

  {
      "status": "UP"
  }

Status ``UP`` indicates that the API is running as expected.

No response or any other response indicates that the API is not functioning correctly.

Books
=====

Get a book list
---------------

``GET /books/lists``

Returns a list of books. Requires authentication. 

This endpoint uses pagination to handle the returned results. Paginating the results ensures responses are easier to handle. Each response will indicate the total number of results, the current page, and the total number of pages.

Parameters
~~~~~~~~~~

+-------------+---------+-------+--------------+---------------------------------------------------------------------------------------------------------------------------+
| **Name**    | **Type**| **In**| **Required** | **Description**                                                                                                           |
+=============+=========+=======+==============+===========================================================================================================================+
| ``list``    | string  | query | Yes          | Specifies the list you want to retrieve. Must be one of: ``favourite-books``, ``non-fiction``, ``wishlist``, ``fiction``. |
+-------------+---------+-------+--------------+---------------------------------------------------------------------------------------------------------------------------+
| ``api-key`` | string  | query | Yes          | ``8fhg93xkjd38fhg834jdfgjd``                                                                                              |
+-------------+---------+-------+--------------+---------------------------------------------------------------------------------------------------------------------------+
| ``page``    | integer | query | No           | Specifies the page you wish to retrieve from the entire result set.                                                       |
+-------------+---------+-------+--------------+---------------------------------------------------------------------------------------------------------------------------+


Status codes
~~~~~~~~~~~~

+----------------------+-----------------------------------------------------+
| **Status code**      | **Description**                                     |
+======================+=====================================================+
| ``200 OK``           | Indicates a successful response.                    |
+----------------------+-----------------------------------------------------+
| ``400 Bad Request``  | Indicates that the parameters provided are invalid. |
+----------------------+-----------------------------------------------------+
| ``401 Unauthorized`` | API Key invalid.                                    |
+----------------------+-----------------------------------------------------+

Example response:
~~~~~~~~~~~~~~~~~

``200 Success``
^^^^^^^^^^^^^^^

.. code:: json

  {
      "status": "OK",
      "num_results": 17,
      "page": 1,
      "total_pages": 4,
      "results": [
          {
              "title": "Crush It!: Why NOW Is the Time to Cash In on Your Passion",
              "category": [
                  "non-fiction"
              ],
              "type": "audio",
              "author": "Gary Vaynerchuk",
              "release_year": 2010,
              "rating": "7"
          },
          ...
      ]
  ]

``400 Bad Request``
^^^^^^^^^^^^^^^^^^^

.. code:: json

  {
      "error": {
          "error-string": "Failed to resolve API List parameter request.queryparam.list",
          "detail": {
              "errorcode": "MISSING_BOOK_LIST"
          }
      }
  }


``401 Unauthorized``
^^^^^^^^^^^^^^^^^^^^

.. code:: json

  {
      "error": {
          "error-string": "Failed to resolve API Key parameter request.queryparam.api-key",
          "detail": {
              "errorcode": "FAILED_TO_RESOLVE_API_KEY"
          }
      }
  }

API Authentication
==================

Some endpoints require authentication. 

The endpoints that require authentication expect the API key to be provided as a query parameter named `api-key`.
