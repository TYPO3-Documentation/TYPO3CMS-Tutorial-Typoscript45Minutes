.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _function-encapslines:
.. _encapslines:

encapsLines
^^^^^^^^^^^

encapsLines is short for "encapsulate lines". This TypoScript function
allows us to define how single lines in the content are wrapped. For
example, if nothing is defined, a <p> or a <div> will wrap the
element. Another example would be to automatically replace all <b>
tags with <strong> tags.

A simple example:

In the RTE we have a text with the following HTML code::

   A simple text without anything special.
   &nbsp;
   <div class="myclass">Some text with a wrapping div tag.</div>

In TypoScript we have this::

   encapsLines {
          # Define which tags will be seen as wrappers.
          encapsTagList = div,p

          # Lines, which are not already encapsulated with a tag from
          # encapsTagList, will be wrapped with <p> tags.
          wrapNonWrappedLines = <p>|</p>

          # Replace all DIV tags with P tags.
          remapTag.DIV = P

          # If a line is empty, insert an empty space.
          innerStdWrap_all.ifEmpty = &nbsp;
   }

The result will look like this in HTML code::

    <p>A simple text without anything special.</p>
    <p>&nbsp;</p>
    <p class="myclass">Some text with a wrapping div tag.</p>;

With most TYPO3 projects, the following code will not be necessary.
But in the extension "css\_styled\_content", some settings are defined
with this function, which can be changed, if needed. So here follows an
example from the standard configuration of "css\_styled\_content" to
clarify its functionality. ::

   lib.parseFunc_RTE {

           nonTypoTagStdWrap.encapsLines {

                  # Wrapping tags.
                  encapsTagList = div,p,pre,h1,h2,h3,h4,h5,h6

                  # Convert all DIV tags to P tags.
                  remapTag.DIV = P

                  # Wrap all lines, which are not wrapped at all, with the <p> tag.
                  nonWrappedTag = P

                  # Add a space to all empty lines.
                  innerStdWrap_all.ifBlank = &nbsp;

                  # Here the - infamous - class "bodytext" is added.
                  addAttributes.P.class = bodytext

                  # Use addAttributes, if no other attribute is set.
                  addAttributes.P.class.setOnly = blank
          }
   }

Comparing the first example with the second, you might notice that
apparently there are two parameters, which do the same thing: firstly,
"wrapNonWrappedLines"; and secondly, "nonWrappedTag". The difference is
that "nonWrappedTag" can be extended by "addAttributes", whereas for
"wrapNonWrappedLines" you need to specify *exactly one* complete
wrapping tag. If you have lines, which are already wrapped in
<p class="foo">\|</p> and "wrapNonWrappedLines" is defined as
<p>\|</p>, the result would be an inconsistent mixture of P tags with
and without classes, instead of one consistent wrap.

To demonstrate it clearly: To get rid of the mostly annoying
class="bodytext", you don't need to do more than to insert the
following line::

   lib.parseFunc_RTE.nonTypoTagStdWrap.encapsLines.addAttributes.P.class >

