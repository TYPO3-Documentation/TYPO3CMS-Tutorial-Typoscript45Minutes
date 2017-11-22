.. include:: ../../Includes.txt


.. _function-select:
.. _select:

======
select
======

The :ref:`select <t3tsref:select>` function generates a SQL SELECT query, which
is used to read records from the database. :code:`select` automatically checks
whether the records might be "hidden", "deleted", or if they have a "start and
end date". If :code:`pidInList` is used (meaning a list of pages is rendered),
the function also checks if the current user is allowed to see all records.

With the help of the select function, it is possible to show the content of a
page on all pages. For example:

.. code-block:: typoscript

    temp.leftContent = CONTENT
    temp.leftContent {

        table = tt_content
        select {

            # The page with ID = 123 is the source.
            pidInList = 123

            # Sorting is the same as in the backend.
            orderBy = sorting

            # Only select the content of the left column.
            where = {#colPos}=1

            # Define the field with the language ID in tt_content.
            languageField = sys_language_uid
        }
    }

    # Replace the mark ###LEFT### with the output of temp.leftContent.
    marks.LEFT < temp.leftContent

