.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _stdwrap-recursively:

Modify the order
^^^^^^^^^^^^^^^^

There are basically two ways to obtain another execution order of
the stdWrap functions: First you can use stdWrap recursively. Second
you can use the stdWrap property "orderedStdWrap" to conveniently
provide a custom order.

Because **the stdWrap function can be called recursively**, it is
possible to change the execution order.

The function "prioriCalc" permits easy mathematical expressions. If
set to 1, the content is calculated; however, the calculations are
done from left to right (no mathematical precedence like "\*" before
"+", etc.). The following example looks, as if the content of field
"width" gets 20 added to it. ::

    10 = TEXT
    10.field = width   # Assumption: "width" is 100
    10.wrap = |+20
    10.prioriCalc = 1

But this is not the case! The result which will be rendered is:
"100+20". The function "prioriCalc" is executed *before* the function
wrap, and thus only calculates the result of "field" - the expression
"100". In order to get the result we anticipated, we have to make sure
that "field" *and "wrap"* are executed before "prioriCalc". This can be
achieved by using the following expression::

    10 = TEXT
    10.field = width   # Assumption: "width" is 100
    10.stdWrap.wrap = |+20
    10.prioriCalc = 1

We do not use "wrap" directly, but use it nested inside stdWrap. The
stdWrap function is executed after "field", but before "prioriCalc",
thus "100+20" is wrapped, and *after that* the function "prioriCalc"
is executed, resulting in the value "120".

With **orderedStdWrap** you can do the same, but more conveniently. ::

    10 = TEXT
    10.orderedStdWrap {
           10.field = width   # Assumption: "width" is 100
           20.wrap = |+20
           30.prioriCalc = 1
    }

Using :ref:`orderedStdWrap <t3tsref:stdwrap-orderedstdwrap>` we can
execute multiple stdWrap functions in a freely selectable order without
having to nest them inside other stdWrap calls. The execution order
inside orderedStdWrap is just defined by the numbers you provide. The
result will again be "120".

