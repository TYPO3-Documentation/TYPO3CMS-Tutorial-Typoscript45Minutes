.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _styles-content-get:

styles.content.get
^^^^^^^^^^^^^^^^^^

::

    # Our code so far starts like that:
    page.10 = CONTENT
    page.10.table = tt_content
    page.10.select {

        # Use the sorting of the backend. We could as well use the date field or the header.
        orderBy = sorting

        # normal column
        where = colPos = 0
    }

Thanks to css\_styled\_content, it suffices to just write the following
instead to achieve the same::

    # This returns content from the "normal" column (colPos = 0).
    page.10 < styles.content.get

For the other columns there are according default definitions, as
well::

    # This returns content from the "left" column (colPos = 1).
    page.10 < styles.content.getLeft

    # This returns content from the "right" column (colPos = 2).
    page.10 < styles.content.getRight

    # This returns content from the "border" column (colPos = 3).
    page.10 < styles.content.getBorder

In css\_styled\_content the border is internally defined as follows::

    # The normal column is copied.
    styles.content.getBorder < styles.content.get

    # After that, colPos is altered.
    styles.content.getBorder.select.where = colPos=3

