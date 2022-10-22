# Project Types

```{toctree}
---
caption: Contents
hidden: true
---
Project/Reference.md
ResourceSet/Reference.md
Tool/Reference.md
Library/index.md
```

## Common Types

* [Project](Project/Reference.md)
    * [Tool](Tool/Reference.md)
    * Application
    * [Library](Library/Reference.md)

## Inheritance Hierarchy

* [Project](Project/Reference.md)
    * CTool - does *not* inherit from Tool
    * Documentation
    * 
    * SharedBundle
        * Bundle
        * [ResourceSet](ResourceSet/Reference.md)
        * Application
        * GSWebApplication
        * [Library](Library/Reference.md)
            * CLibrary
        * Palette
        * Service
        * Subproject
        * [Tool](Tool/Reference.md)
    * SharedHeaders
        * Bundle
        * Framework
        * GSWebBundle - deprecated
        * [Library](Library/Reference.md)
            * CLibrary
        * Subproject
    * SharedStrings
        * Bundle
        * Framework
        * Application
        * GSWebApplication
        * GSWebBundle - deprecated
        * [Library](Library/Reference.md)
            * CLibrary
        * ObjCTool
        * Palette
        * Service
        * Subproject
        * [Tool](Tool/Reference.md)
    * SharedJava
        * JavaTool
        * JavaPackage
    * SharedPkgConfig
        * Framework
        * [Library](Library/Reference.md)
            * CLibrary

The make library has some Shared* things that are *not* in the inheritance hierarcy, even though they are included by some project types -- they do not define any project type variables.

## Licensing

This file is part of the GNUstep Makefile Package.

This library is free software; you can redistribute it and/or
modify it under the terms of the GNU General Public License
as published by the Free Software Foundation; either version 3
of the License, or (at your option) any later version.
  
You should have received a copy of the GNU General Public
License along with this library; see the file COPYING.
If not, write to the Free Software Foundation,
51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.
    