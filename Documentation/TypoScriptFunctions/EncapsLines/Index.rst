.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


encapsLines
^^^^^^^^^^^

EncapsLines is short for "encapsulate lines". This TypoScript function
allows us to define how single lines in the content are wrapped. For
example, if nothing is defined, a <p> or a <div> will wrap the
element. Another example would be to automatically replace all <b>
tags with a <strong> tag.

**A simple example:**

In the RTE we have the following text::

   A simple text without anything special

   <div class="myclass">Some text with a wrapping div tag.</div>

In TypoScript we have the following::

   encapsLines {
          # define which tags will be seen as wrappers
          encapsTagList = div,p

          # Lines which are not already encapsulated with tags from the
          # encapsTagList will be wrapped with <p>-tags
          wrapNonWrappedLines = <p>|</p>

          # replace all DIV tags with P tags
          remapTag.DIV = P

          # if a line is empty insert a empty space
          innerStdWrap_all.ifEmpty = &nbsp;
   }

The result will look like this in HTML code::

    <p>A simple text without anything special.</p>
    <p>&nbsp;</p>
    <p class="myclass">Some text with a wrapping div tag.</p>;

With most TYPO3 projects, the following code will not be necessary.
But in the extension "css\_styled\_content", some settings are defined
with this function, which can be changed, if needed. Therefore follows
an example from the standard configuration from
"css\_styled\_content", to clarify its functionality. ::

   lib.parseFunc_RTE {

           nonTypoTagStdWrap.encapsLines {

                  # wrapping tags
                  encapsTagList = div,p,pre,h1,h2,h3,h4,h5,h6

                  # convert all DIV tags to <p> tags
                  remapTag.DIV = P

                  # wrap all lines which are not wrapped at all with the <p> tag
                  nonWrappedTag = P

                  # replace all empty lines with the empty space code
                   innerStdWrap_all.ifBlank = &nbsp;

                  # here the - infamous - bodytext is placed
                  addAttributes.P.class = bodytext

                  # use addAttributes if no other attribute is set
                  addAttributes.P.class.setOnly=blank
          }
   }

Comparing the first example with the second, you might notice that
apparently there are 2 parameters which do the same thing: firstly,
"wrapNonWrappedLines"; and secondly, "nonWrappedTag". The difference
is that "nonWrappedTag" can be extended, whereas "wrapNonWrappedLines"
needs a comprehensive wrapping tag. If already wrapped lines like <p
class="foo">\|</p> are wrapped, and "wrapNonWrappedLines" is defined
as <p>\|</p>, the result would be a mixture of P tags with and without
classes, instead of a consistent wrap.

To demonstrate it clearly, to get rid of the mostly annoying
class="bodytext", you don't need to do more than insert the following
line::

   lib.parseFunc_RTE.nonTypoTagStdWrap.encapsLines.addAttributes.P.class >

