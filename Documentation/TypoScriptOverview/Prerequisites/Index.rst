.. include:: /Includes.rst.txt


.. _prerequisites:

Prerequisites
^^^^^^^^^^^^^

It is assumed that you have a running TYPO3 CMS system
(if not, please refer to the :doc:`Installation Guide <t3install:Index>`)
and that you have been through the
:doc:`Getting Started Tutorial <t3start:Index>` in order
to have a general idea of how the TYPO3 CMS backend operates.

You may also want to have been through the
:doc:`Editors Tutorial <t3editors:Index>` in order to be
familiar with the concepts of pages and content elements.

A few more elements that you need to know before starting:

* all content elements are stored in a database table called `tt_content`
* each content element has a database field called `CType` in which
  the type of the content element is stored
* the `tt_content` table also has a field called `pid` which refers
  to the page the content element is on
* in general, each TYPO3 CMS table has a field called `uid` which
  contains the primary key (unique id for each record)
* you will probably find it useful to have a database access to check
  how information is stored as we proceed along this tutorial

..  note::
    `pid` stands for *parent*-id, not *page*-id.
