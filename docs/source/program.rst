Create the Simpqt program
=========================

In the src directory create the simpqt file and add the following to it.
::

	#!/usr/bin/python3

	import sys, os
	from PyQt5.QtWidgets import QApplication, QMainWindow
	from PyQt5 import uic

	if os.path.split(sys.argv[0])[0] == '/usr/bin':
		GUI_PATH = '/usr/lib/simpqt'
		print('Installed')

	if os.path.split(sys.argv[0])[0] == '.':
		GUI_PATH = os.path.split(os.path.realpath(sys.argv[0]))[0]
		print('In Development')

	class main(QMainWindow):
		def __init__(self):
			super().__init__()
			uic.loadUi(os.path.join(GUI_PATH, 'simpqt.ui'), self)
			self.setGeometry(50, 50, 500, 300)
			self.setWindowTitle("PyQT5 Minimal!")
			self.show()

	if __name__ == '__main__':
		app = QApplication(sys.argv)
		gui = main()
		sys.exit(app.exec_())

In order to test our application without installing each time we make a
change we have to know if the program is installed or not to use the
correct path to the .ui file. Also to test the program file needs to be
marked as executable. Right click on the file and check executable or in
the src directory open a terminal and use the following command.
::

	chmod +x simpqt

Next we need the .ui file so create simpqt.ui file and add the following.
::
	
	<?xml version="1.0" encoding="UTF-8"?>
	<ui version="4.0">
	 <class>MainWindow</class>
	 <widget class="QMainWindow" name="MainWindow">
	  <property name="geometry">
	   <rect>
	    <x>0</x>
	    <y>0</y>
	    <width>800</width>
	    <height>600</height>
	   </rect>
	  </property>
	  <property name="windowTitle">
	   <string>MainWindow</string>
	  </property>
	  <widget class="QWidget" name="centralwidget">
	   <layout class="QGridLayout" name="gridLayout">
	    <item row="0" column="1">
	     <widget class="QLabel" name="label_2">
	      <property name="text">
	       <string>Load ui file</string>
	      </property>
	     </widget>
	    </item>
	    <item row="0" column="0">
	     <widget class="QLabel" name="label">
	      <property name="text">
	       <string>Minimal</string>
	      </property>
	     </widget>
	    </item>
	   </layout>
	  </widget>
	  <widget class="QMenuBar" name="menubar">
	   <property name="geometry">
	    <rect>
	     <x>0</x>
	     <y>0</y>
	     <width>800</width>
	     <height>25</height>
	    </rect>
	   </property>
	  </widget>
	  <widget class="QStatusBar" name="statusbar"/>
	 </widget>
	 <resources/>
	 <connections/>
	</ui>


Now the directory structure looks like this and we have all the files
needed to build the deb.
::

	john@d10cave:~/gui-deb$ tree
	.
	└── simpqt-0.0.1
	    ├── debian
	    │   ├── changelog
	    │   ├── compat
	    │   ├── control
	    │   ├── copyright
	    │   ├── files
	    │   ├── manpages
	    │   ├── rules
	    │   └── source
	    │       └── format
	    ├── man
	    │   └── simpqt.1
	    └── src
	        ├── simpqt
	        └── simpqt.ui


	5 directories, 10 files

If you want to edit the ui file with Qt5 Designer you will need install
it with the following command.
::

	sudo apt install libqt5designer5
