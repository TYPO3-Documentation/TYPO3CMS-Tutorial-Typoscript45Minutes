.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _function-tags:
.. _tags:

tags
^^^^

The function "tags" is used in combination with :ref:`parseFunc
<parsefunc>` to define custom tags. For example, in the extension
"css\_styled\_content", a custom tag <LINK> is defined to create simple
links. ::

   tags {
           # Here the name of the new tag is defined.
           link = TEXT

           # Here is how the tag is processed and parsed.
           link {
                   current = 1
                   typolink {

                           parameter.data = parameters:allParams

                           extTarget = {$styles.content.links.extTarget}

                           target = {$styles.content.links.target}

                   }

                   parseFunc.constants = 1
           }
   }

This function is especially useful, if a certain type of element is
used by the editors very often, and we would like to make things
easier for them. We are able to provide a way that the editors do not
have to format things manually every time. Instead they can just enter
the tag, and the formatting is done automatically.

