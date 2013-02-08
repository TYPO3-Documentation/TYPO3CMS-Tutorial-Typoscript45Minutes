.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../Includes.txt


using `stdWrap <http://typo3.org/documentation/document-library/references/doc_core_tsref/4.3.1/view/1/5/#id2359953>`_ correctly
--------------------------------------------------------------------------------------------------------------------------------

The function `stdWrap <http://typo3.org/documentation/document-
library/references/doc_core_tsref/4.3.1/view/1/5/#id2359953>`_
includes a wide variety of functions and parameter. Some are trivial,
the use of some are hard to find. Here we will commit ourselves to the
basic principle and highlight a few special functions/properties.

The `stdWrap <http://typo3.org/documentation/document-
library/references/doc_core_tsref/4.3.1/view/1/5/#id2359953>`_
-property can only be used if it is defined explicitly. Most cObjects
have a property "stdWrap", which is of the type "stdWrap" and
offers stdWrap functionality. If we have a property of another type,
e.g. of the type "wrap", then this property does **not** have `stdWrap
<http://typo3.org/documentation/document-
library/references/doc_core_tsref/4.3.1/view/1/5/#id2359953>`_
-properties. By default either a property of type `stdWrap
<http://typo3.org/documentation/document-
library/references/doc_core_tsref/4.3.1/view/1/5/#id2359953>`_ is
presented or a property offers for example "string/ `stdWrap
<http://typo3.org/documentation/document-
library/references/doc_core_tsref/4.3.1/view/1/5/#id2359953>`_ ". ::

    10 = IMAGE
    10.stdWrap.typolink...

The object has a property `stdWrap <http://typo3.org/documentation
/document-
library/references/doc_core_tsref/4.3.1/view/1/5/#id2359953>`_ of type
`stdWrap <http://typo3.org/documentation/document-
library/references/doc_core_tsref/4.3.1/view/1/5/#id2359953>`_ . ::

    10 = TEXT
    10.value = Hello World
    10.typolink …

The object TEXT in contrast does **not** have a property "stdWrap", under
which the stdWrap functions would be available. Instead the cObject
TEXT offers the stdWrap functions on the very rootlevel of the object
(as shown with the property "typolink" above). This is non-standard!


.. toctree::
   :maxdepth: 5
   :titlesonly:
   :glob:

   HeedTheOrder/Index
   UseStdwrapRecursively/Index
   TheDataType/Index
   LangMultilanguageFunctionality/Index
   Cobject/Index

