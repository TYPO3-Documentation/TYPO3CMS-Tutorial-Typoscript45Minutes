.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _cobjects-rendering-content:

Objects rendering content
^^^^^^^^^^^^^^^^^^^^^^^^^

- `IMAGE <http://typo3.org/documentation/document-
  library/references/doc_core_tsref/4.3.1/view/1/7/#id2518630>`_ the
  rendering of an image ::

   lib.logo = IMAGE
   lib.logo {
     file = fileadmin/logo.gif
     file.width = 200
     stdWrap.typolink.parameter = 1
   }

- lib.logo holds the logo with a width of 200 pixel and is being linked
  with the page with PID 1.

- `TEXT <http://typo3.org/documentation/document-
  library/references/doc_core_tsref/4.3.1/view/1/7/#id2518196>`_ for the
  rendering of standard text or the content of fields. The TEXT-object
  implements the `stdWrap <http://typo3.org/documentation/document-
  library/references/doc_core_tsref/4.3.1/view/1/5/#id2359953>`_
  functionality on the very rootlevel of the object. This is non-standard! ::

   lib.test1 = TEXT
   lib.test1.field = uid

- `FILE <http://typo3.org/documentation/document-
  library/references/doc_core_tsref/4.3.1/view/1/7/#id2518497>`_ imports
  the content of a file directly

- `TEMPLATE <http://typo3.org/documentation/document-
  library/references/doc_core_tsref/4.3.1/view/1/7/#id2526304>`_
  replaces a marker with content in a template ::

   page.10 = TEMPLATE
   page.10 {
     template = FILE
     template.file = fileadmin/test.tmpl
     subparts {
       HELLO = TEXT
       HELLO.value = replaces the content in between the markers ###HELLO### and ###HELLO###
     }
     marks {
       Test = TEXT
       Test.value = the marker Test will be replaced by this text
     }
     workOnSubpart = DOCUMENT
   }

- `MULTIMEDIA <http://typo3.org/documentation/document-
  library/references/doc_core_tsref/4.3.1/view/1/7/#id2526661>`_ renders
  multimedia objects

- `IMGTEXT <http://typo3.org/documentation/document-
  library/references/doc_core_tsref/4.3.1/view/1/7/#id2522382>`_ allows
  to generate images inline with text. Is used for the content element
  "text with image"

- `FORM <http://typo3.org/documentation/document-
  library/references/doc_core_tsref/4.3.1/view/1/7/#id2523709>`_
  generates an HTML-form

