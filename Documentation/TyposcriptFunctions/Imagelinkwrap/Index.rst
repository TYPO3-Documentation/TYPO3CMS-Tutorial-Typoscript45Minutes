

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


imageLinkWrap
^^^^^^^^^^^^^

By using "imageLinkWrap", we can wrap the image with a link to the PHP
script "showpic.php". The script will open the image in a new window
with predefined parameters like window background, image size, etc.
This function can be used to create "click-to-enlarge" functionality.
(A small image (thumbnail) is clicked to open a new window and show
the image in its original size.)

::

   temp.meinBild = IMAGE
   temp.meinBild {
          
            file = toplogo.gif
   
           imageLinkWrap = 1
           imageLinkWrap {
   
                   # activate ImageLinkWrap 
                   enable = 1
   
                   # define the body tag for the new window
                   bodyTag = <body class=“BildOriginal“>
   
                   # wrap the image (Close the window if it is clicked)
                   wrap = <a href="javascript:close();"> | </a>
   
                   # Width of the image(m allows proportional scaling)
                   width = 800m
   
                   # height of the image
                   height = 600
   
                   # create a new window for the image
                   JSwindow = 1
   
                   # open a new window for every image (instead of using the same window)
                   JSwindow.newWindow = 1
   
                   # Padding for the new window
                   JSwindow.expand = 17,20
           }
   
   }

