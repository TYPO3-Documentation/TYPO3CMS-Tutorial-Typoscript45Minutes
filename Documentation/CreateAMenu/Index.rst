.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../Includes.txt


Create a menu
-------------

Until now, we learned how the page content is rendered; however, the
page navigation is missing.

TYPO3 offers a special menu object `HMENU
<http://wiki.typo3.org/TSref/HMENU>`_ (H stands for hierarchical) to
easily build different kinds of menus.

The menu should be built like a nested list::

   <ul>
      <li>first level</li>
      <li>first level
          <ul>
              <li>second level</li>
          </ul>
      </li>
      <li>first level</li>
   </ul>

In order to keep oversight, we create a new folder and a new extension
template. In here, we define a new object which we can add to the main
template, later. In this way, we can define a diversity of objects
apart and safe keep them for future projects. The extension template
can be added with the use of "include basis template".

Normally, these objects are defined as sub-objects of "lib". We could
use any term that hasn't been assigned, yet. ::

    lib.textmenu = HMENU
    lib.textmenu {

      # we define the first level as text menu
      1 = TMENU

      # We define the ''NO''rmal state
      1.NO.allWrap = <li>|</li>

      # We define the ''ACT''ive state
      1.ACT = 1
      1.ACT.wrapItemAndSub = <li>|</li>

      # Wrap the whole menu
      1.wrap = <ul class="level1">|</ul>

      # The second level should be configured exactly the same.
      # In-between the curly brackets objects can be copied.
      # With the dot "." we define that the object can be found in the brackets
      2 < .1
      2.wrap = <ul class="level2">|</ul>
      3 < .1
      3.wrap = <ul class="level3">|</ul>
    }

The object HMENU allows us to create a diversity of menus. For every
menu level, an arbitrary menu object can be created which does the
rendering. Thus, it is possible to create a GMENU on the first level,
and to use TMENU for the 2nd and 3rd level.

The first menu level will be defined with the number one, the second
2, etc. Naturally, it is not allowed to have missing numbers. (For
example, if the third menu level is not defined, the fourth will not
be rendered.)

On every menu level, we can configure various states of menu items –
see menu items (NO = "normal"; ACT = "pages in the root line" (means
current page, the parents, grandparents, etc.); CUR = "the current
page"). In doing so, pay special attention to the fact that aside the
normal state ("NO"), every state has to be activated first (i.e. ACT =
1).

Henceforth, we can use the menu and implement it at our page. ::

   page.5 < lib.textmenu


