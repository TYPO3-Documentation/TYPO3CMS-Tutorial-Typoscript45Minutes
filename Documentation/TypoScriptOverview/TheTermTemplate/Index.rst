.. include:: /Includes.rst.txt


.. _template:
.. _the-term-template:

=================
The term template
=================

The term template has a double meaning in TYPO3 CMS. On the one hand,
there is the *HTML template file*, which serves as the skeletal
structure in which the content, provided by the CMS,
will be rendered. On the other hand, there is the *TypoScript template*,
which is created in the :guilabel:`Site Management > TypoScript` module in the TYPO3 CMS
Backend and can exist on any page.

..  versionchanged:: 12.3
    The Template module moved to another section and changed its name to
    "TypoScript" in TYPO3 version 12.

    .. image:: /Images/ManualScreenshots/ModuleNameTypoScript.png
       :alt: Module name "TypoScript"
       :class: with-shadow

The :doc:`Sitepackage Tutorial <t3sitepackage:Index>` shows how the two are related
together. This manual is purely about TypoScript templates.


.. _troubleshooting:

Troubleshooting
===============

Common mistakes made with TypoScript templates can cause a message like this:

.. figure:: /Images/ManualScreenshots/NoTypoScriptTemplateFoundDebuggingOff.png
   :alt: Error message "No TypoScript template found! Without debug mode"

If you turn on the :ref:`debug mode <t3coreapi:troubleshooting-debug-mode>`
you will get more detailed information:

.. figure:: /Images/ManualScreenshots/NoTypoScriptTemplateFound.png
   :alt: Error message "No TypoScript template found!"

`No TypoScript template found`: This warning appears if no template,
with the `root level` flag enabled, is found in the page tree.

.. figure:: /Images/ManualScreenshots/ThePageIsNotConfigured.png
   :alt: Error message "The page is not configured!"


`The page is not configured! [type=0][]. This means that there is no TypoScript
object of type PAGE with typeNum=0 configured.`: This warning appears if the
root level flag of a template in the page tree is enabled (i.e. this template
is used), but no :ref:`PAGE <t3tsref:page>` Object can be found.

The following TypoScript setup code is enough to remove this warning::

   page = PAGE
   page.10 = TEXT
   page.10.value = Hello World

Do not worry about this code for now, it will be explained later.
