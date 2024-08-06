# MontaVista Make Ramdisk

This tool creates a ramdisk for booting based upon the needs of the
system and the dependencies of those things.

There are three basic files that drive this, all should be installed
in /usr/share/mvmkramdisk:

1. required_binaries - Binaries that need to be put onto the ramdisk.
   Theis code will look through all the binaries, extract all
   necessary shared libraries, and install all those, too.  These
   mostly have to do with basic functions and setting up disk devices.
   
2. required_modules - Kernel modules that need to be on the ramdisk.
   Again, these are mostly about disk devices.

3. required_files - Files that need to be put onto the ramdisk.  By
   default there aren't any, but it's here just in case.
   
4. init_template - This is the template for the script on the ramdisk
   that is used to install modules, set up RAID, LVM, and other disk
   type things, and then pivot to the main root filesystem.

The ramdisk makes heave use of busybox for basic functions, see the
init_template and mvmkramdisk file for details on what is required
from busybox.
