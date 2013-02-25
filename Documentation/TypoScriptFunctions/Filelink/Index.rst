.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _function-filelink:
.. _filelink:

filelink
^^^^^^^^

With the function "filelink" we can generate - as the name suggests -
a link to a file. While doing so, not just a link to the file is being
generated, but "filelink" also allows us to add an icon and display
the file size. ::

   temp.example = TEXT
   temp.example {

           # Link description and file name at the same time.
           value = my_image.png

           filelink {

                   # Path to the file.
                   path = fileadmin/images/

                   # The file should have an icon.
                   icon = 1

                   # The icon will be wrapped.
                   icon.wrap = <span class="icon">|</span>

                   # The icon should be linked to the file as well.
                   icon_link = 1

                   # Instead of the symbol for the file type, the file
                   # will be displayed as an icon, if it is of type .png or .gif.
                   icon_image_ext_list = png,gif

                   # The file size will be displayed as well.
                   size = 1

                   # Wraps the file size (with regard to the empty spaces).
                   size.noTrimWrap = | (| bytes) |

                   # Rendering of the file size will be done in bytes.
                   size.bytes = 1

                   # Abbreviations for the various file size units.
                   size.bytes.labels =  | K| M| G

                   # Wrap for the whole element.
                   stdWrap.wrap = <div class="filelink">|</div>
           }
   }

