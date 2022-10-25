# Library reference

Makefiles: [Top-level](https://github.com/gnustep/tools-make/blob/master/library.make) | [Instance](https://github.com/gnustep/tools-make/blob/master/Instance/library.make) | [Master](https://github.com/gnustep/tools-make/blob/master/Master/library.make)

A **library** is an object that other libraries and applications can link to in order to use functions, classes, and constants from the library.

Tools link against Base (FoundationKit), but not against Gui (AppKit). If you need to link against Gui, use {make:var}`xxx_NEEDS_GUI`. If you need a tool that doesn't link against Base, use an [Objective-C Tool](../ObjCTool.md).

## Creating a tool

```{make:var} TOOL_NAME
The list of all tools in this GNUmakefile.
```

```makefile
include $(GNUSTEP_MAKEFILES)/common.make

TOOL_NAME = <Your tool name here>

include $(GNUSTEP_MAKEFILES)/tool.make
```

(properties)=
## Tool properties

Tool also inherits [Project properties](../Project/Reference.md#properties).

```{make:var} xxx_HEADER_FILES
The list of header filenames that are to be installed with the library. If a filename has a directory path prefixed to it then that prefix will be maintained when the headers are installed. It is up to the user to make sure that the installation directory exists; otherwise, an error will occur when the library is installed, see {make:var}`xxx_HEADER_FILES_INSTALL_DIR`.
```

```{make:var} xxx_HEADER_FILES_DIR
The relative path from the current directory, where the `GNUmakefile` is located, to where the header files specified by {make:var}`xxx_HEADER_FILES` are located. If a filename specified in `xxx_HEADER_FILES` has a directory path prefixed to it then that path will not be removed when the `GNUmakefile` Package accesses the files, so do not specify a path with {make:var}`xxx_HEADER_FILES_DIR` that is already prefixed to the header filenames, see {make:var}`xxx_HEADER_FILES_INSTALL_DIR`. `xxx_HEADER_FILES_DIR` is optional; if blank or undefined, GNUstep make assumes that the relative path to the header files is the current directory where the `GNUmakefile` resides.
```

```{make:var} xxx_HEADER_FILES_INSTALL_DIR
The relative subdirectory path below `GNUSTEP_HEADERS` where the header files are to be installed. If this directory or any of its parent directories do not exist, then the Makefile Package will create them. The Makefile Package prefixes `xxx_HEADER_FILES_INSTALL_DIR` to each of the filenames in `xxx_HEADER_FILES` when they are installed, so if the filenames in `xxx_HEADER_FILES` already have a directory path prefixed then the user is responsible for creating that directory, the Makefile Package will not create. `xxx_HEADER_FILES_INSTALL_DIR` is optional; leaving it blank or undefined, and the Makefile Package assumes that the installation directory is just `GNUSTEP_HEADERS` with no subdirectory.
```