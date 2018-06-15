.. include:: ../../Includes.txt


.. _prerequisites:

Prerequisites
^^^^^^^^^^^^^

It is assumed that you have a running TYPO3 CMS system
(if not, please refer to the :ref:`Installation Guide <t3install:start>`)
and that you have been through the
:ref:`Getting Started Tutorial <t3start:start>` in order
to have a general idea of how the TYPO3 CMS backend operates.

You may also want to have been through the
:ref:`Editors Tutorial <t3editors:start>` in order to be
familiar with the concepts of pages and content elements.

A few more elements that you need to know before starting:

- all content elements are stored in a database table called `tt_content`

- each content element has a database field called `CType` in which
  the type of the content element is stored

- the `tt_content` table also has a field called `pid` which refers
  to the page the content element is on

- in general, each TYPO3 CMS table has a field called `uid` which
  contains the primary key (unique id for each record)

- you will probably find useful to have a database access to check
  how information is stored as we proceed along this tutorial
