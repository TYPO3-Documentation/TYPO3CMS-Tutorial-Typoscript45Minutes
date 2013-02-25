.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _why-typoscript:

Why TypoScript?
^^^^^^^^^^^^^^^

Strictly speaking, TypoScript is a configuration language. We cannot
program with it, but we can configure many aspects of a TYPO3 site
very comprehensively. With TypoScript, we define the rendering of the
website, including navigation, some fixed content, and how individual
content elements are rendered on a page.

TYPO3 is a content management system that clearly separates content
and design. TypoScript is the glue that joins these two together again.
TypoScript reads content which is stored in the database, prepares it
for display and then renders it on the frontend.

To render a website, we only need to define what content to display and
how it will be rendered.

- The "what" is controlled by the backend - where pages and content
  are generated.

- The "how" is controlled by TypoScript.

With TypoScript we define how the individual content elements are
rendered in the frontend. For example, we use TypoScript to add a <div>
tag to an element, or the <h1> tag to a headline.

