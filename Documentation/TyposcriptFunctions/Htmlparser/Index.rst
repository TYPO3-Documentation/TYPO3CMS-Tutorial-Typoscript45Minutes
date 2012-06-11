

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


HTMLparser
^^^^^^^^^^

The HTML parser defines how content is processed. Normally, it's used
as a subfunction of parseFunc. For example, we could define that all
links will be set with an absolute value (for example, for a
newsletter):

::

   page.stdWrap.HTMLparser = 1
   page.stdWrap.HTMLparser {
         keepNonMatchedTags=1
   
           # Here we define the domain which will be placed in front of the relative path
         tags.a.fixAttrib.href.prefixRelPathWith=http://www.example.com/
   
           # All links without a target will receive a target = _blank
         tags.a.fixAttrib.target.default=_blank
   }

The function HTMLparser is extremely mighty, because every content can
be altered before it's rendered. We could define custom tags - e.g.,
internal links are stored as follows: <link `http://www.typo3.org/
<http://www.typo3.org/>`_ >Linktext</link> thus a custom tag is being
used. This custom tag can be defined in all fields - also headlines -
on which a parser has been defined.

The following example allows the <u> tag in headlines. The default
definition from "css\_styled\_content" will be altered. The function
htmlSpecialChars will be deactivated, so the <u> remains untouched.
Thereafter, the parseFunc function is used, and defined that aside the
tag "u", no other tags will be allowed. Thus, all tags apart from the
<u> will be removed.

::

   # In the headline the <u> tag shall be allowed
   # Apart from that all elements have to be parsed as usual
   lib.stdheader.10.setCurrent.htmlSpecialChars = 0
   lib.stdheader.10.setCurrent.parseFunc {
     allowTags = u
     denyTags = *
     constants=1
     nonTypoTagStdWrap.HTMLparser = 1
     nonTypoTagStdWrap.HTMLparser {
       keepNonMatchedTags=1
       htmlSpecialChars = 2
       allowTags = u
       removeTags = *
     }
   }

This example once again shows how important the stdWrap function
actually is. The function setCurrent is of Type string/stdWrap, and
thus allows the usage of parseFunc.

