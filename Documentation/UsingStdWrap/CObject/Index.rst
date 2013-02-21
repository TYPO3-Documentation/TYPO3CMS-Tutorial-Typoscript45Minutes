.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


cObject
^^^^^^^

The stdWrap parameter cObject can be used to replace the content with
a TypoScript object. This can be a `COA <http://typo3.org/documentation
/document-
library/references/doc_core_tsref/4.3.1/view/1/7/#id2518270>`_ , a
plugin or a text like in this example::

    10.typolink.title.cObject = TEXT
    10.typolink.title.cObject.value = Impressum
    10.typolink.title.cObject.lang.en = Imprint

