.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _stdwrap-order:

Heed the order
^^^^^^^^^^^^^^

An important limitation should be highlighted:

**The single functions are executed in the order specified by the** `
**reference**  <http://typo3.org/documentation/document-library/core-documentation/doc_core_tsref/current/>`_  **.**

If we don't pay attention to this fact the results might look
different from what we expected. ::

    10 = TEXT
    10.value = Hello World
    10.case = upper
    10.field = header # assuming the header contains "typo3" (small case characters)
    10.stdWrap.wrap = <strong>|</strong>

    # results in the following:
    <STRONG>TYPO3</STRONG>

The following happens in this example: First, the value of the TEXT
object is set to "Hello world". We know that the TypoScript
configuration is stored in an array. The sorting in this array is not
like the sorting in TypoScript. The sorting in the array is
constrained by definitions of the ordering of stdWrap. This order is
mirrored by the reference. After a short look into the TSref it should
be clear that, first, "field" is processed, thereafter stdWrap (and
with it "stdWrap.wrap"), and in the end, "case".

