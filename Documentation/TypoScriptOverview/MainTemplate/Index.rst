.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _main-template:

The Main Template
^^^^^^^^^^^^^^^^^

The TypoScript code that is used to define how pages are rendered is
located in the "main" template. In this template the root level flag is
set.

.. figure:: ../../Images/RootlevelFlag.png
   :alt: The rootlevel flag in a template record.

When the frontend renders a page, TYPO3 searches along the page tree to
find a "main" template. Normally, there are additional templates
besides the "main" template. How these templates work together is easy
to see in the template analyzer. For now, we will assume we are only
using the "main" template.

TypoScript syntax is very straight-forward. On the left side, objects
and properties are defined. Properties are assigned values, and both
objects and properties can contain other objects. Objects properties
are defined using dot "." notation.

