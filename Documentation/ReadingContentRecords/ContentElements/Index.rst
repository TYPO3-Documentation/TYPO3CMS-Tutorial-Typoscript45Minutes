.. include:: ../../Includes.txt


.. _content-objects:
.. _content-elementts:
.. _the-various-content-objects:

The various content elements
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The setup we just defined is pretty basic and will work only
for content elements containing text. But the content elements
are varied and we also need to render images, forms, etc.

The type of a content element is stored in the column
:code:`CType` of table "tt\_content". We can use this information
with a :ref:`CASE <t3tsref:cobj-case>` object, which makes it possible to
differentiate how the individual content element types are rendered.

.. code-block:: typoscript

	page.10.renderObj = CASE
	page.10.renderObj {

		# The field CType will be used to differentiate.
		key.field = CType

		# The content type "headline" is stored internally as "header".
		header = TEXT
		header.stdWrap.field = header
		header.stdWrap.wrap = <h1>|</h1>

		# Text is used for the text content element.
		text = COA
		text {

			10 = TEXT
			# The field tt_content.header normally holds the headline.
			10.stdWrap.field = header
			10.stdWrap.wrap = <h1>|</h1>

			20 = TEXT
			# The field tt_content.bodytext holds the content text.
			20.stdWrap.field = bodytext
			20.stdWrap.wrap = <p>|</p>

		}

		# ... other definitions follow here ...
	}

For content elements of type "headline" we render the content of
the header field wrapped in :code:`<h1>` tags. For content elements of type
"text" we render the headline and the content text.
