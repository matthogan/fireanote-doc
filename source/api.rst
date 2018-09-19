API
===

Endpoint
--------

https://api.firenote.com/api/v0.1/

All calls are invoked over SSL. HTTP calls will be redirected to HTTPS 
using a 302 response status.

.. _api-authorization:
Authorization
-------------

API calls are authorized using the HTTP authorization header, which contains a comma delimited list of key pairs containing the api keys required to match the notification with the app and its group.

Schema
-------

<auth-scheme>\<space>\<auth-param>

Fields:-

+----------------+-------------------+----------------------------------+
| Field          | Description       | Values                           |  
+================+===================+==================================+
| auth-scheme    | literally CJ      | CJ                               |
+----------------+-------------------+----------------------------------+
| auth-param     | Encoded api keys  | Base64 encoded list of key pairs |
+----------------+-------------------+----------------------------------+

Key pairs:-

+---------------+-----------------------------------------------+---------------------------------+
| Key           | Description                                   | Format                          |
+===============+===============================================+=================================+
| client-id     | The app's group API key and the app's API key | <group-api-key>:<app-api-key>   |
+---------------+-----------------------------------------------+---------------------------------+
| redirect_uri  | Field is unused and reserved                  |                                 |
+---------------+-----------------------------------------------+---------------------------------+
| response_type | token (literally)                             | token                           |
+---------------+-----------------------------------------------+---------------------------------+
| scope         | Field is unused and reserved                  |                                 |
+---------------+-----------------------------------------------+---------------------------------+
| state         | Field is unused and reserved                  |                                 |
+---------------+-----------------------------------------------+---------------------------------+

Example
-------

The group and app api keys are appended and separated by a colon:-

```
CJ client-id=129923561bbd0869:565fcac43a3f2b80,response_type=token
```

And encoded as:-

```
CJ Y2xpZW50LWlkPTEyOTkyMzU2MWJiZDA4Njk6NTY1ZmNhYzQzYTNmMmI4MCxyZXNwb25zZV90eXBlPXRva2VuCg==
```

.. _api-send-notification:

Send notification
-----------------

Notify that an event has occurred.

URI
---

https://api.fireanote.com/api/v0.1/notification

Request
-------

HTTP verb
---------

POST

Headers
-------

+-------------------+------------------------------------------------------+
| Header            | Value                                                |  
+===================+======================================================+
| content-type      | application/json, application/json; charset=utf8     |
+-------------------+------------------------------------------------------+
| accept            | application/json, application/json; charset=utf8     |
+-------------------+------------------------------------------------------+
| authorization*    | CJ Y2xpZ.....PXRva2VuCg==                            |
+-------------------+------------------------------------------------------+

Body
----

The payload is valid JSON with a simplistic and customizable format. The power of the generic fields relies on your own definition of their values, for instance the categories should be driven by the app definition, not by the message handler.

Example::

  {
    "notificationId" : "KTfn89CvlLqJ1FTQDLm1",
    "description" : "An error happened in the system",
    "dataType" : "text/plain",
    "category" : "DEFCON3",
    "priority" : "SEVERE",
    "body" : "Was it something I said? Something I didn't do?"
  }

Fields
------

+----------------+--------+------------+----------------------------------------------------------------------------------------------------------------------------+
| Field          | Type   | Max Length | Description                                                                                                                |
+================+========+============+============================================================================================================================+
| notificationId | string | 100        | Your unique identifier. The system will not enforce uniqueness. Think of it as a message identifier or a correlation id.   |
+----------------+--------+------------+----------------------------------------------------------------------------------------------------------------------------+
| description    | string | 100        | Describe the message.                                                                                                      |
+----------------+--------+------------+----------------------------------------------------------------------------------------------------------------------------+
| dataType       | string | 100        | Your data type identifier. Recommendation:- mime-types                                                                     |
+----------------+--------+------------+----------------------------------------------------------------------------------------------------------------------------+
| category       | string | 100        | A generic category classifier, for instance a business level category such as MEDICAL, or a severity index such as DEFCON. |
+----------------+--------+------------+----------------------------------------------------------------------------------------------------------------------------+
| priority       | string | 100        | Your priority assignment for this notification.                                                                            |
+----------------+--------+------------+----------------------------------------------------------------------------------------------------------------------------+
| body           | string | 4000       | Content of the message, such as an error message, or any text including user messages and so on.                           |
+----------------+--------+------------+----------------------------------------------------------------------------------------------------------------------------+

.. _api-notification-response:
Response
--------

HTTP Status

201 Created

Headers

+-------------+----------------------------------+--------------------------------------------------+
| Header      | Description                      | Format                                           |  
+=============+==================================+==================================================+
| location    | Path to the created notification | /api/v0.1/user/web/notification/<notificationId> |
+-------------+----------------------------------+--------------------------------------------------+

