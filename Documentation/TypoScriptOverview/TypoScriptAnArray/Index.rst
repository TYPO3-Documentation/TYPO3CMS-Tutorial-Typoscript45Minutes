.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _typoscript-array:

TypoScript is just an array
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Internally, TypoScript is just stored in a PHP array. It is used and
evaluated by various classes according to object types. ::

   page = PAGE
   page.10 = TEXT
   page.10.value = Hello World
   page.10.stdWrap.wrap = <h2>|</h2>

will be converted to the following PHP array ::

   $data['page'] = 'PAGE';
   $data['page.']['10'] = 'TEXT';
   $data['page.']['10.']['value'] = 'Hello World';
   $data['page.']['10.']['stdWrap.']['wrap'] = '<h2>|</h2>';


On evaluation, the object ":ref:`PAGE <t3tsref:page>`" will be created
first, and the parameter $data['page.'] will be assigned. The object
":ref:`PAGE <t3tsref:page>`" will then search for all properties, which
define it. In this case, it will just find a numeric entry "10", which
has to be evaluated. A new object ":ref:`TEXT <t3tsref:cobj-text>`"
with the parameter $data['page.']['10.'] will be created. The object
":ref:`TEXT <t3tsref:cobj-text>`" knows the parameters "value" and
"stdWrap". It will set the content of "value" accordingly. The
parameters from "stdWrap" will be passed to the function stdWrap.
(That's how ":ref:`TEXT <t3tsref:cobj-text>`" is implemented. We will
elaborate on stdWrap later). There the property 'wrap' is known, and
the text "Hello world" will be inserted at the pipe (\|) position and
returned.

This relationship is important to understand the behavior of
TypoScript in many cases. If, for example, the TypoScript is extended
with the following line::

   page.10.myFunction = Magic!

this entry will be added to the PHP array::

   $data['page.']['10.']['myFunction'] = 'Magic!';

However, the object :ref:`TEXT <t3tsref:cobj-text>` does not know the
property "myFunction". Consequently, the entry will have no effect.

No semantic error checking is done. If you define an object or
properties, which do not exist, you will not see an error message.
Instead the according lines of TypoScript just do not do anything. This
should especially be considered whilst troubleshooting.

