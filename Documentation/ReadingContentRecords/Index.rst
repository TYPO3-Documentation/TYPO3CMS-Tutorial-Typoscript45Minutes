.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../Includes.txt


Reading content records
-----------------------

.. figure:: ../Images/icon_note.png
   :alt: Note

**Note**

*The following paragraphs serve as an example and for a better
understanding of the background and relationships. The following
scripts are from css\_styled\_content, and it's not necessary to write
them by hand. If a content element has to be rendered totally
different, or you programmed an extension with new content elements,
it will be necessary to understand the relationships.*

We do not want to enter all content with TypoScript - that would be
tiresome, and we can't expect an editor to do that.

So, we create a content element with the type " `TEXT
<http://wiki.typo3.org/TSref/TEXT>`_ ", and create a TypoScript which
will gather the content automatically. This example will create a page
with a headline and the text from all content elements which are on
the current page.

First, we create the `PAGE <http://wiki.typo3.org/TSref/PAGE>`_ object
so there will be some rendering at all. In this object PAGE we will
create the object `CONTENT <http://wiki.typo3.org/TSref/CONTENT>`_ ,
which can be controlled with various TypoScript parameters. ::

    page = PAGE
    page.typeNum = 0

    # The content-object executes a database query and loads the content
    page.10 = CONTENT
    page.10.table = tt_content
    page.10.select {

         # "sorting" is a column from the tt_content table and
           # keeps track of the sorting order which is given in the backend
         orderBy = sorting

         # normal column
         where = colPos = 0
    }

    # For every result-line from the database query the renderObj is executed
    # and the internal data array is filled with the content. This ensures that we
    # can call the .field property and we get the according value
    page.10.renderObj = COA
    page.10.renderObj {

      10 = TEXT

      # The field tt_content.header normally holds the headline.
      10.field = header

      10.wrap = <h1>|</h1>

      20 = TEXT

      # The field tt_content.bodytext holds the content text
      20.field = bodytext

      20.wrap = <p>|</p>
    }

The object CONTENT executes a SQL query on the database. The query is
controlled by "select". "Select" defines that we want all records from
the column 0 (which is the column "NORMAL" in the backend), and that
the result will be sorted according to the field "sorting". If the
property pidInList is not set or has been removed, the query will be
limited to the current page only. For example, if the page with ID 100
is referenced, the CONTENT object will only return records from the
page with pid=100.

The property renderObj defines how the records get rendered.
Therefore, it will be defined as COA (Content Object Array) which can
hold a arbitrary number of TypoScript objects. In this case, two TEXT
objects are used, which will be rendered one after the other. The
order of the rendering is not controlled by the order in TypoScript,
but by the number with which they are defined. The TEXT object "10"
will be created before the TEXT object "20".

The challenge is to render all content elements of type text like the
web designer predetermined. Therefore, we have to create a definition
for every field (e.g., for images, image size, image position, on top,
index, etc.)


.. toctree::
   :maxdepth: 5
   :titlesonly:
   :glob:

   TheContentElements/Index
   CssStyledContent/Index
   Stylescontentget/Index

