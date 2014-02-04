.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _function-numrows:
.. _numrows:

numRows
^^^^^^^

In TypoScript, there are not only *big* mighty functions, but also
*small* mighty functions. An example is the function numRows, which has
the sole purpose to return the number of lines of a SELECT query. Just
like the object CONTENT, numRows uses the :ref:`select` function. The
query is generated similarly in both cases. The difference is only
whether the number of lines or the actual content of those lines is
returned.

In cooperation with the ":ref:`if`" function, it is possible to
generate some nice stuff. An example is a stylesheet for the content of
the right column in the backend, which is only used if there actually
also is some content in the column. ::

   temp.headerdata = TEXT
   temp.headerdata {
           value = <link rel="stylesheet" type="text/css" href="fileadmin/templates/rightColumn.css">

           # If the select returns at least one line, insert the stylesheet.
           stdWrap.if.isTrue.numRows {

                   # Check if this page
                   pidInList = this

                   # has content in table tt_content,
                   table = tt_content

                   # which belongs in the right column (the column with "colPos=2").
                   select.where = colPos=2
           }
   }

   # Copy temp.headerdata in page.headerData.66 (and overwrite page.headerData.66).
   page.headerData.66 < temp.headerdata

Or, use another template, if there is content in the right column::

   # A COA (content object array) allows us to merge many objects.
   temp.maintemplate= COA
   temp.maintemplate {

           # 10 will only be embedded, if the "if" Statement returns "true".
           10 = COA
           10 {
                   # We use a copy of the select from css_styled_content.
                   if.isTrue.numRows < styles.content.getRight

                   10 = TEMPLATE
                   10 {
                           template = FILE
                           template.file = fileadmin/templates/template-2column.html
                   }
           }

           # 20 will only be embedded, if the "if" Statement returns "true".
           20 = COA
           20 {
                   if.isFalse.numRows < styles.content.getRight
                   10 = TEMPLATE
                   10 {
                           template = FILE
                           template.file = fileadmin/templates/template.html
                   }
           }
   }

