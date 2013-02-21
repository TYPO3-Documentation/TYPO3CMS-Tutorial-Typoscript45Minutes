.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _stdwrap-multilanguage:

Multilanguage functionality
^^^^^^^^^^^^^^^^^^^^^^^^^^^

`stdWrap <http://typo3.org/documentation/document-
library/references/doc_core_tsref/4.3.1/view/1/5/#id2359953>`_ offers
a property "lang" with which it is possible to translate simple texts
which are implemented via TypoScript on a page. ::

    10 = TEXT
    10.value = Imprint
    10.lang.de = Impressum
    10.typolink.parameter = 10

However, texts like these are hard to translate by external editors.
Especially with unknown languages, this can become a challenge.

For this case, it is best to handle the translations with constants.
These can be placed together at a specific place, and implemented into
TypoScript. ::

    # Constants
    text.imprint = Imprint
    text.de.imprint = Impressum

    # Setup
    10 = TEXT
    10.value = {$text.imprint}
    10.lang.en = {$text.en.imprint}
    10.typolink.parameter = 10

This way the translation is not depending on the TS configuration of
the item.

