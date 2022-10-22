# Project Reference

**Inheritance**: Project *(root class)*

**Project** is the root class for all projects. It is defined in `$(GNUSTEP_MAKEFILES)/rules.make`. It doesn't actually exist -- it's more like a protocol.

## Project properties

````{make:var} xxx_COPY_INTO_DIR
By adding the line
```makefile
xxx_COPY_INTO_DIR = ../Vanity.framework/Resources
```
to you GNUmakefile, you cause the after-xxx-all:: stage of
compilation of xxx to copy the created stuff into the *local*
directory `../Vanity.framework/Resources` (this path should be
relative).  It also disables installation of xxx.

This is normally used, for example, to bundle a tool into a
framework.  You compile the framework, then the tool, then you can
request the tool to be copied into the framework, becoming part of
the framework (it is installed with the framework etc).
````

````{make:var} xxx_STANDARD_INSTALL
By setting this to `no`, you can disable the standard installation code
for a certain project.  This can be useful if you are
installing manually in some other way (or for some other reason you
don't want installation to be performed ever) and don't want the
standard installation to be performed.  Please note that
before-xxx-install and after-xxx-install are still executed, so if
you want, you can add your code in those targets to perform your
custom installation.
````

```{make:var} xxx_INSTALL_DIRS
By adding an xxx_INSTALL_DIRS variable you can request additional
installation directories to be created before the first installation
target is executed.  You can also have general
ADDITIONAL_INSTALL_DIRS directories that are always created before
install is executed; this is done top-level in the Master
invocation.
```

````{make:var} xxx_NEEDS_GUI
You can control whether you want to link against the gui library
by using one of the two commands --
```makefile
xxx_NEEDS_GUI = yes
xxx_NEEDS_GUI = no
```
(where 'xxx' is the name of your application/bundle/etc.)

You can also change it for all applications/bundles/etc by doing
```makefile
NEEDS_GUI = yes # (or no)
```
If you don't specify anything, the default for the project type will
be used (this is the NEEDS_GUI = yes/no that is at the top of all
project types' makefiles).

If the project type doesn't specify anything (eg, doesn't need
linking to ObjC libraries, or it is buggy/old or it is from a
third-party and hasn't been updated yet) then the default is NO.
````

```{make:var} xxx_OBJ_FILES
The list of object files that are not produced during the normal compilation stage to link into the resulting binary.
```

```{make:var} xxx_OBJC_FILES
The list of Objective-C source files to be compiled
```

```{make:var} xxx_C_FILES
The list of C source files to be compiled
```

```{make:var} xxx_OBJCC_FILES
The list of Objective-C++ source files to be compiled
```

```{make:var} xxx_CC_FILES
The list of C++ source files to be compiled
```

```{make:var} xxx_PSWRAP_FILES
The list of PostScript Wrap (`.psw`) source files to be compiled into a C source and header file, which will be compiled and added to the project.
```

```{make:var} xxx_JAVA_FILES
The list of Java source files to be compiled into bytecode.
```

```{make:var} xxx_JAVA_JNI_FILES
The list of Java files to be converted into Java JNI headers.
```

% TODO: Figure out what this is.

```{make:var} xxx_WINDRES_FILES
It's unclear what this is for. See the [`windres` man page](https://man7.org/linux/man-pages/man1/windres.1.html).
```

Shared with `ADDITIONAL`*:

* `xxx_BUNDLE_LIBS`
* `xxx_INCLUDE_DIRS`
* `xxx_GUI_LIBS`
* `xxx_TOOL_LIBS`
* `xxx_OBJC_LIBS`
* `xxx_LIBS`
* `xxx_LIBRARY_LIBS`
* `xxx_NATIVE_LIBS`
* `xxx_LIB_DIRS`
* `xxx_CPPFLAGS`
* `xxx_CFLAGS`
* `xxx_OBJCFLAGS`
* `xxx_CCFLAGS`
* `xxx_OBJCCFLAGS`
* `xxx_LDFLAGS`
* `xxx_CLASSPATH`
* `xxx_LIBRARIES_DEPEND_UPON`
