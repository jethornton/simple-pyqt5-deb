Directory Structure
===================

Building a deb of a Python PyQt5 GUI program so you can share it with
others using a deb.

The example Python program is called simpqt. Setup the directory
structure for the program as shown.
::

	john@d10cave:~/gui-deb$ mkdir -p simpqt/debian/source simpqt/man simpqt/src
	john@d10cave:~/gui-deb$ tree
	.
	└── simpqt
	    ├── debian
	    │   └── source
	    ├── man
	    └── src

	5 directories, 0 files


I created a directory called gui-deb and placed the other directories in there.

The program directory also has the revision as part of the name.

You can create the directories with a file manager or in a terminal with the
following command.
::

  mkdir -p simpqt/debian/source simpqt/man simpqt/src
