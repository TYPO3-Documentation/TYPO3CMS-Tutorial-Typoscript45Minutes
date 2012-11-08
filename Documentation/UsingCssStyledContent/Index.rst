.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../Includes.txt


Using css\_styled\_content
--------------------------

We already saw that we can define the different content elements of
TYPO3, ourselves. But css\_styled\_content reduces the amount of work,
with about 2000 lines of TypoScript.

It is rewarding - even if it doesn't make sense in the beginning - to
have a good look at TypoScript. In TYPO3, we have to be at the page
which has the setup template. Then, in the module "Template", we
choose "Template Analyzer" from the selector box on top of the window.

A list with active and integrated TypoScript templates appears. These
are evaluated from top to bottom by TYPO3, and joined together into
one configuration array.

With a click on "EXT:css\_styled\_content/static/", the contents of
that template will be displayed. First, the constants will appear, and
then the setup TypoScript.

The extension css\_styled\_content will add many classes in HTML
elements. This has the advantage that it's not necessary to enter all
classes by hand. It suffices to find out which HTML element has which
class, and to add CSS styles to it. ::

   Example:
   <div class="csc-textpic-imagewrap">...

The descriptions of the classes are simple and - if the TYPO3
internals are familiar - intuitive. All classes start with "csc"; this
stands for "css\_styled\_content". In the example, this is followed by
"textpic", which stands for the TypoScript element "textpic" (text
with image). "imagewrap" suggests that the DIV container wraps around
an image.

What's happening in detail can be understood by making an empty page
with only one element, and then checking out the generated source code
of that page.

For example, headlines are normally enumerated so that the first
headline can be handled specifically. For HTML tables, the classes
"odd" and "even" are inserted so that it's easy to color table rows
differently. In the same manner, the table columns can be handled
individually.

For the HTML purists, it means that many css classes will be inserted
which are obsolete. In order to get rid of those, one needs to edit a
lot of the css\_styled\_content extension.


