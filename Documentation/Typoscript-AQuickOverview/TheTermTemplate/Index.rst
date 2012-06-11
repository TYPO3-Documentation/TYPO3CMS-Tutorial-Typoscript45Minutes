.. include:: Images.txt

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


The term template
^^^^^^^^^^^^^^^^^

The term template has a duplicate meaning in TYPO3. On the one hand,
there is the HTML template which serves as the skeletal structure in
which the content will be rendered. On the other hand, there is the
TypoScript template which can be created in the pages.

Common mistakes which can be made with TypoScript templates can look
like this:

|img-3|

"No TypoScript template found": This warning appears if no template
can be found which has the root level flag enabled in the page tree.

|img-4| "The page is not configured": This warning appears if the root level
flag is enabled, but no PAGE Object can be found.

The following code suffices to circumvent this warning:

::

   page = PAGE
   page.10 = TEXT
   page.10.value = Hello World

