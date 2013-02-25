.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../Includes.txt


.. _menu:
.. _create-a-menu:

Create a menu
-------------

Until now, we learned how the page *content* is rendered; however, the
page *navigation* is missing.

TYPO3 offers a special menu object called :ref:`HMENU
<t3tsref:cobj-hmenu>` ("H" stands for hierarchical) to easily build
different kinds of menus.

The menu should be built like a nested list::

   <ul class="level1">
      <li>first level</li>
      <li>first level
          <ul class="level2">
              <li>second level</li>
          </ul>
      </li>
      <li>first level</li>
   </ul>

In order to keep oversight, we create a new folder and a new extension
template. In here, we define a new object which we can add to the main
template, later. In this way, we can define a diversity of objects
separately from each other and use them for future projects easily. The
extension template can be added in the main template with "include
basis template".

Normally, these objects are defined as sub-objects of "lib". We could
use any term that hasn't been assigned, yet. ::

    lib.textmenu = HMENU
    lib.textmenu {

      # We define the first level as text menu.
      1 = TMENU

      # We define the normal state ("NO").
      1.NO = 1
      1.NO.allWrap = <li>|</li>

      # We define the active state ("ACT").
      1.ACT = 1
      1.ACT.wrapItemAndSub = <li>|</li>

      # Wrap the whole first level.
      1.wrap = <ul class="level1">|</ul>

      # The second and third level should be configured exactly
      # the same way.
      # In between the curly brackets, objects can be copied.
      # With the dot "." we define that the object can be found
      # in the brackets.
      # With 2.wrap and 3.wrap we overwrite the wrap, which was
      # copied from 1.wrap.
      2 < .1
      2.wrap = <ul class="level2">|</ul>
      3 < .1
      3.wrap = <ul class="level3">|</ul>
    }

The object HMENU allows us to create a diversity of menus. The first
menu level will be defined with the number "1", the second with the
"2", etc. Naturally, it is not allowed to have missing numbers. (For
example, if the third menu level is not defined, the fourth will not be
rendered.)

For every menu level, an arbitrary menu object can be created, which
does the rendering. Thus, it is for example possible to create a GMENU
on the first level, and to use a TMENU for the 2nd and 3rd level.

On every menu level, we can configure various states for the single
menu items – see :ref:`menu items
<t3tsref:tmenu-gmenu-imgmenu-common-properties>`, e.g. NO for "normal",
ACT for "pages in the root line" (means current page, the parent,
grandparent, etc.) or CUR for "the current page". In doing so, pay
special attention to the fact that aside the normal state ("NO"),
*every state has to be activated first* (i.e. "ACT = 1").

Henceforth, we can use the menu and implement it in our page. ::

   page.5 < lib.textmenu


