

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


Prerequisites
^^^^^^^^^^^^^

We assume that the reader has a TYPO3 system up and running and that
the basic operations are known. The difference between pages and
content elements will not be elaborated here. We also assume that you
know that the content of a page is put together by a combination of
various content elements. Just to make sure, we point out the fact
that these content elements are being stored in the table tt\_content.
The database field "CType" defines which content element type we have.
Depending on CType a certain mask is loaded.

For a better understanding of TYPO3 and TypoScript, it is helpful to
have a look at the database. The extension phpmyadmin allows an easy
and comfortable way to access the database from the backend, thus
allowing an overview on the relationships between the pages,
tt\_content and the backend. It should be known that the PID (Page ID)
stands for the ID of a page and the UID (Unique ID) stands for a
unique record.

