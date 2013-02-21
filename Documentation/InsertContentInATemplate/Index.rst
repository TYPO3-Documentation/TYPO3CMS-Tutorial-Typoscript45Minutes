.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../Includes.txt


.. _insert-content-in-a-template:

Insert content in a template
----------------------------

We now know how to render content, and how to build a menu; but we
still do not have a real website, yet.

We could build a website with COAs, and create the HTML skeleton with
TypoScript. Although, this would be very complex, and prone to errors.
If the HTML template has been built by a template designer and is
delivered completely done, it gets even more complicated, especially
with slight changes in the layout, afterward.

Therefore, we have the element TEMPLATE, with which we can parse an
HTML template, and insert the menu, content, and so on, at the right
place. ::

    page.10 = TEMPLATE
    page.10 {
     template = FILE

     # We load the HTML template
     template.file = fileadmin/test.tmpl

     # Text-areas
     # <!-- ###MENU### begin -->
     # Here is a example content as placeholder, everything which is in-between the markers will
     # be replaced by the content of the sub-parts, in this case the menu
     # <!-- ###MENU### end -->

     subparts {
       MENU < lib.textmenu
       CONTENT < styles.content.get
       COLUMNRIGHT < styles.content.getRight
     }

     # Marks are single marker. i.e. there is no start and end marker,
     # instead the marker is replaced directly. ###LOGO### will
     # be replaced by the logo
     marks {
       LOGO = IMAGE

       # The Graphic logo*.gif will be added in the resource-field of the TypoScript template
       LOGO.file = logo*.gif

       # The logo links to the page with ID 1
       LOGO.stdWrap.typolink.parameter = 1
     }
     workOnSubpart = DOCUMENT
    }

An alternative to this solution could be the extension
automaketemplate, with which it's possible to abandon markers,
completely. Instead, it uses IDs as references, and thus allows better
cooperation with the template designer.

Another alternative would be the extension templavoila. This extension
provides a visual user interface. This is not recommended for
beginners, though.


