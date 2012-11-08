.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


styles.content.get
^^^^^^^^^^^^^^^^^^

::

    # our code so far
    page.10 = CONTENT
    page.10.table = tt_content
    page.10.select {

        # Use the sorting of the backend we could as well use the date field or the header
        orderBy = sorting

        # normal column
        where = colPos = 0
    }

Thanks to css\_styled\_content, it suffices to write the following to
achieve the same::

    # Returns content from the "normal" column (colPos = 0)
    page.10 < styles.content.get

For the other columns there are default definitions, as well::

    # Returns content from the "left" column (colPos = 1)
    page.10 < styles.content.getLeft

    # Returns content from the "right" column (colPos = 2)
    page.10 < styles.content.getRight

    # Returns content from the "border" column (colPos = 3)
    page.10 < styles.content.getBorder

In css\_styled\_content the border is defined as follows::

    # The normal column is copied
    styles.content.getBorder < styles.content.get

    # after that colPos is altered
    styles.content.getBorder.select.where = colPos=3

