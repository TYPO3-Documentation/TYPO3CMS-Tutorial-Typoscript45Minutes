.. include:: ../../Includes.txt


.. _function-if:
.. _if:

if
^^

The :ref:`if <t3tsref:if>` function is perhaps the most difficult
of all TypoScript functions. It does not work like the "if" construct
known from most programming language and is thus very open to misuse.
Hopefully the examples below will help you get it right.

Generally the :code:`if` function returns :code:`true`,
if **all** conditions are fulfilled. This resembles a boolean AND combination.
If what we would like returned is a :code:`false` value,
we can use the :code`negate` option to negate the result.

.. code-block:: typoscript

   10 = TEXT
   10 {

       # Content of the TEXT object.
       value = The L parameter is passed as GET variable.

       # Results in "true" and leads to rendering of the upper value, if the
       # GET/POST parameter is passed with a value, which is not 0.
       stdWrap.if.isTrue.data = GP:L
   }

With the use of :code:`if` it is also possible to compare values. For this
purpose we use :code:`value` property.

.. code-block:: typoscript

   10 = TEXT
   10 {

       # WARNING: This value resembles the value of the TEXT object, not that of the "if"!
       value = 3 is bigger than 2.

       # Compare parameter of the "if" function.
       stdWrap.if.value = 2

       # Please note: The sorting order is "backwards",
       # returning the sentence "3 isGreaterThan 2".
       stdWrap.if.isGreaterThan = 3
   }

Because the properties of the :code:`if` function implement
:ref:`stdWrap functions <using-stdwrap>`, all kinds of variables can be compared.

.. code-block:: typoscript

   10 = TEXT
   10 {
       # Value of the TEXT object.
       value = The record can be shown, because the starting date has passed.

       # Condition of the if clause (number of seconds since January 1st, 1970).
       stdWrap.if.value.data = date:U

       # Condition backwards again: Start time isLessThan date:U.
       stdWrap.if.isLessThan.field = starttime
   }

