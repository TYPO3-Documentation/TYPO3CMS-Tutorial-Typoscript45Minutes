

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


file link
^^^^^^^^^

With the function "file link" we can generate - as the name suggests -
a file link. While doing so, not just a link to the file is being
generated, but "filelink" also allows us to add an icon and display
the file size.

::

   temp.example = TEXT
   temp.example {
           
           # link description and file name at the same time
           value = my_image.png
   
         filelink {
   
                   # Path to the file
                   path = fileadmin/images/
   
                   # The file should have an icon
                   icon = 1
           
                   # The icon will be wrapped
                   icon.wrap = <span class=�icon�>|</span>
   
                   # The icon has to be linked to the file as well
                   icon_link = 1
   
                   # Instead of the symbol for the filetype the file 
               # will be displayed as an icon if it is of type png or gif
                   icon_image_ext_list = png,gif
   
                   # The size will be displayed as well
                   size = 1
   
                   # Wraps the filesize (with regard to the empty spaces)
                   size.noTrimWrap = | (| Bytes) |
   
                   # Rendering of the filesize will be done in bytes
                   size.bytes = 1
   
                   # Abbreviations for the various filesize units
                   size.bytes.labels =  | K| M| G
   
                   # Wrap for the whole element
                   stdWrap.wrap = <div class=“filelink“>|</div>
         }
   }

