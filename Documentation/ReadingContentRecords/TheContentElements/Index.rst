.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _content-objects:
.. _the-various-content-objects:

The various content elements
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Until now we only have rendering definitions for content elements
containing text. But there are different kinds of content elements. If
we want to render an image instead of a text, we have to choose
different fields from tt\_content, and also render them differently
compared to standard text. The same applies to "text & images",
"headline", etc.

The type of a content element is stored in the column
tt\_content.CType. In the following example, after having selected the
content elements e.g. with a CONTENT object, we show that with the
:ref:`CASE object <t3tsref:cobj-case>`, we can differentiate how the
individual content elements will get rendered. ::

    page.10.renderObj = CASE
    page.10.renderObj {

      # The field CType will be used to differentiate.
      key.field = CType

      # The content type "headline" is stored internally as "header".
      header = TEXT
      header.stdWrap.field = header
      header.stdWrap.wrap = <h1>|</h1>

      # Text is used for the text content element.
      text = COA
      text {

        10 = TEXT
        # The field tt_content.header normally holds the headline.
        10.stdWrap.field = header
        10.stdWrap.wrap = <h1>|</h1>

        20 = TEXT
        # The field tt_content.bodytext holds the content text.
        20.stdWrap.field = bodytext
        20.stdWrap.wrap = <p>|</p>

      }

      # ... other definitions follow here ...
    }

For content elements of the type "headline" we render the content of
the header field wrapped in <h1> tags. For content elements of the type
"text" we render the headline and the content text.

