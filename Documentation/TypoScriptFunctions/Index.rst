.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../Includes.txt


.. _TS-functions:

TypoScript functions
--------------------

TypoScript functions are used to change and adjust the output of
content elements. The most popular function is the standard wrap,
better known as stdWrap. Whether an object implements a certain
function or not, is shown in TSref in the column "data type". Here is
an extract of the cObject IMAGE from TSref:


.. ### BEGIN~OF~TABLE ###

.. container:: table-row

   Property
         file

   Data type
         imgResource

   Description
         [...]

.. container:: table-row

   Property
         imageLinkWrap

   Data type
         boolean /->imageLinkWrap

   Description
         [...]

.. container:: table-row

   Property
         if

   Data type
         ->if

   Description
         [...]

.. container:: table-row

   Property
         altText

         titleText

   Data type
         string /stdWrap

   Description
         [...]

.. ###### END~OF~TABLE ######


[Example:(cObject).IMAGE]

The first entry in this example (property "file") tells us that "file"
is of the data type "imgResource". This means that we can use the
:ref:`imgResource functions <t3tsref:imgresource>` on the file
property.

Sometimes functions are - for better recognition - marked with an
arrow (like ->if).

If there are multiple entries separated by a slash, it means that you
have various possibilities to use that element. In the example above,
you can for example see this with titleText and altText. Both can be
either plain string or stdWrap. So, you can enter a plain string and do
nothing more; or you can adjust and change your string by using stdWrap
features on it; or you can leave the string empty all together and
generate the content with stdWrap only.

Some important and frequently used functions are presented in the
following subsections. This chapter is about introducing those
functions, and where they can be used. All details, however, can be
found in :ref:`TSref <t3tsref:functions>`, and not here.


.. toctree::
   :maxdepth: 5
   :titlesonly:
   :glob:

   ImgResource/Index
   ImageLinkWrap/Index
   NumRows/Index
   Select/Index
   Split/Index
   If/Index
   Typolink/Index
   EncapsLines/Index
   Filelink/Index
   ParseFunc/Index
   Tags/Index
   HTMLparser/Index

