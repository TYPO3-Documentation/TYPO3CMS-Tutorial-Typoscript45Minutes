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

TYPO3 CMS provides the :ref:`FLUIDTEMPLATE <t3tsref:cobj-fluidtemplate>` object,
with which we can use Fluid template and render our web site with it.

.. code-block:: typoscript

	10 = FLUIDTEMPLATE
	10 {
		templateName = TEXT
		templateName.value = Default

		templateRootPaths {
			0 = EXT:sitepackage/Resources/Private/Templates/Page/
		}
		partialRootPaths {
			0 = EXT:sitepackage/Resources/Private/Partials/Page/
		}
		layoutRootPaths {
			0 = EXT:sitepackage/Resources/Private/Layouts/Page/
		}
	}


In your template file you can now replace the parts that should be filled by TYPO3 with references to the TypoScript
configuration objects you defined earlier.

For example to render a template with the menu we defined and :

.. code-block:: html

	<nav>
		<f:cObject typoscriptObjectPath="lib.textMenu" />
	</nav>

	<div class="container">
		<f:cObject typoscriptObjectPath="lib.dynamicContent" data="{pageUid: '{data.uid}', colPos: '0'}" />
	</div>
