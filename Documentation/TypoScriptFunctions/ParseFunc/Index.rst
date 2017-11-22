.. include:: ../../Includes.txt


.. _function-parsefunc:
.. _parsefunc:

=========
parseFunc
=========

This function parses the main part of the content, i.e., the content which has
been entered in the Rich Text Editor. The function is responsible for the fact
that the content is not rendered exactly as it was entered in the RTE. Some
default parsing rules are implemented in the core, like parsing link tags via
:ref:`typolink` function.

You can also use :ts:`parseFunc` for your own processing. In the following
example, every occurrence of "COMP" is replaced by "My company name".

.. code-block:: typoscript

   page.stdWrap.parseFunc.short {
      COMP = My company name
   }

The various possibilities of changing the default behavior can be found by
using the TypoScript object browser. All possibilities of how parseFunc can
alter the rendering are be found in the
:ref:`TypoScript Reference <t3tsref:parsefunc>`.
