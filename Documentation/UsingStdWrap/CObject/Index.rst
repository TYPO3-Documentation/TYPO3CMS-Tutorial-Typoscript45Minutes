.. include:: /Includes.rst.txt


.. _stdwrap-cobject:

cObject
^^^^^^^

The `stdWrap` property ":ref:`cObject <t3tsref:stdwrap-cobject>`" can be
used to replace the content with a TypoScript object. This can be a
:ref:`COA <t3tsref:cobj-coa>`, a plugin or a text like in this
example::

   10.typolink.title.cObject = TEXT
   10.typolink.title.cObject {
      value = Copyright
      case = upper
   }

