.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../Includes.txt


.. _typoscript-objects:
.. _cobjects:

TypoScript objects
------------------

There are many different TypoScript objects for rendering a variety
of content elements in any given page according to need.
To each object there is a corresponding PHP class in the TYPO3 CMS.
Each object also has properties. For example,
the :ref:`IMAGE <t3tsref:cobj-image>` object has a "border" property
and a "titleText" property. In the :ref:`TypoScript Reference (TSref) <t3tsref:start>`,
we can find a complete list of available objects and all their properties,
complete with the type of data that each object accepts.
Adding arbitrary properties or erroneous values will not work.

The object receives the parameter (as described above) in a PHP array
(e.g. :code:`$conf['border.']['color'] = 'red';`). This array can contain an
arbitrary number of entries. Only those entries which are referenced
by the object will be used, though (e.g.
:code:`$conf['border']` or :code:`$conf['titleText']`).

In the case "titleText", the data type is "string /stdWrap". This means
that both text (string) and methods of the :ref:`stdWrap <t3tsref:stdwrap>`
type are allowed. Looking up the :ref:`section on stdWrap in TSref <t3tsref:stdwrap>`
will tell you which properties stdWrap evaluates.
Hence, we are allowed to augment the method "titleText" with various properties from stdWrap (e.g.
:code:`titleText.field = header`). In doing so, the value of titleText will
be filled with standard text first, and, after that,  the stdWrap
functions are executed.

So, it is not necessary to guess, which object will get manipulated in
that way; but, it suffices to look up this information in
:ref:`the TypoScript reference <t3tsref:start>`.

Many more objects are used for the rendering of a web page. The
challenge is to artfully combine all of them.

In the section :ref:`Reading content records <reading-content-records>`,
we show how we can use the :ref:`CONTENT <t3tsref:cobj-content>` object
to query to database and return the content of a page.
The object receives a list of content elements, which are rendered one
after the other (normally in sorting order).
Therefore, we use the object :ref:`CASE <t3tsref:cobj-case>` to differentiate between
the different element type (CType) and render them accordingly.

It is absolutely necessary to know the various
:ref:`TypoScript objects <t3tsref:cobjects>` and :ref:`functions <t3tsref:functions>`.


.. toctree::
   :maxdepth: 5
   :titlesonly:
   :glob:

   ExecutingDatabaseQueries/Index
   RenderingContent/Index
   FurtherObjects/Index

