.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _stdwrap-multilanguage:

Multilanguage functionality
^^^^^^^^^^^^^^^^^^^^^^^^^^^

stdWrap offers a property ":ref:`lang <t3tsref:stdwrap-lang>`" with
which it is possible to translate simple texts which are implemented
on a page via TypoScript. ::

    10 = TEXT
    10.value = Imprint
    10.stdWrap.lang.de = Impressum
    10.stdWrap.typolink.parameter = 10

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
    10.stdWrap.lang.de = {$text.de.imprint}
    10.stdWrap.typolink.parameter = 10

This way, the place of the translation is not depending on the
TypoScript configuration of the item.

