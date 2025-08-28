# Over the wire: bandit
**https://overthewire.org/wargames/bandit/bandit1.html**

To log on the game type the following
```
ssh bandit0@bandit.labs.overthewire.org -p 2220
```
It will ask your for the password. It is `bandit0`


# Notes

**Level 0 >> Level 1**
```
The password you are looking for is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```


**Level 1 >> Level 2**
```
bandit1@bandit:~$ cat ./-
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
bandit1@bandit:~$
```

Using - as an argument refers to STDIN/STDOUT i.e dev/stdin or dev/stdout .So if you want to open this type of file you have to specify the full location of the file such as `./-` .For eg. , if you want to see what is in that file use `cat ./-`.


**Level 2 >> Level 3**

```
bandit2@bandit:~$ ls
--spaces in this filename--
bandit2@bandit:~$ cat ./--spaces\ in\ this\ filename--
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

Using the same method as the last level to display `--spaces in this filename--` into the terminal.


**Level 3 >> Level 4**

```
bandit3@bandit:~/inhere$ ls -a
.  ..  ...Hiding-From-You
bandit3@bandit:~/inhere$ cat ...Hiding-From-You
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

Used `ls -a` to show all files, including hidden ones, and then using `cat` to show the password to the next level.3


**Level 4 >> Level 5**

```
bandit4@bandit:~/inhere$ ls
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
bandit4@bandit:~/inhere$ file ./-file00
./-file00: data
bandit4@bandit:~/inhere$ file ./-file00 ./-file01
./-file00: data
./-file01: data
bandit4@bandit:~/inhere$ file ./-file02 ./-file03 ./-file04 ./-file05 ./-file06 ./-file07 ./-file08 ./-file09
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
bandit4@bandit:~/inhere$ cat ./-file07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

Using `ls` I listed all the files to get their names. After that I used `file` to check wich type of file each one is. At the end I simply used `cat` to show the password for the next level.

**Level 5 >> Level 6**

```
bandit5@bandit:~$ ls
inhere
bandit5@bandit:~$ cd inhere/
bandit5@bandit:~/inhere$ ls
maybehere00  maybehere03  maybehere06  maybehere09  maybehere12  maybehere15  maybehere18
maybehere01  maybehere04  maybehere07  maybehere10  maybehere13  maybehere16  maybehere19
maybehere02  maybehere05  maybehere08  maybehere11  maybehere14  maybehere17
bandit5@bandit:~/inhere$ find . type -size 1033k
find: ‘type’: No such file or directory
bandit5@bandit:~/inhere$ find . -size 1033b
bandit5@bandit:~/inhere$ find . -size 1033c
./maybehere07/.file2
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

After changing directory to `inhere`, I used `ls` to see how many directories and files were. Then I used `find` to find the file based on the properties it had, like 1033 bytes. I used `.` refering to the `inhere` directory, `-size` to refer the size of the file and with `1033c` `1033` is the number and `c` at the end is the type of unit (in this case bytes).

**Level 6 >> Level 7**



