.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _function-if:
.. _if:

if
^^

The perhaps most difficult TYPO3 function is the "if" function, because
every programmer, who is familiar with if functions from somewhere
else, instinctively misuses it. Therefore, we have some examples to
show, how it works correctly.

Generally, the if function returns "true", if **all** conditions are
fulfilled. This resembles a boolean AND combination. If "false" should
be returned in that case, we can use the "negate" option to negate the
result (like a !(true)). ::

   10 = TEXT
   10 {

       # Content of the TEXT object.
       value = The L parameter is passed as GET variable.

       # Results in "true" and leads to rendering the upper value, if the
       # GET/POST parameter is passed with a value, which is not 0.
       stdWrap.if.isTrue.data = GP:L
   }

With the use of "if" it is also possible to compare values. For this
purpose we use the parameter "if.value". ::

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

Because the properties of the "if" function implement stdWrap
functions, all kinds of variables can be compared. ::

   10 = TEXT
   10 {
       # Value of the TEXT object.
       value = The record can be shown, because the starting date has passed.

       # Condition of the if clause (number of seconds since January 1st, 1970).
       stdWrap.if.value.data = date:U

       # Condition backwards again: Start time isLessThan date:U.
       stdWrap.if.isLessThan.field = starttime
   }

