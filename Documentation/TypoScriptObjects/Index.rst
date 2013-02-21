.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../Includes.txt


.. _typoscript-objects:
.. _cobjects:

TypoScript Objects
------------------

The :ref:`TypoScript objects <t3tsref:cobjects>` are implemented in TYPO3 by corresponding
classes. For the various requirements while rendering a web page,
there are various objects. These objects have a number of properties.
For example, the object IMAGE has a method wrap and a method
titleText. In the TypoScript reference, we can look up what kind of
value this object expects. For wrap, a data type wrap is being
expected - meaning a text which is separated by a pipe (\|). To add
several functions (e.g., "wrap.crop = 100") is therefore useless.

The object receives the parameter (as described above) in a PHP array
(e.g., $conf['wrap.']['crop']='100';). This array can contain an
arbitrary number of entries. Only those entries which are referenced
by the object will be used, though (e.g., $conf['wrap'] or
$conf['titleText']).

In the case "titleText", the data type is "string / stdWrap". This
means that both text (string) and a method of type stdWrap are
allowed. Which property stdWrap evaluates can be looked up in the
stdWrap. Hence, we are allowed to augment the method "titleText" with
various properties from stdWrap (e.g., titleText.field = header). In
doing so, the value of titleText will be filled with standard text,
and afterward the stdWrap functions are executed.

So, it is not necessary to guess which object will get manipulated in
that way; but, it suffices to look up this information in the
reference.

For the rendering of a web page, many more objects are being used. The
challenge is to combine all of them artfully.

In the section "Reading content records", we show how we can use the
CONTENT object to execute a query on the database and return the
content of a page. The object receives a list of content elements
which are created one after the other (normally in sorting order).
Therefore, we use the object CASE to differentiate the type of the
elements (CType) and render them differently.

It is absolutely necessary to know the various TypoScript objects and
functions.


.. toctree::
   :maxdepth: 5
   :titlesonly:
   :glob:

   ExecutingDatabaseQueries/Index
   RenderingContent/Index
   FurtherObjects/Index

