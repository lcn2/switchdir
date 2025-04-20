# switchdir

switch a directory symlink to a new directory

This tool will cause symdir to point at newdir by replacing dir1 or dir2
with newdir.   The replacement selection of dir1 or dir2 depends on which
directory symdir does NOT initially point at.  If symdir does not point
at either dir1 or dir2, the older of the two or the one that exist or
dir1 is picked for replacement.

Assuming that newdir, symdir, dir1 and dir2 all exist symdir always points
at something consistently thoughout the operation.

Example of: switchdir newdir symdir dir1 dir2

    Before:		        After:

	symdir -> dir1		symdir -> dir2
	dir1			    dir1	(former symdir pointer)
	dir2			    dir2	(new symdir pointer, was newdir)
	newdir

Example of: switchdir newerdir symdir dir1 dir2

    Before:		        After:

	symdir -> dir2		symdir -> dir1
	dir1			    dir1	(new symdir pointer, was newerdir)
	dir2			    dir2	(old symdir pointer, was newdir)
	newerdir

NOTE: The newdir must exist.

NOTE: The dir1 and dir2 (or their parent dirs if they do not exist) must be in the same file system.

NOTE: The symdir symlink can be anywhere.


# To install

```sh
sudo make install
```


# To use

```
/usr/local/bin/switchdir [-h] [-v level] [-V] [-n] [-N] [-t] newdir symdir dir1 dir2

    -h          print help message and exit
    -v level    set verbosity level (def level: 0)
    -V          print version string and exit

    -n          go thru the actions, but do not update any files (def: do the action)
    -N          do not process anything, just parse arguments (def: process something)

    -t		time sync identical files to oldest time

    newdir		the new directory to which symdir should point
    symdir		a symlink that points to dir1 or dir2
    dir1		either the current or previous directory pointed to by symdir
    dir2		either the previous or current directory pointed to by symdir

switchdir version: 1.4.1 2025-03-25
```


# Reporting Security Issues

To report a security issue, please visit "[Reporting Security Issues](https://github.com/lcn2/switchdir/security/policy)".
