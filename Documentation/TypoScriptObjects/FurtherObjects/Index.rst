.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _cobjects-further-cobjects:

Further objects
^^^^^^^^^^^^^^^

- :ref:`CASE <t3tsref:cobj-case>` allows case differentiation. In
  css\_styled\_content, this object is used for rendering different
  objects according to their type.

- :ref:`COA <t3tsref:cobj-coa>` (content object array) allows us to
  combine an arbitrary number of objects.

- :ref:`COA\_INT <t3tsref:cobj-coa-int>` is a COA object, but non
  cached. This element will be regenerated at each call. This is useful
  with time and date or user dependent data, for example.

- :ref:`LOAD\_REGISTER <t3tsref:cobj-load-register>` /
  :ref:`RESTORE\_REGISTER <t3tsref:cobj-restore-register>`
  objects allow us to fill the global array $GLOBALS['TSFE']->register[]
  with content. These objects return nothing. Single values and complete
  TypoScript objects can be used. In doing so, the register works as a
  stack: With every call, a further element is stacked. With
  RESTORE\_REGISTER, the element on top can be removed.

- :ref:`USER <t3tsref:cobj-user>` and USER\_INT are for user defined
  functions. Every plugin is such an object. USER\_INT is the non
  cached variant.

- :ref:`IMG\_RESOURCE <t3tsref:cobj-img-resource>` is used by IMAGE.
  The resource is returned (the content), which normally is the SRC
  attribute of the IMG tag. If images are scaled, this object serves as
  a calculation basis for the new files, which are stored in the
  /typo3temp folder.

- :ref:`EDITPANEL <t3tsref:cobj-editpanel>` is inserted, if a backend
  user is logged in and the option "Display Edit Icons" is set in the
  frontend admin panel. If the admin panel is inserted, the pages will
  not be cached anymore. Icons for sorting order, editing, removing,
  and so on, will be shown.

- :ref:`GIFBUILDER <t3tsref:gifbuilder>` is used for generating .gif
  files dynamically. Various texts and images can be combined, and much
  more. The GIFBUILDER object itself again offers some objects, like
  TEXT or IMAGE, which are **not** related to the standard TEXT or
  IMAGE objects, respectively. While working with the GIFBUILDER, we
  have to watch out that we do not confuse the objects with one
  another.

We did not introduce all objects which exist in TypoScript, but we
have named the most important ones.

