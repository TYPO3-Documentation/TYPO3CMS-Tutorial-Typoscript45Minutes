

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


The various content elements
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If we want to render an image instead of a text, we have to choose
different fields from tt\_content, and also render them differently
than standard text. The same applies to "text with image", "headline",
etc.

The type of a content element is stored in the column
tt\_content.CType. In the following example, we show that with the
CASE object, we can differentiate how the individual content elements
will get rendered.

::

    10.renderObj = CASE
    10.renderObj {
   
      # the field CType will be used to differentiate
      key.field = CType
   
      # The content type "headline" is stored internally as "header"
      header = TEXT
      header.field = header
      header.wrap = <h1>|</h1>
   
      # Text is used for the text content element
      text = COA
      text {
   
        10 = TEXT
        # the field tt_content.header normally holds the headline.
        10.field = header
        10.wrap = <h1>|</h1>
   
        20 = TEXT
        # the field tt_content.bodytext holds the content text 
        20.field = bodytext
        20.wrap = <p>|</p>
   
      }
   
      # ... other definitions follow here
    }

