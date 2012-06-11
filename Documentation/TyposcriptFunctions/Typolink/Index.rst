

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


typolink
^^^^^^^^

Typolink is the TYPO3 function which allows us to generate all kinds
of links. If possible, one should use this function to generate links,
because these will be "registered" in TYPO3. This is a prerequisite,
for example, for realURL, which will generate search engine friendly
paths; or for the anti-spam protection on email addresses. So, if you
feel the urge to use <a href="..."> - don't.

The functionality of typolink is basically very easy. Typolink links
the specified text according to the defined parameters. One example:

::

    temp.link = TEXT
    temp.link {
   
        # this is the defined text
        value = Examplelink
   
        # here comes the typolink function
        typolink {
   
            # whats the goal of the link?
            parameter = http://www.example.com/
   
            # with which target(_blank opens a new window)
            extTarget = _blank
   
            # and add a class to the link so we can style it.
            ATagParams = class="linkclass"
        }
    }

The example above will generate this HTML code: <a class="linkclass"
target="\_blank" href=" `http://www.example.com/
<http://www.example.com/>`_ " >Examplelink</a>

Typolink works almost like a wrap - the content which is defined by
value, for example, will be wrapped by the HTML anchor tag. If no
content is defined, it will be generated automatically. With a link to
a page, the page title will be used. With an external URL, the URL
will be shown.

One can shorten this example, because the "parameter" tag from the
typolink function does some of the thinking for you. Here, the short
example will generate the exact same HTML code.

::

    temp.link2 = TEXT
    temp.link2 {
   
        # again the defined text
        value = Examplelink
   
        # the parameter with the summary of the parameters of the first example (explanation follows below)
        typolink.parameter = www.example.com _blank linkclass
    }

The "parameter"-part from the typolink function analyzes the entry on
specific characters and converts The "parameter" part from the
typolink function analyzes the entry on specific characters, and
converts the respective sections. Initially, the parameter entry will
be separated at the blank spaces. If then a dot "." is found (if the
case may be in before a slash "/"), an external link will be
generated. If the dot "." is found after a slash "/", a file link is
generated. If an @ is found, an e-mail link would be generated. If a
integer is found, like "51", an internal link to the page with the id
"51" will be generated. If a leading hash "#" is found, a certain
content element will be linked (for example, for a link to the content
element with the id #234 on the current page. In order to link to the
page with ID 51 and content element #234, one would use 51#234).

The second part of the parameter describes the goal of the link.
Normally, this would be - like in the first example - defined by
extTarget (for external links) or target (for internal links); but, it
can be overwritten by using a second parameter.

The third part will be converted to a class attribute for the link.

If only a class attribute is needed, and no target, one has to fill
the target part anyway, because the function would not recognize the
class being in the third place. So, without a target, the line would
be the following (with a minus sign "-" as divider):

::

   typolink.parameter = www.example.com � linkclass

With the usage of the typolink function and the target attribute, it's
also possible to open links in JavaScript-popups.

::

   temp.link = TEXT
   temp.link {
   
        # the link text
        value = Open a popup window
   
        typolink {
             # 1. Parameter = PageID of the target page, 1 2. parameter = size of the popup
             parameter = 10 500x400
   
             # The title tag of the link
             title = Click here to open a popup window
   
             # The parameters of the popup window
             JSwindow_params = menubar=0, scrollbars=0, toolbar=0, resizable=1
   
        }
   }

It is important to note that many of the properties of typolink are of
the type stdWrap. This means that values can be calculated, or read
out of the database.

::

   lib.stdheader >
   lib.stdheader = TEXT
   lib.stdheader {
      field = header
      typolink.parameter.field = header_link
      wrap = <h2>|</h2>
   }

The headline will be displayed, and a link will be placed with a goal
which is defined in the field header\_link. The first line removes the
default settings from css\_styled\_content.

