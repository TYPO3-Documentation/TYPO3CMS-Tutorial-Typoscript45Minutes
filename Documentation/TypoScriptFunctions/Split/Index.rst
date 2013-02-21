.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _function-split:
.. _split:

split
^^^^^

The split function can be used to split given data at a predefined
character, and process the single pieces afterward. At every
iteration, the current index key "SPLIT-COUNT" is stored (starting
with 0).

By using "split", we could, for example, read a table field and wrap
every single line with a certain code (e.g., generate a HTML table
which can be used to show the same content on more than one page)::

     # Example
     20 = TEXT

     # The content of the field "bodytext" is imported (from $cObj->data-array)
     20.field = bodytext
     20.split {

       # The separation character (char = 10 is newline) is defined.
       token.char = 10

       # We define which element will be used.
       # By using optionSplit we can distinguish between elements.
       # A corresponding element with the number must be defined!
       # Here the option split property is used.
       # Alternating the number 1 and 2 are being used for rendering.
       # In this example the classes "odd" and "even" are used so we can style a table in zebra style.
       cObjNum = 1 || 2

       # The first element is being defined (which is referenced by cObjNum)
       # The content is imported using stdWrap->current
       1.current = 1

       # The element is wrapped
       1.wrap = <TR class="odd"><TD valign="top"> | </TD></TR>

       # The 2nd element is determined and wrapped
       2.current = 1
       2.wrap = <TR class="even"><TD valign="top"> | </TD></TR>
     }

     # A general wrap to create valid table markup
     20.wrap = <TABLE border="0" cellpadding="0" cellspacing="3" width="368"> | </TABLE>

