.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _function-select:
.. _select:

select
^^^^^^

The function "select" generates an SQL SELECT query, which is used to
read records from the database. The select function automatically
checks whether the records might be "hidden", or "deleted", or if they
have a "start and end date". If pidInList is used (meaning a list of
pages is rendered), the function also checks if the current user is
allowed to see all records.

With the help of the select function, it is possible to show the
content of a page on all pages. For example::

    temp.leftContent = CONTENT
    temp.leftContent {

        table = tt_content
        select {

            # The page with ID = 123 is the source.
            pidInList = 123

            # Sorting is like in the backend.
            orderBy = sorting

            # Only select the content of the left column.
            where = colPos=1

            # Define the field with the language ID in tt_content.
            languageField = sys_language_uid
        }
    }

    # Replace the mark ###LEFT### with the output of temp.leftContent.
    marks.LEFT < temp.leftContent

