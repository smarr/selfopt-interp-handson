Building Languages with Truffle and RPython: Required Software
==============================================================

For the hands-on tutorial, we will need a system prepared with the following
software:

  - git
  - GCC/Clang
  - make
  - Java 8
  - ant
  - Eclipse (or another Java IDE)
  - PyPy (or Python 2.7, if you are very patient)
  - PyGame (optional)
  - PyCharm (or another Python IDE/editor)

For the language implementations themselves, we need TruffleSOM, the Graal
repository, RTruffleSOM, and the RPython(PyPy) source code.

Below is a brief list of installation instructions.


Basic Software Setup
====================

On OS X, git, Clang, and make should be part of the Xcode command line tools.
On Ubuntu, they can be installed with `apt-get install build-essential`.


git
---

TruffleSOM, RTruffleSOM, and my copy of the Graal VM are managed with git.

OS X, MacPorts:     `port install git`  
OS X, Homebrew:     `brew install git`    
Ubuntu:             `apt-get install git`


Java 8
------

Note, Java 8 version 1.8.0_20 to 1.8.0_40 have bugs and are not compatible with
the Ideal Graph Viewer. The latest version should work without problems however.

On OSX, Windows, other Linux Distributions, download and install:
  [Java SE Development Kit 8 Downloads](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

Ubuntu:  
`    sudo add-apt-repository ppa:webupd8team/java`  
`    sudo apt-get update`  
`    sudo apt-get install oracle-java8-installer`

  Note, the latest available version is problematic with IGV, but Java 7 works:
`    sudo apt-get install oracle-java7-installer`  

ant
---

TruffleSOM uses the ant build systems for compilation and loading of libraries.

OS X, MacPorts:  `port install apache-ant`  
OS X, Homebrew:  `brew install ant`  
Ubuntu: `apt-get install ant`

or see [Installing Apache Ant](http://ant.apache.org/manual/install.html)


Eclipse
-------

Eclipse or any other Java IDE of your choice. Eclipse is available here:
  [Eclipse Downloads](http://www.eclipse.org/downloads/)
 
  When in doubt _Eclipse IDE for Java Developers_ or one of the other versions
  with the Java development tools are needed.


PyPy
----

PyPy or Python 2.7 are needed to compile RTruffleSOM. I recommend PyPy, since
it is significantly faster.

OS X, MacPorts:  `port install pypy`  
OS X, Homebrew:  `brew install pypy`

Ubuntu:  
`  sudo add-apt-repository ppa:pypy/ppa`  
`  sudo apt-get update`  
`  sudo apt-get install pypy`

PyGame
------

RPython offers a PyGame-based tool for the inspection of traces. Thus, PyGame
is not strictly necessary, but helpful especially for beginners.

OS X, MacPorts: `port install py-game`  
Ubuntu: `apt-get install python-pygame`

Else, install from source: [PyGame Downloads](http://www.pygame.org/download.shtml)

PyCharm
-------

PyCharm is not strictly necessary, any Python IDE could be used. Other
alternatives include PyDev for Eclipse.

PyCharm can be obtained from [JetBrains](https://www.jetbrains.com/pycharm/).

Setup of the Language Implementations
=====================================

TruffleSOM
----------

You'll need to download and install TruffleSOM on the command line. Note, the
setup won't work from within Eclipse. Eclipse, or more precisely EGit does not
support symlinks, which are used in the TruffleSOM repository

    git clone https://github.com/smarr/TruffleSOM.git
    cd TruffleSOM
    ant develop


Load TruffleSOM in Eclipse
--------------------------

 1. Menu: Import existing project -> Import from Git
 2. Select local repository which was just created.
 3. Click Next (Import existing projects)
 4. Click Finish

Get and Build Graal
-------------------

In the hands-on, I want you to use the Ideal Graph Viewer (IGV) to investigate
the various optimizations. For that, we need the full source of Graal,
otherwise, we could just use prebuilt binaries.

Somewhere adjacent to the TruffleSOM folder:

    # --depth 10 to avoid endless waiting for the download
    git clone --depth 10 https://github.com/smarr/GraalVM.git
    cd GraalVM
    ./rebuild.sh  # the script will ask questions

Prebuilt binaries: http://lafo.ssw.uni-linz.ac.at/builds

RTruffleSOM
-----------

    git clone https://github.com/smarr/RTruffleSOM.git
    cd RTruffleSOM
 
  
RPython Sources
---------------

    wget https://bitbucket.org/pypy/pypy/downloads/pypy-2.4.0-src.tar.bz2
    tar xvf pypy-2.4.0-src.tar.bz2
    export PYPY_DIR=`pwd`/pypy-2.4.0-src/ # PYPY_DIR is used to built RTruffleSOM


