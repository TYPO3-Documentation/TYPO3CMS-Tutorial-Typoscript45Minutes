.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _function-htmlparser:
.. _htmlparser:

HTMLparser
^^^^^^^^^^

The HTML parser defines how content is processed. Normally, it is used
as a subfunction of parseFunc. For example, we could define that all
links will be set with an absolute value (for example, for a
newsletter)::

   page.stdWrap.HTMLparser = 1
   page.stdWrap.HTMLparser {
           keepNonMatchedTags = 1

           # Here we define the domain, which will be placed in front
           # of the relative path.
           tags.a.fixAttrib.href.prefixRelPathWith = http://www.example.com/

           # All links without a target should have the target "_blank".
           tags.a.fixAttrib.target.default = _blank
   }

The function HTMLparser is extremely mighty, because every content can
be altered before it is rendered. E.g. links are internally stored as
follows: <link http://www.typo3.org/>Linktext</link>. We can also
define custom tags. Custom tags can be defined in all fields - also in
headlines -, on which a parser has been defined.

The following example allows the <u> tag in headlines. To do that the
default definition from "css\_styled\_content" will be altered: The
function htmlSpecialChars will be deactivated, so the <u> remains
untouched. Thereafter, the parseFunc function is used, and defined that
aside the tag "u", no other tags will be allowed. Thus, all tags apart
from the <u> will be removed. ::

   # In the headline the <u> tag shall be allowed.
   # Apart from that all elements have to be parsed as usual.
   lib.stdheader.10.setCurrent.htmlSpecialChars = 0
   lib.stdheader.10.setCurrent.parseFunc {
     allowTags = u
     denyTags = *
     constants = 1
     nonTypoTagStdWrap.HTMLparser = 1
     nonTypoTagStdWrap.HTMLparser {
       keepNonMatchedTags = 1
       htmlSpecialChars = 2
       allowTags = u
       removeTags = *
     }
   }

This example once again shows how important the stdWrap function
actually is. The function setCurrent is of Type string /stdWrap, and
thus allows the usage of parseFunc.

