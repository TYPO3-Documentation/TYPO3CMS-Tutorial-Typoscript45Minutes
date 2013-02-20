.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


First steps
^^^^^^^^^^^

In the setup of the main template, the basic rendering is defined.

TypoScript essentially consists of objects which have certain
properties. Some of these properties can accept other objects, others
stand for certain functions or define the behavior of the object.

For rendering, the object PAGE is responsible. ::

    # the object mypage is defined as PAGE object
    mypage = PAGE

    # it has the property typeNum
    mypage.typeNum = 0

    # and an object "10" of type TEXT
    mypage.10 = TEXT

    # the object "10" has in turn a property called "value"
    mypage.10.value = Hello World

The PAGE object offers, in addition to numerous properties, an endless
number of objects which can only be identified by their numbers (a so-
called content array). This means that they only consist of numbers,
and will get sorted accordingly when they are rendered. First, the
object with the smallest number will be rendered; at the end, the
object with the biggest number. The order of the TypoScript is
irrelevant. ::

    mypage.30 = TEXT
    mypage.30.value = This is last

    # Rendering would first output object number 10, then 20 and 30. Object number 25 would logically be
    # outputted between 20 and 30
    mypage.20 = TEXT
    mypage.20.value = I'm the middle

    # This is the first outputted object
    mypage.10 = TEXT
    mypage.10.value = Hello World!

    # here we create a second object for the print view
    print = PAGE
    print.typeNum = 98
    print.10 = TEXT
    print.10.value = This is what the printer will see.

Every entry is stored in a multidimensional PHP array. Every object
and every property, therefore, is unique. We could define an arbitrary
number of PAGE objects; however, the typeNum has to be unique. For
every typeNum, there can be only one PAGE object.

In the example, for the parameter typeNum = 98, a different output
mode is created. By using typeNum, various output types can be
defined. Typically, typeNum = 0 is used for the HTML output. The
request for HTML would be index.php?id=1, respectively, and
index.php?id=1&type=98 for the print output. The value of &type
defines which PAGE object is displayed. That is why it is possible to
have print output, HTML output and even PDF output in one and the same
configuration. In doing so, configurations which are used in all of
the views can be copied and changed just a little bit in the new
object. (For example, normal page content can be copied into the print
view but not the menu.)

.. figure:: ../../Images/icon_note.png
   :alt: Note

**Note**

*The output of these examples where both normal text. Especially with
output formats like WML the HTTP header should be changed etc. This is
not covered here.'*

The previous example would look like this PHP array::

    $TypoScript['mypage'] = 'PAGE';
    $TypoScript['mypage .']['typeNum'] = 0;
    $TypoScript['mypage .']['10'] = 'TEXT';
    $TypoScript['mypage .']['10.']['value'] = 'Hello World!';
    $TypoScript['mypage .']['20'] = 'TEXT';
    $TypoScript['mypage .']['20.']['value'] = 'I'm the middle';
    $TypoScript['mypage .']['30'] = 'TEXT';
    $TypoScript['mypage .']['30.']['value'] = 'This is last';

Empty spaces at the start and end will be removed by TYPO3 (trim()).

With the "=" sign, we saw the basic assignment: a value is assigned. ::

    # = Value is set
    test = TEXT
    test.value = Holla

    # < Object will be copied
    # mypage.10 returns "Holla"
    mypage.10 < test

    # The copied object will be changed
    # The change has no effect on mypage.10
    test.value = Hello world

    # =< means that the object is referenced (the object is linked)
    test.value = Holla
    mypage.10 =< test
   .
    # - Object which is referenced changes
    # - changes HAVE an effect on mypage.10
    # - mypage.10 will return Hello world
    test.value = Hello world

Objects are always written with capital letters; parameter and
functions typically in camel case (first word lower case, next word
starts with a capital letter, no space between words). There are some
exceptions to this.

With the "." as a separator parameter, functions and child objects are
referenced and can be set accordingly with values. ::

   mypage.10.wrap = <h1>|</h1>

Which objects, parameters, and functions exist can be referenced in
the `TypoScript Reference (TSref) <http://typo3.org/documentation
/document-library/core-documentation/doc_core_tsref/current/>`_ .

If some objects are wrapped in each other, and many parameters are
assigned, it can get complicated. ::

    mypage = PAGE
    mypage.typeNum = 0
    mypage.10 = TEXT
    mypage.10.value = Hello world
    mypage.10.typolink.parameter = http://www.typo3.org/
    mypage.10.typolink.additionalParams = &nothing=nothing

    # ATagParams unfortunately does not use the standardized "camelCase"
    mypage.10.typolink.ATagParams = class="externalwebsite"
    mypage.10.typolink.extTarget = _blank
    mypage.10.typolink.title = The website of TYPO3
    mypage.10.postCObject = TEXT
    mypage.10.postCObject.value = This Text also appears in the link text
    mypage.10.postCObject.wrap = |, because the postCobject is executed before the typolink function

To keep it simple, the curly brackets {} are allowed to define object
levels. Parenthesis () are for writing text on more than one line. The
above example can be rewritten like the following example::

    mypage = PAGE
    mypage {

      typeNum = 0

      10 = TEXT
      10 {

         value = Hello world
         typolink {

            parameter = http://www.typo3.org/
            additionalParams = &nothing=nothing

            # ATagParams unfortunately does not use the standardized "camelCase"
            ATagParams = class="externalwebsite"

            extTarget = _blank
            title = The website of TYPO3
         }

         postCObject = TEXT
         postCObject {

            value = This Text also appears in the link text
            wrap (
             |, because the postCObject is executed before the typolink function
             )
          }
       }
    }

The danger of typographic errors is reduced, and the script is easier
to read. In addition, if we would like to rename mypage, we would only
have to change the first two lines, instead of the entire script.

**Please note** that the opening curly bracket always must be **on the same
line** as the property, after which it is noted! Adding a line break in
between (so that the opening bracket would be located in a new line) is not
allowed.
