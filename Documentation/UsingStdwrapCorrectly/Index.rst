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
-property can only be used if its defined explicitly. If we have a
property of type "wrap" then there are no `stdWrap
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

    10 = HTML
    10.value = Hello World
    10.value.typolink …

The object HTML in contrast has a property of type string/ `stdWrap
<http://typo3.org/documentation/document-
library/references/doc_core_tsref/4.3.1/view/1/5/#id2359953>`_ . We
can add a string and in addition we can use `stdWrap
<http://typo3.org/documentation/document-
library/references/doc_core_tsref/4.3.1/view/1/5/#id2359953>`_
properties.


.. toctree::
   :maxdepth: 5
   :titlesonly:
   :glob:

   HeedTheOrder/Index
   UseStdwrapRecursively/Index
   TheDataType/Index
   LangMultilanguageFunctionality/Index
   Cobject/Index

