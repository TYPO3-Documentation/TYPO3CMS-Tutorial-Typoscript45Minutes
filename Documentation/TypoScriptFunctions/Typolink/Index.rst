.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _function-typolink:
.. _typolink:

typolink
^^^^^^^^

typolink is the TYPO3 function, which allows us to generate all kinds
of links. If possible, one should use this function to generate links,
because these will be "registered" in TYPO3. This is a prerequisite,
for example, for realURL, which will generate search engine friendly
paths; or for the anti-spam protection on email addresses. So, if you
feel the urge to use <a href="..."> - **don't**!

The functionality of typolink is basically very easy. typolink links
the specified text according to the defined parameters. One example::

    temp.link = TEXT
    temp.link {

        # This is the defined text.
        value = Example link

        # Here comes the typolink function.
        stdWrap.typolink {

            # This is the destination of the link,
            parameter = http://www.example.com/

            # with a target ("_blank" opens a new window),
            extTarget = _blank

            # and add a class to the link so we can style it.
            ATagParams = class="linkclass"
        }
    }

The example above will generate this HTML code::

   <a class="linkclass" target="\_blank" href="http://www.example.com/">Example link</a>

typolink in some way almost works like a wrap: The content which is
defined for example by value, will be wrapped by the HTML anchor tag.
If no content is defined, it will be generated automatically: With a
link to a page, the page title will be used. With an external URL, the
URL will be shown.

One can shorten this example, because the "parameter" tag from the
typolink function does some of the thinking for you. Here, the short
example will generate exactly the same HTML code. ::

    temp.link2 = TEXT
    temp.link2 {

        # Again the defined text.
        value = Example link

        # The parameter with the summary of the parameters of the first
        # example (explanation follows below).
        stdWrap.typolink.parameter = www.example.com _blank linkclass
    }

The "parameter" part from the typolink function analyzes the entry on
specific characters and converts the respective sections. Initially,
the parameter entry will be separated at the blank spaces. 

If in the first part then a dot "." is found (if the case may be in
before a slash "/"), an external link will be generated. If the dot "."
is found after a slash "/", a file link is generated. If an "@" is
found, an e mail link will be generated. If an integer is found, like
"51", an internal link to the page with the ID "51" will be generated.
If a leading hash "#" is found, a certain content element will be
linked (for example, for a link to the content element with the ID #234
on the current page. In order to link to the page with ID 51 and
content element #234, one would use 51#234).

The second part of the parameter describes the destination of the link.
Normally, this would be - like in the first example - defined by
extTarget (for external links) or target (for internal links); but, it
can be overwritten by using a second parameter.

The third part will be converted to a class attribute for the link.

If only a class attribute is needed, but no target, one has to fill
the target part anyway, because the class has to be at the third place.
To do that we can use the minus sign "-" instead of a target. The line
would then be the following::

   stdWrap.typolink.parameter = www.example.com - linkclass

With the usage of the typolink function and the target attribute, it is
also possible to open links in JavaScript popups. ::

   temp.link = TEXT
   temp.link {

        # The link text.
        value = Open a popup window.

        stdWrap.typolink {
             # First parameter is the page ID of the target page,
             # second parameter is the size of the popup window.
             parameter = 10 500x400

             # The title attribute of the link.
             title = Click here to open a popup window.

             # The parameters of the popup window.
             JSwindow_params = menubar=0, scrollbars=0, toolbar=0, resizable=1

        }
   }

It is important to note that many of the properties of typolink are of
the type stdWrap. This means that values can be calculated, or read
out of the database. ::

   lib.stdheader >
   lib.stdheader = TEXT
   lib.stdheader.stdWrap {
      field = header
      typolink.parameter.field = header_link
      wrap = <h2>|</h2>
   }

Here the first line removes the default settings from
css\_styled\_content. Then the headline will be displayed, and a link
will be placed with a destination, which is defined in the field
"header\_link".

