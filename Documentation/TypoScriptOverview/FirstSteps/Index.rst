.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


First steps
^^^^^^^^^^^

In the Setup field of the main template, the basic rendering is
defined.

TypoScript essentially consists of objects, which have certain
properties. Some of these properties can accept other objects, others
stand for certain functions or define the behavior of the object.

For rendering, the object PAGE is responsible. ::

    # The object mypage is defined as PAGE object.
    mypage = PAGE

    # PAGE objects have the property typeNum.
    mypage.typeNum = 0

    # mypage has an object "10" of type TEXT. It is a TEXT object.
    mypage.10 = TEXT

    # TEXT objects in turn have a property called "value".
    mypage.10.value = Hello World

The PAGE object on the one hand offers numerous properties "with names"
(like typeNum). On the other hand it also has an endless number of
numbered objects (a so-called content array). The names of these
objects only consist of numbers and the objects will get sorted
accordingly when they are rendered. First, the object with the smallest
number will be rendered; at the end, the object with the biggest
number. The order of the lines in the TypoScript template is
irrelevant. ::

    # Create a PAGE object.
    mypage = PAGE
    mypage.typeNum = 0

    mypage.30 = TEXT
    mypage.30.value = This gets rendered last.

    # Rendering would first output object number 10, then 20 and 30.
    # Object number 25 would logically be output between 20 and 30.
    mypage.20 = TEXT
    mypage.20.value = This is rendered in the middle.

    # This is the first output object
    mypage.10 = TEXT
    mypage.10.value = This is rendered first.

    # Here we create a second PAGE object, which we can use for the
    # print view.
    print = PAGE
    print.typeNum = 98
    print.10 = TEXT
    print.10.value = This is the print version.

Every entry is stored in a multidimensional PHP array. Every object
and every property, therefore, is unique. We could define an arbitrary
number of PAGE objects; however, the typeNum has to be unique. For
every typeNum, there can be only one PAGE object.

In the example, for the parameter typeNum = 98, a different output
mode is created. By using typeNum, various output types can be
defined. If typeNum is not set explicitly, it defaults to "0".
Typically, typeNum = 0 is used for the HTML output. The request for
HTML would be index.php?id=1, respectively, and index.php?id=1&type=98
for the print output. The value of &type defines, which PAGE object 
(according to its typeNum), is displayed. That is why it is possible to
have print output, HTML output and even PDF output in one and the same
TypoScript template. In doing so, configurations which are used in all of
the views can be copied and changed just a little bit in the new
object. (For example, we can copy the normal page content into the
print view, but leave away the menu.)

.. note::

   *The output of these examples were both normal text. Especially with
   output formats like WML the HTTP header should be changed etc. This is
   not covered here.*

The previous example would look like this PHP array::

    $TypoScript['mypage'] = 'PAGE';
    $TypoScript['mypage.']['typeNum'] = 0;
    $TypoScript['mypage.']['10'] = 'TEXT';
    $TypoScript['mypage.']['10.']['value'] = 'This is rendered first.';
    $TypoScript['mypage.']['20'] = 'TEXT';
    $TypoScript['mypage.']['20.']['value'] = 'This is rendered in the middle.';
    $TypoScript['mypage.']['30'] = 'TEXT';
    $TypoScript['mypage.']['30.']['value'] = 'This gets rendered last.';

    $TypoScript['print'] = 'PAGE';
    $TypoScript['print.']['typeNum'] = 98;
    $TypoScript['print.']['10'] = 'TEXT';
    $TypoScript['print.']['10.']['value'] = 'This is the print version.';

Empty spaces at the start and end of values will be removed by TYPO3
automatically (using the trim() function of PHP).

With the "=" sign, we saw the basic assignment: a value is assigned. ::

    # The object test is an object of type TEXT.
    # "=" means "set value".
    test = TEXT
    test.value = Holla

    # "<" means "copy object".
    # mypage.10 returns "Holla"
    mypage.10 < test

    # Change the copied object.
    # The change has no effect on mypage.10; it still returns "Holla".
    test.value = Hello world

    # "=<" means "create an object reference (link the object)".
    test.value = Holla
    mypage.10 =< test

    # Change the object which is referenced.
    # Changes DO have an effect on mypage.10.
    # mypage.10 will return "Hello world".
    test.value = Hello world

Object types are always written with capital letters; parameter and
functions typically in camel case (first word lower case, next word
starts with a capital letter, no space between words). There are some
exceptions to this.

With the "." as a separator parameter, functions and child objects are
referenced and can be assigned values accordingly. ::

   mypage.10.stdWrap.wrap = <h1>|</h1>

**Which objects, parameters, and functions exist, can be referenced in
the :ref:`TypoScript Reference (TSref) <t3tsref:start>`.**

If some objects are wrapped in each other, and many parameters are
assigned, things can get more complicated. ::

    mypage = PAGE
    mypage.typeNum = 0
    mypage.10 = TEXT
    mypage.10.value = Hello world
    mypage.10.stdWrap.typolink.parameter = http://www.typo3.org/
    mypage.10.stdWrap.typolink.additionalParams = &parameter=value

    # The function name "ATagParams" does not use the standardized
    # "camelCase".
    mypage.10.stdWrap.typolink.ATagParams = class="externalwebsite"
    mypage.10.stdWrap.typolink.extTarget = _blank
    mypage.10.stdWrap.typolink.title = The website of TYPO3
    mypage.10.stdWrap.postCObject = TEXT
    mypage.10.stdWrap.postCObject.value = This text also appears in the link text
    mypage.10.stdWrap.postCObject.stdWrap.wrap = |, because the postCObject is executed before the typolink function.

To keep it simple, **curly brackets {}** are allowed to define object
levels. *Note* that the opening curly bracket always must be *on the
same line* as the property, after which it is noted! Adding a line
break in between (so that the opening bracket would be located in a new
line) is not allowed. **Parenthesis ()** are for writing text on more
than one line. The above example can be rewritten as the following::

    mypage = PAGE
    mypage {

      typeNum = 0

      10 = TEXT
      10 {

         value = Hello world
         stdWrap {
            typolink {

               parameter = http://www.typo3.org/
               additionalParams = &parameter=value

               # The function name "ATagParams" does not use the standardized
               # "camelCase".
               ATagParams = class="externalwebsite"

               extTarget = _blank
               title = The website of TYPO3
            }

            postCObject = TEXT
            postCObject {

               value = This text also appears in the link text
               stdWrap.wrap (
                |, because the postCObject is executed before the typolink function.
               )
            }
         }
      }
    }

Using this style of notation the danger of typographic errors is
reduced and the script is easier to read. In addition, if we liked to
rename mypage, we would only have to change the first two lines,
instead of many more occurrences all over the entire script.

