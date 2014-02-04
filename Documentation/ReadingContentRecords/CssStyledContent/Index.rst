.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _css-styled-content:

css\_styled\_content
^^^^^^^^^^^^^^^^^^^^

It would be tiresome to program this for every TYPO3 installation,
because the elements are the same, or have very similar functionality.
For this reason, TYPO3 offers "static templates". The current version
comes with the TYPO3 system extension "css\_styled\_content". It has a
meaningful definition for every existing type of content element.

The usage is comparably easy. The definitions are available as
tt\_content objects. ::

   page.10.renderObj < tt_content

This assignment also is the default configuration of the CONTENT
object. If the static template "css\_styled\_content" is available,
there is no need to explicitly set the parameter "renderObj".

So for every content element in TYPO3, there is a corresponding
definition in css\_styles\_content. In the object browser, it would
look like this:

.. figure:: ../../Images/ObjectBrowserSetupRoot.png
   :alt: Definitions in the Object Browser.

So it is comprehensible, which content element is configured in which
way. If a content element has to be configured completely differently,
then this can be done with tt\_content.internal identifier of the
content element. Here follows an example of how the standard properties
of the header can be overwritten::

    # Because TYPO3 saves everything in one big array, the properties that are not overwritten
    # are preserved and could result in strange behavior. That is why all old properties should be deleted.
    tt_content.header >

    # Every header will be rendered with h1 tags, independently from the properties in the content element.
    tt_content.header = TEXT
    tt_content.header.stdWrap.wrap = <h1>|</h1>
    tt_content.header.stdWrap.field = header

But, not only doesn't "renderObj" have to be recreated; the CONTENT
object itself is also already defined in css\_styled\_content.

