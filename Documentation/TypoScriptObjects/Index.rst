.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../Includes.txt


.. _typoscript-objects:
.. _cobjects:

TypoScript objects
------------------

The :ref:`TypoScript objects <t3tsref:cobjects>` are implemented in
TYPO3 by corresponding classes. For the various requirements while
rendering a web page, there are various objects. These objects have a
number of properties. For example, the object :ref:`IMAGE
<t3tsref:cobj-image>` has a method "border" and a method "titleText".
In the :ref:`TypoScript reference <t3tsref:start>`, we can look up what
kind of value each object expects. For "border", the data type
"integer" is expected. That means we can supply a number. Adding
several functions to it in our TypoScript (e.g. "border.color = red")
is therefore useless.

The object receives the parameter (as described above) in a PHP array
(e.g. $conf['border.']['color'] = 'red';). This array can contain an
arbitrary number of entries. Only those entries which are referenced
by the object will be used, though (e.g. $conf['border'] or
$conf['titleText']).

In the case "titleText", the data type is "string /stdWrap". This means
that both text (string) and methods of type :ref:`stdWrap
<t3tsref:stdwrap>` are allowed. Which properties stdWrap evaluates can
be looked up in the :ref:`section on stdWrap in TSref
<t3tsref:stdwrap>`. Hence, we are allowed to augment the method
"titleText" with various properties from stdWrap (e.g.
"titleText.field = header"). In doing so, the value of titleText will
be filled with standard text first, and afterwards the stdWrap
functions are executed.

So, it is not necessary to guess, which object will get manipulated in
that way; but, it suffices to look up this information in :ref:`the
TypoScript reference <t3tsref:start>`.

For the rendering of a web page, many more objects are used. The
challenge is to combine all of them artfully.

In the section ":ref:`Reading content records
<reading-content-records>`", we show how we can use the CONTENT object
to execute a query on the database and return the content of a page.
The object receives a list of content elements, which are rendered one
after the other (normally in sorting order).
Therefor, we use the object CASE to differentiate between the types of
the elements (CType) and render them differently.

It is absolutely necessary to know the various :ref:`TypoScript objects
<t3tsref:cobjects>` and :ref:`functions <t3tsref:functions>`.


.. toctree::
   :maxdepth: 5
   :titlesonly:
   :glob:

   ExecutingDatabaseQueries/Index
   RenderingContent/Index
   FurtherObjects/Index

