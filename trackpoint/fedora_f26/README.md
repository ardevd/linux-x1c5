This patch is for the Fedora 26 kernel. To use it you have to first checkout the Fedora kernel and switch to the f26 branch.

```
$ fedpkg co -a kernel
$ cd kernel
$ git checkout -b my_kernel origin/f26
``` 

Then use the newpatch.sh script to import the patch.

```
$ ./scripts/newpatch.sh /path/to/patch/0001-Added-support-for-the-X1-Carbon-5-Elantech-trackpoin.patch
```

Finally, build the kernel.

```
fedpkg local
```
