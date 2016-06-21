.. include:: ../Includes.txt


.. _insert-content-in-a-template:

Insert content in a HTML template
---------------------------------

Although we now know how to render content, and how to build a menu,
we do not have a real website yet.

Again everything could be done using TypoScript. That would be pretty
complex and error prone. Furthermore if a HTML template file is
prepared by a designer for the web site, it would be a shame not to
reuse it as is as much as possible. It would also make further
corrections to the HTML template much harder to apply.

TYPO3 CMS provides the :ref:`TEMPLATE <t3tsref:cobj-template>` object,
with which we can parse a HTML template file and insert the menu, content,
and so on, at the right place into it.

.. code-block:: typoscript

    page.10 = TEMPLATE
    page.10 {
	template = FILE

		# We load the HTML template file.
		template.file = fileadmin/test.tmpl

		# Text areas in the template file:
		# <!-- ###MENU### begin -->
		# Here is an example of content as placeholder, everything which is
		# in between the markers will be replaced by the content of the
		# sub-parts, in this case by the menu.
		# <!-- ###MENU### end -->

		# Subparts are a pair of two markers (like "###MENU###" above).
		subparts {
			MENU < lib.textmenu
			CONTENT < styles.content.get
			COLUMNRIGHT < styles.content.getRight
		}

		# Marks are single markers. That is, there is no start and end marker;
		# instead, the marker is replaced directly. ###LOGO### will
		# be replaced by the logo.
		marks {
			LOGO = IMAGE

			# Use the graphic logo.gif.
			LOGO.file = fileadmin/templates/logo.gif

			# The logo links to the page with ID 1.
			LOGO.stdWrap.typolink.parameter = 1
		}
		workOnSubpart = DOCUMENT
	}

The :ref:`TEMPLATE <t3tsref:cobj-template>` object works with markers,
which are inserted in the HTML template and dynamically replaced by
TYPO3 CMS upon rendering.

There are two types of markers. One is called a **mark**. It represents
a simple insertion point. The other type is the **subpart**. It is comprised
of an openign and a closing marker. Everything between the two markers
in the HTML template is replaced by TYPO3 CMS.

Using HTML templates in such a way is covered in details in the
:ref:`Templating Tutorial: Basics <t3templating:start>`.

Alternatives exists, such as extension
`automaketemplate <https://typo3.org/extensions/repository/view/automaketemplate>`_
which relies :code:`id` attributes instead of markers. It is also possible
to go for a rendering based on Fluid.

