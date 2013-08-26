.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../Includes.txt


.. _reading-content-records:

Reading content records
-----------------------

.. note::

   *The following chapter serves as an example and for a better
   understanding of the background and relationships. The following
   scripts are from css\_styled\_content, and it's **not** necessary to
   write them by hand. If a content element has to be rendered totally
   differently, or you programmed an extension with new content elements,
   it will be necessary to understand the relationships.*

We do not want to enter all content written in TypoScript - that would
be tiresome, and we can't expect an editor to do that.

So, we create a TypoScript, which will gather the content
automatically. The next example will create a page, on which for each
content element on that page we will get displayed the headline of the
content element and the text of the content element.

First, we create the :ref:`PAGE <t3tsref:page>` object
so there will be some rendering at all. In this PAGE object we will
create the object :ref:`CONTENT <t3tsref:cobj-content>`,
which can be controlled with various TypoScript parameters. Inside it,
we do the rendering of each content element using objects of the type
":ref:`TEXT <t3tsref:cobj-text>`"::

    page = PAGE
    page.typeNum = 0

    # The CONTENT object executes a database query and loads the content.
    page.10 = CONTENT
    page.10.table = tt_content
    page.10.select {

         # "sorting" is a column from the tt_content table and
         # keeps track of the sorting order, which was specified in
         # the backend.
         orderBy = sorting

         # Only select content from column "0" (the column called
         # "normal").
         where = colPos = 0
    }

    # For every result line from the database query (that means for every content
    # element) the renderObj is executed and the internal data array is filled
    # with the content. This ensures that we can call the .field property and we
    # get the according value.
    page.10.renderObj = COA
    page.10.renderObj {

      10 = TEXT

      # The field tt_content.header normally holds the headline.
      10.field = header

      10.wrap = <h1>|</h1>

      20 = TEXT

      # The field tt_content.bodytext holds the content text.
      20.field = bodytext

      20.wrap = <p>|</p>
    }

The object CONTENT executes an SQL query on the database. The query is
controlled by the property "select". Here "select" defines that we want
all records from the column 0 (which is the column "NORMAL" in the
backend), and that the result will be sorted according to the field
"sorting". If the property pidInList is not set (like here) or has been
removed, the query will be limited to the current page only. For
example, if the page with ID 100 is referenced, the CONTENT object will
only return records from the page with pid=100.

The property renderObj defines how each record gets rendered.
Therefore, it is defined as COA (Content Object Array), which can hold
an arbitrary number of TypoScript objects. In this case, two TEXT
objects are used, which will be rendered one after the other. Remember
that the order of the rendering is not controlled by the order in
TypoScript, but by the numbers with which they are defined. The TEXT
object "10" will be created first and the TEXT object "20" will be
rendered after it.

The challenge is to render all content elements like the web designer
predetermined. Therefore, we have to create TypoScript definitions for
every single database field (e.g. for images, image size, image
position, link to top, index, etc.).


.. toctree::
   :maxdepth: 5
   :titlesonly:
   :glob:

   TheContentElements/Index
   CssStyledContent/Index
   Stylescontentget/Index

