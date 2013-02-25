.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _function-imagelinkwrap:
.. _imagelinkwrap:

imageLinkWrap
^^^^^^^^^^^^^

With "imageLinkWrap", we can wrap the image with a link to the PHP
script
"typo3/sysext/frontend/Classes/Controller/ShowImageController.php". The
script will open the image in a new window with predefined parameters
like window background, image size, etc. This function can be used to
create "click-to-enlarge" functionality. (A small image (thumbnail) is
clicked to open a new window and show the image in its original size.) ::

   temp.myImage = IMAGE
   temp.myImage {

           file = toplogo.gif

           imageLinkWrap = 1
           imageLinkWrap {

                   # Activate ImageLinkWrap.
                   enable = 1

                   # Define the body tag for the new window.
                   bodyTag = <body class="ImageOriginal">

                   # Wrap the image. (Close the window, if it is clicked.)
                   wrap = <a href="javascript:close();"> | </a>

                   # Width of the image(m allows proportional scaling).
                   width = 800m

                   # Height of the image.
                   height = 600

                   # Create a new window for the image.
                   JSwindow = 1

                   # Open a new window for every image (instead of using the same window).
                   JSwindow.newWindow = 1

                   # Padding for the new window.
                   JSwindow.expand = 17,20
           }

   }

