.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


further objects
^^^^^^^^^^^^^^^

- `CASE <http://wiki.typo3.org/TSref/CASE>`_ object allows case
  differentiation. In css\_styled\_content, this object is used for
  rendering different objects according to their type.

- `COA <http://wiki.typo3.org/TSref/COA>`_ - Content Object Array -
  allows us to combine an arbitrary number of objects.

- `COA\_INT <http://wiki.typo3.org/wiki/index.php?title=TSref/COA_INT&ac
  tion=edit&redlink=1>`_ - non cached. This element will be generated at
  each call. This is useful with time and date or user dependent data,
  for example.

- `LOAD\_REGISTER <http://wiki.typo3.org/TSref/LOAD_REGISTER>`_ /
  `RESTORE\_REGISTER <http://wiki.typo3.org/TSref/RESTORE_REGISTER>`_
  objects allow us to fill the global array $GLOBALS["TSFE"]->register[]
  with content. This object returns nothing. Single values and complete
  TypoScript objects can be used. In doing so, the register works as a
  stack: with every call, a further element is stacked. With
  RESTORE\_REGISTER, the element on top can be removed.

- `USER <http://wiki.typo3.org/TSref/USER>`_ and USER\_INT are for user
  defined functions. Every plugin is such an object. USER\_INT is the
  noncached variant.

- `IMG\_RESOURCE <http://wiki.typo3.org/TSref/IMG_RESOURCE>`_ is being
  used by IMAGE. The resource is returned (the content), which normally
  is the SRC attribute of the IMG tag. If images are scaled, this object
  serves as a calculation basis for the new files, which are stored in
  the /typo3temp folder.

- `EDITPANEL <http://wiki.typo3.org/TSref/EDITPANEL>`_ - This object is
  inserted if a backend user is logged in, and the option "Display Edit
  Icons" is set in the frontend admin panel. If the admin panel is
  inserted, the pages will not be cached, anymore. Icons for sorting
  order, editing, removing, and so on, will be shown.

- `GIFBUILDER <http://wiki.typo3.org/TSref/GIFBUILDER>`_ is used for
  generating GIF files dynamically. Various texts and images can be
  combined, and much more. The GIFBUILDER itself offers some objects,
  like TEXT or IMAGE, which are not related to the standard TEXT or
  IMAGE objects, respectively. While working with the GIFBUILDER, we
  have to watch out that we do not confuse the objects, even though they
  have the same name.

We did not introduce all objects which exist in TypoScript, but we
have named the most important one

