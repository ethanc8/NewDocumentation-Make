# Resource Set Reference

This is used to install a bunch of resource files somewhere.  It is
different from a bundle without resources; in a bundle without
resources, we first create the bundle in the build directory, then
copy the build to the install dir, overwriting anything already
there.  This instead will install the separate resource files
directly in the installation directory; it's more efficient as it
doesn't create a local bundle, and it doesn't overwrite an existing
bundle in the installation directory.

```{note}
`Info-gnustep.plist` and `Info.plist` are NOT considered resource files.
These files are generated automatically by certain projects, and if you
want to insert your own entries into `Info-gnustep.plist` or `Info.plist`
you should create a `xxxInfo.plist` file (where `xxx` is the application name)
in the same directory as your makefile, and gnustep-make will automatically
read it and merge it into the generated `Info-gnustep.plist`.
For more detail, see rules.make.
```

## Creating a resource set

