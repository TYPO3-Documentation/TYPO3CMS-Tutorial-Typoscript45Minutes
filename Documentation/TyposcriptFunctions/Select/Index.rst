

.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. ==================================================
.. DEFINE SOME TEXTROLES
.. --------------------------------------------------
.. role::   underline
.. role::   typoscript(code)
.. role::   ts(typoscript)
   :class:  typoscript
.. role::   php(code)


select
^^^^^^

The function "select" generates a SQL SELECT query, which is used to
read records from the database. The select function automatically
checks whether the records might be "hidden", or "deleted", or if they
have a "start and end date". If pidInList is used (meaning a list of
pages is rendered), the function also checks if the current user is
allowed to see all records.

With the help of the select function, it is possible to show the
content of a page on all pages, for example.

::

    temp.leftContent = CONTENT
    temp.leftContent {
   
        table = tt_content
        select {
   
            # the page with ID = 123 is the source
            pidInList = 123
   
            # sorting is like in the backend
            orderBy = sorting
   
            # content of the left column
            where = colPos=1
   
            # defines the field with the lanuguage-ID in tt_content
            languageField = sys_language_uid
        }
    }
   
    # defines the field with the lanuguage-ID in tt_content
    marks.LEFT < temp.leftContent

