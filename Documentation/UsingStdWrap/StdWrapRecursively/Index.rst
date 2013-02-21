.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _stdwrap-recursively:

Use stdWrap recursively
^^^^^^^^^^^^^^^^^^^^^^^

Because the `stdWrap function <http://typo3.org/documentation/document-library/references/doc_core_tsref/4.3.1/view/1/5/#id2359953>`_ 
can be called recursively, it is possible to change the execution
order.

The function "prioriCalc" permits easy mathematical expressions. If
set to 1, the content is calculated; however, the calculations are
done from left to right (no mathematical precedence like "\*" before
"+", etc.). The following example looks as if the content of field
"width" gets 20 added to it. ::

    10 = TEXT
    10.field = width   # Assumption: "width" is 100
    10.wrap = |+20
    10.prioriCalc = 1

This is not the case. The result which will be rendered is: "100+20".
The function "prioriCalc" is executed before the function wrap is
executed, and thus only calculates the result of "field" - the
expression "100". In order to get the result we anticipated, we have
to make sure that "field" and "wrap" are executed before "prioriCalc"
is executed. This can be achieved by using the following expression::

    10.stdWrap.wrap = |+20

The stdWrap function will be executed after "field", but before
"prioriCalc", thus "100+20" is wrapped, and after that the function
"prioriCalc" is executed, resulting in the value "120".

