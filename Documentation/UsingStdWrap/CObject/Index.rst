.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _stdwrap-cobject:

cObject
^^^^^^^

The stdWrap parameter "cObject" can be used to replace the content with
a TypoScript object. This can be a :ref:`COA <t3tsref:cobj-coa>`, a
plugin or a text like in this example::

    10.typolink.title.cObject = TEXT
    10.typolink.title.cObject.value = Impressum
    10.typolink.title.cObject.lang.en = Imprint

