

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


tags
^^^^

The function "tags" is used in combination with parseFunc to get
custom tags. For example, in the extension "css\_styled\_content", a
custom tag <LINK> is defined to create simple links.

::

   tags {
           # Here the name of the new tag is defined
           link = TEXT
   
           # here how the tag is processed/parsed
           link {
                   current = 1
                   typolink {
   
                           parameter.data = parameters:allParams
   
                           extTarget = {$styles.content.links.extTarget}
   
                           target = {$styles.content.links.target}
   
                   }
   
                   parseFunc.constants=1
           }
   }

This function is especially useful, if a certain type of element is
being used very often by the editors, and we would like to make things
easier for them. We are able to provide a way that the editors do not
have to format this manually every time, they just have to enter the
tag, and the formatting is done automatically.

