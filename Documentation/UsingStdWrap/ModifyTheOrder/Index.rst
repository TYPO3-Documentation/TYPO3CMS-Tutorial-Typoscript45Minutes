.. include:: ../../Includes.txt


.. _stdwrap-recursively:

Modify the order
^^^^^^^^^^^^^^^^

There is a way around this ordering restriction. :code:`stdWrap`
has a property called :code:`orderedStdWrap` in which several
:code:`stdWrap` properties can be called in numerical order.
Thus:

.. code-block:: typoscript

	10 = TEXT
	10 {
		value = typo3
		orderedStdWrap {
			10.noTrimWrap = |<strong>Tool: |</strong>|
			20.case = upper
		}
	}

results in:

.. code-block:: html

    <strong>TOOL: TYPO3</strong>

because we explicitely specified that :code:`noTrimWrap` should
happen before :code:`case`.

It should be noted that :code:`stdWrap` itself has a :code:`stdWrap`
property, meaning that it can be called recursively. In most case
:code:`orderedStdWrap` will do the job and is much easier to understand
making for code easier to maintain.
