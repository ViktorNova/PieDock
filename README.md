PieDock
=======

PieDock is a task bar and application launcher in shape of a pie menu.
It feels a little bit like the famous OS X dock in a circle.

Demo
----

To experience the idea in action, try the WebPie
[demo](http://markusfisch.de/WebPie) or watch this
[video](http://vimeo.com/21360384).

Requirements
------------

Requires a C++ compiler, headers and libraries of X11 and libpng.
Xft and the X Rendering Extension (to make use of a compositing manager)
are optional.

Runs on Linux, BSD and Solaris.

Installation
------------

Manual configure, compile and install:

	$ ./configure

Alternatively, for Gnome integration, run configure with:

	$ ./configure --enable-gtk

Or for KDE use:

	$ ./configure --enable-kde

To compile:

	$ make

Then as root:

	# make install-strip

Finally, you may want to invoke the setup script with normal privileges:

	$ sh/setup

Or manually copy res/piedockrc.sample to ~/.piedockrc and modify it to
meet your needs.



--------------
These instructions taken from the original author's website - http://www.markusfisch.de/
You may easily clone the project by running:

````
$ git clone git://github.com/markusfisch/PieDock
````

###Requirements
Requires a C++ compiler, headers and libraries of X11 and libpng. Xft and the X Rendering Extension (to make use of a compositing manager) are optional.

Runs on Linux, BSD and Solaris.

###
Installation
Download tarball above
Unpack tarball:
$ tar xjvf piedock-x.x.x.tar.bz2
Change into the new directory "piedock-x.x.x" and compile it:
$ cd piedock-x.x.x
$ ./configure
$ make
If everything went well, install as root:
# make install
Now you need to set up your configuration, either manually (see below) or by running the enclosed setup script:
$ sh/setup
Configuration
Find some icons (approx. 128x128 Pixels) in PNG format. I'd recommend those places:
http://www.iconfinder.com/
http://www.iconarchive.com/
http://findicons.com/
http://www.iconfactory.com
http://www.smashingmagazine.com/tag/icons/
http://tango.freedesktop.org/
http://www.kde-look.org
http://www.deviantart.com
http://www.pixelgirlpresents.com/icons
http://interfacelift.com/icons

You may use GIMP to convert XP icons; OS X icons can be converted by gthumb or ImageMagick.
Create a directory named ".piedock" in your home directory:

````
$ mkdir ~/.piedock
````
Place all your PNG icons into this directory

Create a ".piedockrc" configuration file in your home directory; you may use the enclosed "res/piedockrc.sample" as a template:

````
$ cp res/piedockrc.sample ~/.piedockrc
````

Edit ".piedockrc" to meet your requirements. The format of the file is very simple: Each line begins with a statement and continues with space-seperated arguments to this statement. If an argument has spaces, it must be enclosed in quotes, just like you do on the command line. There are only two statements that are important: icon and alias.

Use the icon statement to specify persistent icons in the menu. Normally an icon would only appear if there is a corresponding window. icon icons do always appear. The statement accepts two arguments: the name of the application (which must also be the name of the icon in "~/.piedock/") and, optionally, a string to launch the application if the first argument isn't enough to do that (i.e. a path is required or you want to give some arguments).
The alias directive allows you to recognize windows that do not give the correct name of their corresponding executable. Every application window in X11 should have a resource with it's name in it (the so-called class hints for the interested).

Unfortunately, this name may differ from the name of the executable which is where alias comes in. alias accepts two arguments: a string for recognition and the true name of the executable. The recognition string may be prefixed by another argument (either name, class or title) to specifiy the property which the string is checked against.
There is a "utils" subdirectory which contains a helpful utitlity to find the right settings. Just change into this directory and do:

````
$ ./piedockutils -l
````

A list of all open windows with their properties will be displayed. Now you can use those values (always prefer the class or name property) to set up aliases for windows which doesn't get recognized the right way.

If you have some unused button on your mouse, I suggest you specify its number to the trigger button directive like this:
````
trigger button (number of mouse button)
````
You may find the right number by using the xev utitlity. Then you can open the pie menu by clicking that button.


License
-------

PieDock is open source and licensed under the
[MIT license](http://www.opensource.org/licenses/mit-license.php).
