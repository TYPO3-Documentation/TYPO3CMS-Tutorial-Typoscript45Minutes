.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _cobjects-rendering-content:

Objects rendering content
^^^^^^^^^^^^^^^^^^^^^^^^^

- :ref:`IMAGE <t3tsref:cobj-image>` for the rendering of an image. ::

   lib.logo = IMAGE
   lib.logo {
     file = fileadmin/logo.gif
     file.width = 200
     stdWrap.typolink.parameter = 1
   }

- lib.logo holds the logo with a width of 200 pixel and is linked with
  the page with PID 1.

- :ref:`TEXT <t3tsref:cobj-text>` is for the rendering of standard text
  or the content of fields. The TEXT object implements the :ref:`stdWrap
  <t3tsref:stdwrap>` functionality on the very rootlevel of the object.
  This is non-standard! ::

   lib.test1 = TEXT
   lib.test1.field = uid

- :ref:`FILE <t3tsref:cobj-file>` imports the content of a file, directly.

- :ref:`TEMPLATE <t3tsref:cobj-template>` replaces markers in a
  template with content coming from TYPO3. ::

   page.10 = TEMPLATE
   page.10 {
     template = FILE
     template.file = fileadmin/test.tmpl
     subparts {
       HELLO = TEXT
       HELLO.value = This line here replaces the content in between the markers ###HELLO### and ###HELLO### in the HTML template.
     }
     marks {
       Test = TEXT
       Test.value = The marker ###TEST### will be replaced with this text.
     }
     workOnSubpart = DOCUMENT
   }

- :ref:`MULTIMEDIA <t3tsref:cobj-multimedia>` renders multimedia
  objects.

- :ref:`IMGTEXT <t3tsref:cobj-imgtext>` allows us to generate images
  inline with text. It is used for the content element "text &
  images".

- :ref:`FORM <t3tsref:cobj-form>` generates an HTML-form.

