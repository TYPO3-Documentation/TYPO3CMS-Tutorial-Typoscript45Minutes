.. include:: ../../Includes.txt


.. _stdwrap-order:


==============
Heed the order
==============

The single most important thing to know about :code:`stdWrap` is that all
properties are parsed/executed exactly in the order in which they appear in the
:ref:`TypoScript Reference <t3tsref:stdwrap>`, no matter in which order you
have set them in your TypoScript template.

Let's consider this example:

.. code-block:: typoscript

   10 = TEXT
   10.value = typo3
   10.noTrimWrap = |<strong>Tool: |</strong>|
   10.case = upper

It results in the following:

.. code-block:: html

   <strong>Tool: TYPO3</strong>

The :code:`case` property is executed before the :code:`noTrimWrap` property.
Hence only "typo3" was changed to uppercase and not the "Tool:" with which it
is wrapped.
