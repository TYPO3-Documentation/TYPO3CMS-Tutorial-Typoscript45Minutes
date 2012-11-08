.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../Includes.txt


TypoScript functions
--------------------

TypoScript functions are used to change and adjust the output of
content elements. The most popular function is the standard wrap,
better known as stdWrap. Whether an object implements a certain
function, or not, is shown in TSRef, column data type..


.. ### BEGIN~OF~TABLE ###

.. container:: table-row

   Property
         Property

   Data type
         Data type

   Description
         Description

   Default
         Default


.. container:: table-row

   Property
         file

   Data type
         imgResource

   Description


   Default


.. container:: table-row

   Property
         imageLinkWrap

   Data type
         ->imageLinkWrap

   Description
         [...]

   Default


.. container:: table-row

   Property
         if

   Data type
         ->if

   Description
         [...]

   Default


.. container:: table-row

   Property
         altTexttitleText

   Data type
         String/stdWrap

   Description
         [...]

   Default


.. ###### END~OF~TABLE ######


[Example:(cObject).IMAGE]

The first line in this example (property = file) tells us that file is
of the data type imgResource. This means that we can use the
imgResource functions on the file property.

Sometimes functions are - for better recognition - marked with an
arrow (like -> if).

If there are multiple entries separated by a slash, it means that you
have various possibilities to use that element. In the example above,
you can see this with titleText and altText. Both can be either plain
string or stdWrap. So, you can enter a plain string and do nothing
more; or you can adjust and change your string by using stdWrap
features on it; or you can leave the string empty all together and
generate the content with stdWrap, only.

Some important and frequently used functions are presented in the
following subsections. This chapter is about introducing those
functions, and where they can be used. All details to them, however,
can be found at `TSRef <http://typo3.org/documentation/document-
library/core-documentation/doc_core_tsref/current/>`_ , and not here.


.. toctree::
   :maxdepth: 5
   :titlesonly:
   :glob:

   Imgresource/Index
   Imagelinkwrap/Index
   Numrows/Index
   Select/Index
   Split/Index
   If/Index
   Typolink/Index
   Encapslines/Index
   FileLink/Index
   Parsefunc/Index
   Tags/Index
   Htmlparser/Index

