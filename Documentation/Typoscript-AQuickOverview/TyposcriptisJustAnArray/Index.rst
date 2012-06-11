

.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. ==================================================
.. DEFINE SOME TEXTROLES
.. --------------------------------------------------
.. role::   underline
.. role::   typoscript(code)
.. role::   ts(typoscript)
   :class:  typoscript
.. role::   php(code)


TypoScriptis just an array
^^^^^^^^^^^^^^^^^^^^^^^^^^

TypoScript is just stored in a PHP array, internally. It is used and
evaluated by various classes according to object types.

::

   page = PAGE
   page.10 = TEXT
   page.10.value = Hello World
   page.10.wrap = <h2>|</h2>

will be converted to the following PHP array

::

   $data['page'] = 'PAGE';
   $data['page.'][10] = 'TEXT';
   $data['page.']['10.']['value'] = 'Hello World';
   $data['page.']['10.']['wrap'] = '<h2>|</h2>';
   

On evaluation, the object " `PAGE <http://wiki.typo3.org/TSref/PAGE>`_
" will be created first, and the parameter $data['page.'] will be
assigned. The object " `PAGE <http://wiki.typo3.org/TSref/PAGE>`_ "
will then search for all properties which define it. In this case, it
will just find a numeric entry "10" which has to be evaluated. A new
object " `TEXT <http://wiki.typo3.org/TSref/TEXT>`_ " with the
parameter $data['page.']['10.'] will be created. The object " `TEXT
<http://wiki.typo3.org/TSref/TEXT>`_ " only knows the parameter
"value", so it will set its content accordingly. All further
parameters will be passed to the function stdWrap. (That's how " `TEXT
<http://wiki.typo3.org/TSref/TEXT>`_ " is implemented. We will
elaborate on stdWrap later). There the property 'wrap' is known, and
the text "Hello world" will be inserted at the pipe (\|) position and
returned.

This relationship is important to understand the behavior of
TypoScript in many cases. If, for example, the TypoScript is extended
with the following line:

::

   page.10.myFunction = Magic!

the entry will be taken into the PHP array:

::

   $data['page.']['10.']['myFunction'] = 'Magic!';

However, neither the object `TEXT <http://wiki.typo3.org/TSref/TEXT>`_
nor the function stdWrap knows the property "myFunction".
Consequently, the entry will have no effect.

No semantic error checking is done. This should especially be
considered whilst troubleshootin

