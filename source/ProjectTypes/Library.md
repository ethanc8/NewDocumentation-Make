# Library reference

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

```{make:var} xxx_HAS_RESOURCE_BUNDLE
If this variable is `yes`, then GNUstep Make will build a resource bundle for the tool, and install it. You can then add resources to the tool with the usual xxx_RESOURCE_FILES, xxx_LOCALIZED_RESOURCE_FILES, xxx_LANGUAGES, etc -- see (Resource Set Reference)[../ResourceSet/Reference.md]. `xxx` will be the same as the name of the tool.

The tool resource bundle (and all resources inside it) can be accessed at runtime very comfortably, by using gnustep-base's `[NSBundle mainBundle]` (exactly as you would do for an application).
```

## Global configuration variables

```{make:var} TOOL_INSTALL_DIR
This is the directory where the tool gets installed. If you don't specify a directory it will get installed in the GNUstep Local Root (by default `/usr/GNUstep/Local` on Unix-like systems). The tool executable will get installed in *root*`/Tools`.
```