# Developer Command Line Tools Overview

This project is a descriptive list of what I find to be the most useful command line tools for software development.

If you aren't familiar with using command line tools, I'm hoping this can be a good place for you to get started.

I'll try to order them with the simplest / most frequently used at the top.

It's likely that there'll be some crossover between commands that are programs and built-in shell commands. I'm generally using `bash`, so when there's built-in stuff here, that's the shell I'm assuming.


# Not covered

The following are assumed knowledge.

* How to move around the file system and list files: `cd`, `pwd`, `ls`.
* Creating, deleting, moving/renaming files: `touch`, `rm`, `mv`, `mkdir`, `rmdir`.
* Shell wildcards (`*`, `?`, `[...]`)
* The standard I/O steams: stdin, stdout, stderr


# Tools


## man

The command that explains all other commands!
Use it to get explanation of what commands do, and the options available for using them.

Example: Read the manual for `mkdir`:
```
$ man mkdir

MKDIR(1)                  BSD General Commands Manual                 MKDIR(1)

NAME
     mkdir -- make directories

SYNOPSIS
     mkdir [-pv] [-m mode] directory_name ...

DESCRIPTION
     The mkdir utility creates the directories named as operands, in the order specified, using mode rwxrwxrwx (0777) as modified by the current umask(2).

     The options are as follows:
...
```


## cat

Print & concatenate files to stdout.

Example: Print README.md to stdout:
```
$ cat README.md
```

Example: Concatenate and print all `.json` files in the `traces` current directory to stdout:
```
$ cat traces/*.json
```

If you don't give `cat` any arguments, it will read from stdin, which can be useful for writing what you type/paste into a file.

Example: Append the lines I paste into `~/.bashrc` (press CTRL+D to end):
```
$ cat >> ~/.bashrc
alias ll='ls -al'
function jql() {
        jq < $1 | less
}
^D
```


## head 

Print just the lines at the start of a file or files or stdin.
Defaults to printing 10 lines.

Example: Print the first 10 lines of `trace.json`:
```
$ head trace.json
```

Example: Print the first line of every `.xml` file:
```
$ head -1 *.xml
```

Example: Print the first 30 lines of stdin:
```
$ cat /usr/share/dict/words | head -30
```


## tail

The opposite of `head`, printing the last lines of a file

Example: Print the lasy 10 lines of `trace.json`:
```
$ tail trace.json
```

Example: Print the last line of every `.csv` file (without printing a header for each file):
```
$ tail -q -1 *.csv
```

`tail` has the added power of being able to *follow* the end of a file as it is being written to, which can be really useful with log files.
Developers will often talk about "tailing" a file, which usually means watching the end of it as it is written to.

Example: Print the last 100 lines of `application.log` and continue printing new lines as they're added to the file:
```
$ tail -100f application.log
```

Example: Print the last 30 lines of stdin:
```
$ cat /usr/share/dict/words | tail -30
```


## Piping between commands (`|`)

We used a pipe in two examples just above, so I'll explain it briefly.
The pipe operator takes the output (on stdout) of the command on the left and makes it the input (stdin) of the command on the right.

So in this example:
```
$ cat /usr/share/dict/words | head -30
```
the `cat` command writes the contents of the file `/usr/share/dict/words` to stdout, the pipe connects that to stdin of the `head` command, which then prints the first 100 lines of stdin.

Get comfortable with pipes.
They're the command-connecting super-power that makes shell scripting a really fast way to write programs with non-trivial data processing logic.


## Writing out to a file (`>`)

TODO


## Reading in from a file (`<`)

TODO


## less

TODO


## echo

TODO


## history

TODO


## History References (`!!` , `!-2` , `!$`)

TODO


## grep / fgrep / egrep

TODO


## wc

TODO


## find

TODO


## ack

TODO


## for

TODO


## while read

TODO


## if

TODO


## popd / pushd

TODO


## xargs

TODO


## jq

TODO


# License

This content is licensed under the [Creative Commons Attribution Non-Commercial Share-Alike Version 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.

---

© 2021 Graham Lea. All rights reserved.
