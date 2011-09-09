===== Doxygen =====

[[http://www.doxygen.org|Doxygen]] is a popular documentation generation tool. It works by using specially formatted comments within the code that are then used by doxygen for generation. With little effort, excellent and nice looking documentation can be done.

While no special tool is required to write doxygen-formatted comments, a lot of time can be saved if your editor supports the auto-completion of such comments. Auto-completion of doxygen comments is supported by [[eclipse|Eclipse IDE]].
# Installation

Doxygen binaries are available for Linux, Windows and Mac OS X on the [doxygen download page](http://www.stack.nl/~dimitri/doxygen/download.html#latestsrc). It is also available for most Linux distributions, and Mac OS X users can also install it from macports.

In order to generate graphs, you will also need to have [graphviz](http://www.graphviz.org/) installed. Doxygen will use the "dot" program that comes with graphviz, so make sure it is in your system's path.

# Configuration

Doxygen uses a configuration file called "Doxyfile" by default. The Doxyfile for FreeRDP can be found in doc/Doxyfile. It can be tweaked to your needs easily, just open it in a text editor and read the instructions beside each option. For instance, if you do not have graphviz installed on your computer and want to generate documentation without graphs, you can change the "HAVE_DOT" option in the Doxyfile.

# Generation

To generate documentation, open a terminal and move to the location of the Doxyfile (doc directory). At that location, all you need to enter is the command "doxygen", which will use the Doxyfile in the current directory and generate HTML documentation in a new "api" folder. More output options can be added, such as RTF or PDF output, if you modify the Doxyfile accordingly. Once generated, you can open doc/api/index.html in a web browser to browse the newly generated documentation.
