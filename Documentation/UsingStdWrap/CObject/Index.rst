.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _stdwrap-cobject:

cObject
^^^^^^^

The stdWrap parameter ":ref:`cObject <t3tsref:stdwrap-cobject>`" can be
used to replace content with a TypoScript object. This can be a
:ref:`COA <t3tsref:cobj-coa>`, a plugin or a text like in this
example::

    10.typolink.title.cObject = TEXT
    10.typolink.title.cObject.value = Imprint
    10.typolink.title.cObject.lang.de = Impressum

