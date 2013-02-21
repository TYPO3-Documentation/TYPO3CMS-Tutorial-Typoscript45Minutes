.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _function-if:
.. _if:

if
^^

The perhaps most difficult TYPO3 function is the "if" function,
because every programmer who is familiar with it instinctively misuses
it. Therefore, we have some examples to show how it works.

Generally, the if function returns "true" if all conditions are
fulfilled. This resembles a Boolean AND combination. If "false" should
be returned, we can use the "negate" option to negate the result
(!(true)). ::

   10 = TEXT
   10 {

       # Content of the text-element
       value = The L parameter is passed as GET var

       # Results in "true" and leads to rendering the upper value if the
       # GET/POST parameter is passed with a value which is not 0
       if.isTrue.data = GP:L
   }

With the use of "if" it is also possible to compare values. Therefore
we use the parameter if.value. ::

   10 = TEXT
   10 {

       # WARNING: this value resembles the value of the text element not that of the "if"
       value = 3 is bigger than 2

       # compare parameter of the "if"-funtion
       if.value = 2

       # please note: the sorting order is backwards, this example
       # returns the sentence "3 isGreaterThan 2"
       if.isGreaterThan = 3
   }

Because the properties of the "if" function implement stdWrap
functions, all kinds of variables can be compared. ::

   10 = TEXT
   10 {
       # value of the text element
       value = The record can be shown because the starting date has passed.

       # condition of the if-clause
       if.value.data = date:U

       # condition backwards again: start time isLessThan date:U
       if.isLessThan.field = starttime
   }

