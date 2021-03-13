Desktop Application Menu
========================

Adding a desktop file will put your application in the Applications menu
when you install it.

Add the following to debian/install file
::

	*.desktop usr/share/applications


Simple PyQt5.desktop
--------------------

Create a file called `Simple PyQt5.desktop` in the simpqt-0.0.1
directory. Note most file managers will drive you nuts if you rename as
they automaticly add .desktop when you save the name so if you rename a
.desktop be sure and delete the .desktop.
::

	[Desktop Entry]
	Version=1.0
	Type=Application
	Name=Simple PyQt5
	Comment=We just Open a GUI
	Exec=simpqt
	Icon=/usr/share/pixmaps/linuxcncicon.png
	Categories=Utility;
	Terminal=false
	StartupNotify=true
	StartupWMClass=simpqt
	Name[en_US]=Simple PyQt5

Rebuild the deb as before open a terminal in the simpqt-0.0.1 directory
and use the following command
::

	dpkg-buildpackage -us -uc

Reinstall the application and the menu will show up in Applications >
Accessories.


So now the directories and files look like this after building the deb.
::

	john@d10cave:~/gui-deb$ tree
	.
	├── simpqt-0.0.1
	│   ├── debian
	│   │   ├── changelog
	│   │   ├── compat
	│   │   ├── control
	│   │   ├── copyright
	│   │   ├── debhelper-build-stamp
	│   │   ├── files
	│   │   ├── install
	│   │   ├── manpages
	│   │   ├── rules
	│   │   ├── simpqt
	│   │   │   ├── DEBIAN
	│   │   │   │   ├── control
	│   │   │   │   └── md5sums
	│   │   │   └── usr
	│   │   │       ├── bin
	│   │   │       │   └── simpqt
	│   │   │       ├── lib
	│   │   │       │   └── python3
	│   │   │       │       └── dist-packages
	│   │   │       │           └── libsimpqt
	│   │   │       │               └── simpqt.ui
	│   │   │       └── share
	│   │   │           ├── applications
	│   │   │           │   └── Simple PyQt5.desktop
	│   │   │           ├── doc
	│   │   │           │   └── simpqt
	│   │   │           │       ├── changelog.gz
	│   │   │           │       └── copyright
	│   │   │           └── man
	│   │   │               └── man1
	│   │   │                   └── simpqt.1.gz
	│   │   ├── simpqt.substvars
	│   │   └── source
	│   │       └── format
	│   ├── man
	│   │   └── simpqt.1
	│   ├── Simple PyQt5.desktop
	│   └── src
	│       ├── simpqt
	│       └── simpqt.ui
	├── simpqt_0.0.1_amd64.buildinfo
	├── simpqt_0.0.1_amd64.changes
	├── simpqt_0.0.1_amd64.deb
	├── simpqt_0.0.1.dsc
	└── simpqt_0.0.1.tar.xz

19 directories, 28 files
