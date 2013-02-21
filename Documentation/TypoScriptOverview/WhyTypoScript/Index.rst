.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _why-typoscript:

Why TypoScript?
^^^^^^^^^^^^^^^

Strictly speaking, TypoScript is a configuration language. We cannot
program with it, but we can configure many things very comprehensively
with it. With TypoScript, we define the rendering of the website. We
define our navigation, some fixed content, but also how individual
content elements will be rendered on a page.

TYPO3 is a content management system with the goal to separate content
and design. TypoScript is the glue which joins those together again.
The content which is located in the database is read and prepared by
TypoScript, and rendered on the frontend.

To render a website, we only have to define what and how content will
be rendered.

- The "what" is controlled by the backend - there the pages and content
  are generated.

- The "how" is controlled by TypoScript.

With TypoScript we define how the individual content elements will be
rendered in the frontend, if, for example, a DIV container wraps the
element, or if the header <h1> will be integrated.

The TypoScript which defines how the pages are being rendered is
located in the "main" template. In this the root level flag is set.

.. figure:: ../../Images/RootlevelFlag.png
   :alt: The rootlevel flag in a template record.

If the frontend has to render a page, TYPO3 searches along the page
tree to find a "main" template. Normally, there are some more
templates aside the "main" template. How these play together can be
seen nicely in the template analyzer. For now, we assume that we only
have one template.

The TypoScript syntax is very easy. On the left side, objects and
their properties are defined which will get certain values assigned to
them. Objects and properties (which in turn can hold objects as well)
are separated by a dot ".".

