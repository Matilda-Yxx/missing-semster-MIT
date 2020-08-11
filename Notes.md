Some notes on The-missing-semester
=======

Lecture 1 Shell commands
-----------

`shebang` line helps the shell to interpret a script.

Some very useful shell programs:

* `man PROGRAM_NAME` program_name: accessing manual page
* `ls -l DIR` listing long info under a directory.
* `OUTPUT > file` wire OUTPUT into the file
* `PROGRAM < file` wire file into the PROGRAM
* `>>` appending to a file
* `|` piping
* `grep KEYWORD DIR` return lines that include the KEYWORD under DIR

Logging in as the root user allow you to do crazier things, via the `sudo` command

Lecture 2 Shell scripting
-----------

* Bash funtions:
 mcd () {
    mkdir -p "$1"
    cd "$1"
}

* Use `$@`, `$#` to manage input arguments
* `!!` execute last command. Often used with `sudo`.
* Command separators: `;` `&` `|`. `;` run the commands sequentially. `&` put the first one in background then run the second command. `|` is piping. For `&&` and `||`, they work like common logical operators. E.g. `cmd1 $$ cmd2` means that cmd2 will run only if cmd1 is successful.
* Saving output of a command: `${CMD}`
* Process substitution: `<(CMD)`
* File name expansion [IMPORTANT]
  * Wildcards: `*` and `?` are interchangable
  * Curly braces: `*.{png,jpg}`

**The find tool is amazing!**

* Find all directories named src
`find . -name src -type d`
* Find all python files that have a folder named test in their path
`find . -path '*/test/*.py' -type f`
* Find all files modified in the last day
`find . -mtime -1`
* Find all zip files with size in range 500k to 10M
`find . -size +500k -size -10M -name '*.tar.gz'`
**Perform actions to the query results**
* Delete all files with .tmp extension
`find . -name '*.tmp' -exec rm {} \;`
* Find all PNG files and convert them to JPG
`find . -name '*.png' -exec convert {} {}.jpg \;`
