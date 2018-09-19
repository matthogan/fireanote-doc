Frequently Asked Questions
==========================

How do I generate the authorization header?
-------------------------------------------

The header requires the app api key and its group api key.

See the documentation on :ref:`api-authorization`.

.. _faq-group-api-key:
Where is my group API key?
--------------------------

Find the group API key in the `Configuration` for the given group.

.. image:: _static/images/group-configuration.png
  :alt: Group configuration

.. image:: _static/images/group-configuration-api-key.png
  :alt: Group API key


Where is my app API key?
------------------------

Find the app API key in `Manage Apps` for the given group.

.. image:: _static/images/group-apps.png
  :alt: Manage apps

.. image:: _static/images/app-api-key.png
  :alt: App API key


What is the API endpoint?
-------------------------

https://api.fireanote.com/api/v0.1/notification

See the documentation on :ref:`api-send-notification`.

Where is the response?
----------------------

The notification call has no response body, however an 
HTTP status code of 201 will be present in the 
:ref:`api-notification-response` header.
