.. include:: /Includes.rst.txt


.. _function-imgresource:
.. _imgresource:

imgResource
^^^^^^^^^^^

The :ref:`imgResource <t3tsref:imgresource>` function relates to modifications of
pictures. Its main usage is the property :code:`file` of the
:ref:`IMAGE <t3tsref:cobj-image>` object.

This, for example, allows an image to be resized:

.. code-block:: typoscript

	temp.myImage = IMAGE
	temp.myImage {
		file = toplogo.gif
		file.width = 200
		file.height = 300
	}

It is also possible to set minimum or maximum dimensions:

.. code-block:: typoscript

	temp.myImage = IMAGE
	temp.myImage {
		file = toplogo.gif

		# maximum size
		file.maxW = 200
		file.maxH = 300

		# minimum size
		file.minW = 100
		file.minH = 120
	}

:code:`imgResource` also provides direct access to
ImageMagick/GraphicsMagick features:

.. code-block:: typoscript

	temp.myImage = IMAGE
	temp.myImage {
		file = toplogo.gif
		file.params = -rotate 90
	}

