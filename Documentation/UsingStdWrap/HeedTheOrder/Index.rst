.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _stdwrap-order:

Heed the order
^^^^^^^^^^^^^^

An important limitation should be highlighted:

**Note:** The single functions are executed in the order specified by
the :ref:`TypoScript reference <t3tsref:start>`!

If we did not pay attention to this fact, the results might easily
look different from what we expected. ::

    10 = TEXT
    10.stdWrap.field = header # assuming the header contains "typo3" (small case characters)
    10.stdWrap.wrap = <strong>|</strong>
    10.stdWrap.case = upper

This results in the following::

    <strong>TYPO3</strong>

The following happens in this example: First, the value of the TEXT
object is imported from the field "header". We know that the TypoScript
configuration is `stored in an array <typoscript-array>`. The sorting
in this array is not necessarily the same as the sorting in our
TypoScript. Instead, the sorting in the array is constrained by
definitions of the ordering of stdWrap. This order is mirrored by the
TypoScript reference.

After a short :ref:`look into the TSref <t3tsref:stdwrap>` it should be
clear that, first, "field" is processed, thereafter "case", and in the
end, "wrap". This order is the reason, why the words of the tag "strong"
themselves are *not* uppercased.

