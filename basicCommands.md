# **commands**
 1. ### **pwd (print working directory)** 
     >To see where you are, you can use the pwd command, this command means “print working directory” and it just shows you which directory you are in, note the path stems from the root directory.
```bash 
$ pwd 
```
2. ### **cd (change directory)**
 There are two different ways to specify a path, with absolute and relative paths.
 > - Absolute path: This is the path from the root directory.
 ```bash
 $ cd \home\desktop 
 ```
 >- Relative path: This is the path from where you are currently in filesystem.
 ```bash
 $ cd Picture
 ```
 there are some shortcuts to help you out.

>- . (current directory). This is the directory you are currently in.
>- .. (parent directory). Takes you to the directory above your current.
>- ~ (home directory). This directory defaults to your “home directory”. Such as /home/pete.
>- \- (previous directory). This will take you to the previous directory you were just at.

```bash
minak@LAPTOP-83B7EG9K MINGW64 ~/Desktop/Linux (master)
$ cd .

minak@LAPTOP-83B7EG9K MINGW64 ~/Desktop/Linux (master)
$ cd ..

minak@LAPTOP-83B7EG9K MINGW64 ~/Desktop
$ cd -
/c/Users/minak/Desktop/Linux

minak@LAPTOP-83B7EG9K MINGW64 ~/Desktop/Linux (master)
$ cd ~

minak@LAPTOP-83B7EG9K MINGW64 ~
$ cd -
/c/Users/minak/Desktop/Linux

minak@LAPTOP-83B7EG9K MINGW64 ~/Desktop/Linux (master)
$ cd

minak@LAPTOP-83B7EG9K MINGW64 ~
$ cd -
/c/Users/minak/Desktop/Linux

minak@LAPTOP-83B7EG9K MINGW64 ~/Desktop/Linux (master)
$
```
3. ### **ls (list directories)**
>The ls command will list directories and files in the current directory by default, however you can specify which path you want to list the directories of.

```bash
$ ls
$ ls /home/Desktop
```

```bash
$ ls -a  #show hidden files

$ ls -l 
#show you detailed information, starting from the left: file permissions, number of links, owner name, owner group, file size, timestamp of last modification, and file/directory name.

$ ls -al #combination of la -a nad ls -l

$ ls -R # recursively list directory contents

$ ls -r #reverse order while sorting

$ ls -t #sort by modification time, newest first
```

4. ### **touch**
> Touch allows you to the create new empty files.

```bash
$ touch mysuperduperfile
```

>Touch is also used to change timestamps on existing files and directories.

<pre>
minak@LAPTOP-83B7EG9K MINGW64 ~/Desktop
$ touch newFile

minak@LAPTOP-83B7EG9K MINGW64 ~/Desktop
$ ls -l newFile
-rw-r--r-- 1 minak 197609 0 Oct  3 <b>15:02</b> newFile

minak@LAPTOP-83B7EG9K MINGW64 ~/Desktop
$ touch newFile

minak@LAPTOP-83B7EG9K MINGW64 ~/Desktop
$ ls -l newFile
-rw-r--r-- 1 minak 197609 0 Oct  3 <b>15:03</b> newFile
</pre>

5. ### **file**
>To find out what kind of file a file is, you can use the file command. It will show you a description of the file’s contents.

<pre>
minak@LAPTOP-83B7EG9K MINGW64 ~/Desktop/Python
$ file basic.py
basic.py: ASCII text, with no line terminators
</pre>

6. ### **less**
>We can look at the contents of a file with less. Once you’re in the less command, you can actually use other keyboard commands to navigate in the file.

```bash
$ less file_name
```
Use the following command to navigate through less:

>- q - Used to quit out of less and go back to your shell.
>- Page up, Page down, Up and Down - Navigate using the arrow keys and page keys.
>- g - Moves to beginning of the text file.
>- G - Moves to the end of the text file.
>- /search - You can search for specific text inside the text document. Prefacing the words you want to search with /
>- h - If you need a little help about how to use less while you’re in less, use help.

8. ### **cp**

```bash
$ cp source_file dest_dir
$ cp *.extention des_dir
$ cp -r sourcr_dir dest_dir #you need to specify to copy over a directory
$ cp -i src_file dest_dir #You can use the -i flag (interactive) to prompt you before overwriting a file.
```

9. ### **mv (Move)**
>Used for moving files and also renaming them. Quite similar to the cp command in terms of flags and functionality.

You can rename files like this:
<pre>
$ mv oldfile newfile
</pre>

Or you can actually move a file to a different directory:
<pre>
$ mv file2 /home/pete/Documents
</pre>

And move more than one file:
<pre>
$ mv file_1 file_2 /somedirectory
</pre>

You can rename directories as well:
<pre>
$ mv directory1 directory2
</pre>

Like cp, if you mv a file or directory it will overwrite anything in the same directory. So you can use the -i flag to prompt you before overwriting anything.
<pre>
$ mv -i directory1 directory2
</pre>

Let’s say you did want to mv a file to overwrite the previous one. You can also make a backup of that file and it will just rename the old version with a ~.
<pre>
$ mv -b directory1 directory2
</pre>

10. ###  **mkdir (Make Directory)**
>We’re gonna need some directories to store all these files we’ve been working on. The mkdir command (Make Directory) is useful for that, it will create a directory if it doesn’t already exist. 

You can even make multiple directories at the same time.
<pre>
$ mkdir books paintings
</pre>

You can also create subdirectories at the same time with the -p (parent flag).
<pre>
$ mkdir -p books/hemmingway/favorites
</pre>

11. ### **rm (Remove)**

> To remove files you can use the rm command. The rm (remove) command is used to delete files and directories.
<pre>
$ rm file1
</pre>

if you don’t care about any of that, you can absolutely remove a bunch of files.
<pre>
$ rm -f file1
</pre>

Adding the -i flag like many of the other commands, will give you a prompt on whether you want to actually remove the files or directories.
<pre>
$ rm -i file
</pre>

you’ll need to add the -r flag (recursive) to remove all the files and any subdirectories it may have.
<pre>
$ rm -r directory
</pre>

You can remove a directory with the rmdir command.
<pre>
$ rmdir directory
</pre>

