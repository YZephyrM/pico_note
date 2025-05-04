# Shell
## in shell command line prompt(from left to right):
- *** (before @) = username
- @*** = device name
- ~("tilde") = home directory (/home/user/)
- $ = separator, separate computer generated prompt and user-written command

## common command:
```
$ date
$ cat [path] --> cat display all text in a file
$ apt install [package name] --> install app
```

**key "TAB" saves time --> auto-complet**

## web explains shell commands
https://explainshell.com/explain?cmd=mv

## other commands:
```
$ wget [URL]      //download files
$ file [filename]     //file type 
$ man [command]       //command instruction
$ grap        // tutorial in https://ryanstutorials.net/linuxtutorial/grep.php
$ find        // tutorial online
$ gzip -d     // unzip .gz file
```
# Forensics
Digital Forensics is the field in cybersecurity that tries to gather and understand evidence after an incident, which can be crime, to determine ho it happend. They focus on gathering evidence prenst in computer devices that hold info electronically.

# .gz VS .zip

## Key diff

1. **Single File vs. Multiple Files**
- .gz:

    - Compresses only one file (e.g., file.txt → file.txt.gz).

    - To compress multiple files, first combine them into a .tar archive (→ .tar.gz).

- .zip:

    - Directly bundles multiple files/folders into one archive (e.g., archive.zip).

2. **Compression Efficiency**:
- .gz: Optimized for text-based files (e.g., logs, JSON, CSS) with high compression ratios.

- .zip: Uses DEFLATE (default) or other algorithms (e.g., BZIP2 in .zipx), trading speed for versatility.

3. **Metadata & Features**:
- .gz: Strips original filename by default (unless using gzip -N).

- .zip: Stores filenames, paths, timestamps, and permissions (Unix).

4. **Encryption**:
- .gz: No built-in encryption.

- .zip: Supports password protection (AES-256 in modern tools like 7-Zip).

## When to Use Which?
- Use .gz if:

    - Compressing single large text files (e.g., server logs).

    - Working in Linux/macOS environments (e.g., gzip -9 file.txt for max compression).

- Use .zip if:

    - Sharing multiple files across OSes (Windows-friendly).

    - Need encryption or metadata preservation.

# Disk analysis

## Main layer disk
- **Media**: the media layer tools all are prepended wih 'mm' and operate on the disk image with little guidance from the analyst. Media is the lowest level, providing key info to access the deeper layers, but not shedding much light on the data contained in teh image. (`mmls` is a media layer tool that gives us the partition table of the image and key info for delving into the other layers)
- **Block**: the block layer is the second lowest level of the four layers considered here. The block layer is the number of the disk image broken into equal-sized chunks. A single file is likely to cotain multiple blocks. (`blkcat` is a block layer tool that outputs the contents of a single block)
- **Inode**: the inode layer is the bookkeeping layer of a disk image. It's like toc, with the capter number being like the inodes, and the pages like blocks of a file. (`icat` is an inode layer tool that outputs a single file based on its inode number)
- **Filename**: the filename layer is one layer that most any user of a computer actually sees and interacts with. (Filename layer tools are prepended by 'f'. `fls` lists the files on an image starting at the root.) 
## Sleuthkit tools
```
$ gzip -d [filename]      //unzip .gz file

$ gunzip [filename]

$ mmls [disk]             //size partions
```

[Sleuthkit docs](http://wiki.sleuthkit.org/index.php?title=TSK_Tool_Overview )


[Challenge-combination-bash-comm-sleuthkit](./challenge/DDS2.md)
