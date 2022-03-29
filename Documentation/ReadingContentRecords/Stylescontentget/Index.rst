.. include:: /Includes.rst.txt


.. _styles-content-get:

styles.content.get
^^^^^^^^^^^^^^^^^^

"css\_styled\_content" does more than just provide us with
rendering definitions. It also provides useful :ref:`CONTENT <t3tsref:cobj-content>`
objects definitions.

So far our code looks like this:

.. code-block:: typoscript

    page.10 = CONTENT
    page.10.table = tt_content
    page.10.select {

        # Use the sorting of the backend. We could as well use the date field or the header.
        orderBy = sorting

        # normal column
        where = colPos = 0
    }

We can reuse predefined objects from "css\_styled\_content" and
write the following instead:

.. code-block:: typoscript

    # This returns content from the "normal" column (colPos = 0).
    page.10 < styles.content.get

There are similar definitions for the other columns:

.. code-block:: typoscript

    # This returns content from the "left" column (colPos = 1).
    page.10 < styles.content.getLeft

    # This returns content from the "right" column (colPos = 2).
    page.10 < styles.content.getRight

    # This returns content from the "border" column (colPos = 3).
    page.10 < styles.content.getBorder
