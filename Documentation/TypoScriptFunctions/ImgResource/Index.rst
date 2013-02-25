.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _function-imgresource:
.. _imgresource:

imgResource
^^^^^^^^^^^

The functions of the data type "imgResource" relate to modifications of
pictures. The object IMAGE has the property "file", which is inherited
from the data type "imgResource".

This, for example, allows an image to be resized::

   temp.myImage = IMAGE
   temp.myImage {

           file = toplogo.gif
           file.width = 200
           file.height = 300

   }

Enter maximum size (or minimum size)::

   temp.myImage = IMAGE
   temp.myImage {

           file = toplogo.gif

           # maximum size
           file.maxW = 200
           file.maxH = 300

           # minimum size
           file.minW = 100
           file.minH = 120

   }

imgResource also provides direct access to a GraphicsMagick function::

   temp.myImage = IMAGE
   temp.myImage {

           file = toplogo.gif
           file.params = -rotate 90

   }

One of the most common and best examples for the use of imgResource is
the implementation of pictures dynamically from the Media field in the
page properties. This has the advantage that editors can change the
pictures without using TypoScript. This allows us to have changing
header images for different areas of a website with a few lines of
TypoScript. ::

   temp.dynamicHeader = IMAGE
   temp.dynamicHeader {
           file {

                   # Define path to the images.
                   import = uploads/media/

                   import {

                           # If there are no images on this page, search recursively
                           # down the page tree.
                           data = level:-1, slide

                           # Enter the field, in which the image is defined.
                           field = media

                           # Define which of the images will be displayed,
                           # in this case the first it encounters.
                           listNum = 0

                   }
           }
   }

The path "uploads/media/" is the location of the files, which are
inserted in the "files" section. You find it inside the page properties
on the tab "Resources". The TypoScript in the brackets of "import"
completely consists of stdWrap functions, which are used to define from
where and which image will be imported. Finally, stdWrap returns the
file name of the image, which will then be imported from the import
path (uploads/media).

