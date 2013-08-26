.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../Includes.txt


.. _using-css-styled-content:

Using css\_styled\_content
--------------------------

We already saw that we can write the definitions for the different
content elements of TYPO3, ourselves. But css\_styled\_content relieves
us of having to write them ourselves; it comes with more than 2000
lines of TypoScript code containing definitions for each type of
content element.

It is rewarding - even if it doesn't seem to make sense in the
beginning - to have a good look at TypoScript. In TYPO3, we have to be
at the page, which has the TypoScript template with the TypoScript code
in the Setup field. Then, in the module "Template", we choose "Template
Analyzer" from the selector box on top of the window.

A list with active and integrated TypoScript templates appears. These
are evaluated by TYPO3 from top to bottom, and joined together into
one configuration array.

With a click on "EXT:css\_styled\_content/static/", the contents of
that template will be displayed. First, the constants will appear, and
then the setup TypoScript.

The extension css\_styled\_content will add HTML elements with many
classes to the rendering of a page. They are used by TYPO3 to display
things in a structured way, e.g. images at their selected position like
next to text, the link to top, etc. This also has the advantage that it
is not necessary to enter different classes by hand, if you want to
modify the styling. It suffices to find out which HTML element has
which class, and to add CSS styles for that class. ::

   <div class="csc-textpic-imagewrap">...

The descriptions of the classes are simple and - once you got familiar
with the TYPO3 internals - intuitive. All classes start with "csc";
this stands for "css\_styled\_content". In the example, this is
followed by "textpic", which stands for the TypoScript element
"textpic" (which is used to render content elements of the type "text
with image"). "imagewrap" suggests that the DIV container wraps around
an image.

What is happening in detail can be understood by making an empty page
with only one element, and then checking out the generated source code
of that page.

For example, headlines are normally enumerated so that the first
headline can be handled specifically. For HTML tables, the classes
"odd" and "even" are inserted so that it is easy to color table rows
differently. In the same manner, the table columns can be handled
individually.

For HTML purists, it means that many CSS classes will be inserted,
which possibly are not needed for a certain site at all. One could get
rid of those by overwriting the unneeded definitions of the
css\_styled\_content extension. However, for beginners that is not
recommended.


