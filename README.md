[![Build Status](https://travis-ci.org/flightaware/speedbag.svg?branch=master)](https://travis-ci.org/flightaware/speedbag)

This is speedbag, a package for providing accelerated C-based routines for
many common Tcl operations.


Using the speedbag interface
---


```tcl
package require Speedbag

::speedbag::tsv_to_array $line arrayName
```

...splits a tab-separate line of key-value pairs into an array and returns the
number of key-value pairs imported.

It's an error if there is an uneven number of elements.


Bugs
---


Contents
---

Makefile.in	Makefile template.  The configure script uses this file to produce the final Makefile.

README		This file

aclocal.m4	Generated file.  Do not edit.  Autoconf uses this as input when generating the final configure script.  See "tcl.m4" below.

configure	Generated file.  Do not edit.  This must be regenerated anytime configure.in or tclconfig/tcl.m4 changes.

configure.in	Configure script template.  Autoconf uses this file as input to produce the final configure script.

generic/speedbag.c	speedbag functions
generic/tclspeedbag.c  Tcl initialization for speedbag functions

generic/speedbag.h	Header files for the speedbag interface.


tclconfig/	This directory contains various template files that build the configure script.  They should not need modification.

install-sh	Program used for copying binaries and script files to their install locations.

tcl.m4		Collection of Tcl autoconf macros.  Included by aclocal.m4 to define SC_* macros.

UNIX build
---

Building under most UNIX systems is easy, just run the configure script
and then run make. 

	$ cd speedbag
	$ ./configure
	$ make
	$ make install

Windows build
---

Probably irrelevant

Installation
---

The speedbag package installs like so:

         $exec_prefix
          /       \
        lib       bin
         |         |
   PACKAGEx.y   (dependent .dll files on Windows)
         |
  pkgIndex.tcl (.so|.dll files)

The main .so|.dll library file gets installed in the versioned PACKAGE directory, which is OK on all platforms because it will be directly referenced with by 'load' in the pkgIndex.tcl file.  Dependent DLL files on Windows must go in the bin directory (or other directory on the user's PATH) in order for them to be found.

