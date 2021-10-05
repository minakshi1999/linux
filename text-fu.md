<details>
<summary>
1.<b>stdout</b>(standard out)
</summary>

```bash
$ echo hello world         
  # this prints out Hello World to the screen
```
```bash
$ echo hello world > file.txt
  # It allows us to send the output of echo Hello World to a file instead of the screen
```

>The > is a redirection operator that allows us the change where standard output goes.  If the file does not already exist it will create it for us. However, if it does exist it will overwrite it (you can add a shell flag to prevent this depending on what shell you are using).

>Well let's say I didn't want to overwrite my file.txt, luckily there is a redirection operator for that as well, >>:

```bash
$ echo hello world >> file.txt 
    #This will append Hello World to the end of the peanuts.txt file, if the file doesn't already exist it will create it for us like it did with the > redirector!
```
> '>' stdout redirection symbol \
'<' stdin redirection symbol \
'2>' stderr redirection symbol \
> '>>' append symbol
</details>
<details>
<summary>2.<b>stdin</b>(standard in)
</summary>

```bash
$ cat > file.txt  #input text
$ cat file.txt    #show content
$ cat file.txt > file2.txt  
#redirect content of file to file2 or canbe overright it
$ cat file.txt >> file3.txt # append content of file to file3
```
</details>
<details>
<summary>3.<b>stderr</b>(standard error)</summary>

> file descriptor for stdin, stdout and stderr is 0, 1, and 2 respectively.\
>if we want to redirect our stderr to the file we can do this:

```bash
$ ls /fake/directory 2> file.txt
```
> if I wanted to see both stderr and stdout in the peanuts.txt file
```bash
$ ls /fake/directory > file.txt 2>&1
```
>There is a shorter way to redirect both stdout and stderr to a file:
```bash
$ ls /fake/directory &> file.txt
```
</details>

<details>
<summary>
4. <b>pipe and tee</b> </summary>

> it be nice if we could just see the output in another command like less
```bash
$ ls -la /etc | less 
```
>You should see the output of ls on your screen and if you open up the peanuts.txt file you should see the same information!

```bash
$ ls | tee file.txt
$ ls | tee file1.txt file2.txt
```
</details>

<details>
<summary>
5.<b>env</b>(Environment variable)
</summary>

>This outputs a whole lot of information about the environment variables you currently have set. These variables contain useful information that the shell and other processes can use.

```bash
$ env
```
example 

```bash
$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/bin
```
</details>

<details>
<summary>
6.<b>cut</b>
</summary>

>cut command extracts portions of text from a file.

To extract contents by a list of characters: -c --> character
```bash
$ cut -c 5 file.txt
$ cut -c 5-10 file.txt
$ cut -c -5 file.txt
$ cut -c 5- file.txt
```
To extract the contents by a field,  -f --> field  -d --> delimiter  by default TAB is used as a delimiter.
```bash
$ cut -f 2 file.txt
$ cut -f 1 -d ';' file.txt
$ cut -f 2 -d ',' file.txt
$ cut -f 2 -d ' ' file.txt
```
</details>

<details>
<summary>
7.<b>paste</b>
</summary>

>combine all these lines into one line:

```bash
$ paste -s file.txt  #delimited by TAB by default
$ paste -d ' ' -s file.txt #everything should be on one line delimited by spaces
$ paste -d ';' -s file.txt  # delimited by ';'
```
</details>
<details>
<summary>
8.<b>head</b>
</summary>

>the head command will show you the first 10 lines in a file.
```bash
$ head /var/log/syslog
```

>You can also modify the line count to whatever you choose, let's say I wanted to see the first 15 lines instead.
```bash
$ head -n 15 /var/log/syslog #-n flag stands for number of lines.
```
</details>

<details>
<summary>
9.<b>tail</b>
</summary>

>Similar to the head command, the tail command lets you see the last 10 lines of a file by default.
```bash
$ tail /var/log/syslog
```

Along with head you can change the number of lines you want to see.
```bash
$ tail -n 10 /var/log/syslog
```

Another great option you can use is the -f (follow) flag, this will follow the file as it grows. Give it a try and see what happens.
```bash
$ tail -f /var/log/syslog
```

Your syslog file will be continually changing while you interact with your system and using tail -f you can see everything that is getting added to that file.
</details>

<details>
<summary>
10.<b>expand and unexpand</b>
</summary>

>To change your TABs to spaces, use the expand command.
```bash
$ expand sample.txt
```

The command above will print output with each TAB converted into a group of spaces. To save this output in a file, use output redirection like below.
```bash
$ expand sample.txt > result.txt
```
Opposite to expand, we can convert back each group of spaces to a TAB with the unexpand command:
```bash
$ unexpand -a result.txt
```
</details>

<details>
<summary>
11.<b> join and split</b>
</summary>

>The join command allows you to join multiple files together by a common field:
```bash
$ join file.txt file2.txt
```
>You can also split a file up into different files with the split command:
```bash
$ split file.txt
```
</details>

<details>
<summary>
12.<b> sort</b>
</summary>

>The sort command is useful for sorting lines.
<pre>
file1.txt

dog
cow
cat
elephant
bird

</pre>
```bash
$ sort file1.txt

bird
cat
cow
dog
elephant

```

>You can also do a reverse sort:

```bash
$ sort -r file1.txt

elephant
dog
cow
cat
bird
```

>And also sort via numerical value:
```bash
$ sort -n file1.txt

bird
cat
cow
elephant
dog
```
</details>
<details>
<summary>
13.<b> tr </b>(Translate)
</summary>

>The tr (translate) command allows you to translate a set of characters into another set of characters. 

Let's try an example of translating all lower case characters to uppercase characters.
```bash
$ tr a-z A-Z

hello
HELLO
```

example 2
```bash
$ tr -d ello
hello
h
mellogjk
mgjk

$ tr 1 6
111
666
truy1134
truy6634
```

As you can see we made the ranges of a-z into A-Z and all text we type that is lowercase gets uppercased.
</details>

<details>
<summary>
14.<b> uniq</b> (Unique)
</summary>

>The uniq (unique) command is another useful tool for parsing text.

Let's say you had a file with lots of duplicates:
<pre>
reading.txt

book
book
paper
paper
article
article
magazine
</pre>
And you wanted to remove the duplicates, well you can use the uniq command:
```bash
$ uniq reading.txt

book
paper
article
magazine
```

Let's get the count of how many occurrences of a line:
```bash
$ uniq -c reading.txt

2 book
2 paper
2 article
1 magazine
```
Let's just get unique values:
```bash
$ uniq -u reading.txt

magazine
```
Let's just get duplicate values:
```bash
$ uniq -d reading.txt

book
paper
article
```
**Note : uniq does not detect duplicate lines unless they are adjacent.**
 For eg:

Let's say you had a file with duplicates which are not adjacent:
<pre>
reading.txt

book
paper
book
paper
article
magazine
article
</pre>
```bash
$ uniq reading.txt

reading.txt

book
paper
book
paper
article
magazine
article
```

The result returned by uniq will contain all the entries unlike the very first
example.

To overcome this limitation of uniq we can use sort in combination with uniq:
```bash
$ sort reading.txt | uniq

article
book
magazine
paper
```
</details>

<details>
<summary>
15.<b> wc and nl</b>
</summary>

>The wc (word count) command shows the total count of words in a file.
```bash
$ wc /etc/passwd

 96     265    5925 /etc/passwd
```

It display the number of lines, number of words and number of bytes, respectively.

To just see just the count of a certain field, use the -l, -w, or -c respectively.
```bash
$ wc -l /etc/passwd
96
$ wc -w /etc/passwd
265
$ wc -c /etc/passwd
5925
```

Another command you can use to check the count of lines on a file is the nl (number lines) command.

file1.txt

i
like
turtles
```bash
$ nl file1.txt

1. i
2. like
3. turtles
```
<i>
Difference bet wc and nl: 
- wc count blank line in number of lines
- nl count only actual line not blank line in number of lines
</i>

>you get the total count of lines by using the nl file without searching through the entire output
```bash
$ nl file.txt | tail -n 1
```
</details>

<details>
<summary>
16.<b>grep</b>
</summary>

> It allows you to search files for characters that match a certain pattern.

```bash
$ grep fox sample.txt #You should see that grep found fox in the sample.txt file.
```

You can also grep patterns that are case insensitive with the -i flag:
```bash
$ grep -i somepattern somefile
```
To get even more flexible with grep you can combine it with other commands with |.
```bash
$ env | grep -i User
```

As you can see grep is pretty versatile. You can even use regular expressions in your pattern:
```bash
$ ls /somedir | grep '.txt$'
#Should return all files ending with .txt in somedir.
```
</details>