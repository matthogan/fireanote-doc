.. _troubleshooting:

Troubleshooting
===============

Forgotten password
------------------

Click the `Can't remember your password?` link on the sign in dialog 
and enter the email to receive a link to change your password.

.. image:: _static/images/forgot-pw.png
  :width: 600
  :alt: Forgotten password

Invalid request
---------------

Validate the JSON_ in the request using a json_formatter_. 
Verify the data in each field, for instance the body may contain unescaped double quotes.

See the :ref:`api-send-notification` definition.


.. _Fireanote: https://www.fireanote.com
.. _JSON: https://json.org/
.. _json_formatter: https://jsonformatter-online.com/
