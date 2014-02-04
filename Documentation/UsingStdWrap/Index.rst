.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../Includes.txt


.. _using-stdwrap:

Using stdWrap correctly
-----------------------

The function :ref:`stdWrap <t3tsref:stdwrap>` includes a wide variety
of functions and parameters. Some are trivial, the uses of others are
hard to find. Here we will commit ourselves to the basic principle and
highlight a few special functions and properties.

The :ref:`stdWrap <t3tsref:stdwrap>` property can only be used with an
object, if it is explicitly defined for that object in the
:ref:`TypoScript reference <t3tsref:start>`. For example the cObjects
have a property "stdWrap", which is of the type "stdWrap" and offers
stdWrap functionality. If we have a property of another type, e.g. of
the type "wrap", then this property does **not** have :ref:`stdWrap
<t3tsref:stdwrap>` properties. By default either a property named
"stdWrap" of type :ref:`stdWrap <t3tsref:stdwrap>` is presented, or a
property offers stdWrap, for example "string / :ref:`stdWrap
<t3tsref:stdwrap>`". ::

    10 = IMAGE
    10.stdWrap.typolink...

    20 = TEXT
    20.value = Hello World
    20.stdWrap.typolink...

These objects have a property :ref:`stdWrap <t3tsref:stdwrap>` of type
"stdWrap".


.. toctree::
   :maxdepth: 5
   :titlesonly:
   :glob:

   HeedTheOrder/Index
   ModifyTheOrder/Index
   TheDataType/Index
   Multilanguage/Index
   CObject/Index

