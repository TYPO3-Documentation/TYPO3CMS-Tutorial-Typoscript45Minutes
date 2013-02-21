.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _function-numrows:
.. _numrows:

numRows
^^^^^^^

In TypoScript, there are not only big mighty functions, but also small
mighty ones. An example is the function numRows, which sole purpose is
to return the number of lines from a select query. Just like the
object CONTENT, numRows uses the select function. The query is
generated similarly in both cases. The difference is only whether the
number of lines is returned, or the actual content of those lines.

In cooperation with the "if" function, it is possible to generate some
nice stuff. An example is a stylesheet for the content of the right
column in the backend, which is only used if there actually is any
content in the right column. ::

   temp.headerdata = TEXT
   temp.headerdata {
           value = <link rel="stylesheet" type="text/css" href="fileadmin/templates/rechteSpalte.css">

           # if the select returns at least 1 line insert the stylesheet
           if.isTrue.numRows {

                   # check if this page
                   pidInList = this

                   # has content in table tt_content
                   table = tt_content

                   # SQL: WHERE colPos = 2
                   select.where = colPos=2
     }
   }

   # copy temp.headerdata in page.headerData.66 (and overwrite page.headerData.66)
   page.headerData.66 < temp.headerdata

Or, use another template if there is content in the right column::

   #a COA (Content Object Array) allows to merge many objects
   temp.maintemplate= COA
   temp.maintemplate {

           # 10 will only be embedded, if the if-Statement returns „true"
           10 = COA
           10 {
                   # we use a copy of the select from css_styled_content
                   if.isTrue.numRows < styles.content.getRight

                   10 = TEMPLATE
                   10 {
                           template = FILE
                           template.file = fileadmin/templates/template-2column.html
                   }
           }

           # 20 will only be embedded, if the if-Statement returns „true"
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

