Mali tarballs are sometimes terribly packaged.
For unknown reasons all the files have Read-Write-Execute flags.

So before copying the file, some operations need to be done once you've
unpacked the tarball. Do not unpack it directly in the kernel tree...
In the extracted tarball folder :
```bash
find . -type 'd' -exec chmod 0755 {} ';'
find . -type 'f' -exec chmod 0644 {} ';'
find . -name 'sconscript' -exec rm {} ';'
find . -name "license.txt" -exec rm {} ';'
find . -name 'patches' -type 'd' -exec rm -r {} ';'
```

Once these operations done, you can copy the content of the extracted
'kernel' sub-folder in the linux kernel tree.

Then, apply the PostMali patch provided in the patches folder, to 
update the Kconfig and Kbuild files, in order to enable the :
* selection of Mali options in the configuration menus
* compilation of Mali drivers during the kernel compilation

