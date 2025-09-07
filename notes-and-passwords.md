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


## Level 1 >> Level 2
```
bandit1@bandit:~$ cat ./-
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
bandit1@bandit:~$
```

Using - as an argument refers to STDIN/STDOUT i.e dev/stdin or dev/stdout .So if you want to open this type of file you have to specify the full location of the file such as `./-` .For eg. , if you want to see what is in that file use `cat ./-`.


## Level 2 >> Level 3

```
bandit2@bandit:~$ ls
--spaces in this filename--
bandit2@bandit:~$ cat ./--spaces\ in\ this\ filename--
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

Using the same method as the last level to display `--spaces in this filename--` into the terminal.


##Level 3 >> Level 4

```
bandit3@bandit:~/inhere$ ls -a
.  ..  ...Hiding-From-You
bandit3@bandit:~/inhere$ cat ...Hiding-From-You
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

Used `ls -a` to show all files, including hidden ones, and then using `cat` to show the password to the next level.3


## Level 4 >> Level 5

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

## Level 5 >> Level 6

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

## Level 6 >> Level 7 

```
bandit6@bandit:~$ find / -group bandit6 -size 33c -user bandit7 2>/dev/null
/var/lib/dpkg/info/bandit7.password
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
bandit6@bandit:~$
```
Here I used `find` to search the file with the given properties of the file with the password. At the end I used `2>/dev/null` so the screen wouldn't get flooded with permision errors. 
1. `2>` means redirect file descriptor 2 (stderr).
2. `/dev/null` is a “black hole” file that discards whatever you send to it.
3. Together: `2>/dev/null` means send all error messages to /dev/null, i.e. hide them.

## Level 7 >> Level 8

```
bandit7@bandit:~$ cat data.txt | grep -i 'millionth'
millionth	dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

I first used `cat` to display the data in the file, following with a pipeline so that the output of `cat` becomes the input of `grep`, where I used `-i` to ignore caps if there were any.


## Level 8 >> Level 9

```
bandit8@bandit:~$ sort data.txt | uniq -u
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```

First I used `sort` to make the xontent of the file readble, then with a pipeline a used `uniq -u` so that the only displayed line is the one that doesn't repeat in the whole file.


## Level 9 >> Level 10

```
bandit9@bandit:~$ sort data.txt | grep -a "===="
f=+n
�U�ʷ>����m�Y弆��ܫr�ti1O�Ȋk���\���M��s�y+�:�d4��{�s%�q;  �{���;��k��hX���Y���%��]�\�s��ŏN�q��ZD�`���""��j,A/�
                                                                                                            ����T�}�~)��c��P��3�P-�6��<"�QL�u��YCTc��в`*B�k0a��9$�v箰_��"�ș�0���FH���SɕˇG����m���Գ
                                                                     F<�T�g7��3����5����h�P��R[!�I�g9�H{y{K_
                                                                                                           �N�%�K�B�ܡ (R[b���SR��ۼ�t�
e���========== password�#`�XNbϑ�g�
^�������Ĥ��u�f���0�S���E��8��|�z�W���M��2��sw�g��1�����:[��T1_�DU�Hy5� 12wȨ*U[p<z�
                                               p"%�s��]�<�`t�z�sB��^@��v(8;����u[BMgUވ$�Ln`�#��ɔ�3b�;^6P����I"^!�֦��ڴ��݁��Knb�A���߱�.��2U��i��l���p�H
                            1��ʗӃ���@�ϑA�]'kpM����h�I�Tl��Dc���Ȅ���r����t�<&��f�k�?��^�^"F�B��!QeZ��մ;����(C�ֲ�A�MQ�*|T�C�M1P�ҟuU{�z�5&~`Op5u{,���v^y���(�g�
s���f�>�9����!?O� �k��|ʖ��*юͮ���,M��c���
                                       �#6�G���wBܚw��Ōz�i�$x�~h�:���h� D���O
                                                                            �n�bd/�x�;���M��	�9�ά��H�b�~�n��q������~J0�"?�S�!أ��zu`0|�~ԟ�n�O7�&��Y"���}+C5�<�3�=�a�LJY��]�7ް�zE�$H�t�.��$ިtb^_5� ef========== the��ف�w�	��tP�!�хoQ_og�~���q^M��5!{��} Q�|�[s}g'���aXJf`�jdN�(\)��}��'���Kľ����R�[�����d����S�<��R
d�3��{��X��h,¹Y"�Ci+�2i���t����¿_���&g��z�|Ã5�ΫR+�$�)x���r�<�,C���|ƧZ�fM�v?,�9��gh��;Յ���5n%Vˎ���bGU�SC�h�d����CP�
����@E`Ɵ"�W-h                                               ��.Gl$�I�
?{�Z�`�փ���k!x��-:݉�L��gS!�5z7O����˵�W�C�H�$Z\�&c���Ĉ�T
                                                       Ƿ��d�P�x���Yρ�������:�-���@ʞ҉
                                                                                   �>/Meu��OG���!=v5~6�Gt��k�w~�/&�<�r�ڝQ��[Rx������1��0}1��E��K�G�FA���-62�4�UQ���B̫}0˝�m���8�h��	W�L�e�P�\1�~Ć�۠��*�>�j�bB��J�Zf�B�.�э��Ϧ�3�l�[F�F�s.'ԣw�+�3�ِk��6�|���̕�)�V�usE�&����e�C�UY�P�7.p~�'X�
LU�D)��$��,�Z�M J.)�D<խ醸BW���'t;�S5vZ��Ƴ#����(u��]9�S-�\dJL o�(��Щ:�y�X�����a\�$��Y�&����W�ݑs�̥�����>8�b��Ҫ�p�R��5�{��]9��p��%�5�b��l�o���u�����_�eHY2*�4Lܤ���`L?�́�>u`9J========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```

I used `sort`, but later found out it wasn't necessary, but used `grep -a` with that option so it wiill treat the input as text.


## Level 10 >> Level 11

`ssh bandit10@bandit.labs.overthewire.org -p 2220`

```
bandit10@bandit:~$ base64 -d data.txt | cat
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
bandit10@bandit:~$
```

I used `base64 -d` to decode the text in `data.txt` to a readable form. Later found out `cat` wasn't necessary.


## Level 11 >> Level 12

`ssh bandit11@bandit.labs.overthewire.org -p 2220`

```
bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```

I used `cat data.txt` as an input, so that `tr` could read the contents of the file and decode it. I could've also simply used 
`bandit11@bandit:~$ tr 'A-Za-z' 'N-ZA-Mn-za-m' < data.txt`, this way I'm feeding the contents of `data.txt` into `tr` without using cat.


## Level 12 >> Level 13

```
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ ls
my-data.txt
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ xxd -r my-data.txt compressed-data
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ ls
compressed-data  my-data.txt
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ file compressed-data
compressed-data: gzip compressed data, was "data2.bin", last modified: Fri Aug 15 13:15:53 2025, max compression, from Unix, original size modulo 2^32 584
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ gzip -fd compressed-data
gzip: compressed-data: unknown suffix -- ignored
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ mv compressed-data compressed-data.gz
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ gzip -d compressed-data
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ ls
compressed-data  my-data.txt
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ file compressed-data
compressed-data: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ mv compressed-data compressed-data.bz2
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ bzip2 -d compressed-data.bz2
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ file compressed-data
compressed-data: gzip compressed data, was "data4.bin", last modified: Fri Aug 15 13:15:53 2025, max compression, from Unix, original size modulo 2^32 20480
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ mv compressed-data compressed-data.gz
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ gzip -d compressed-data.gz
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ file compressed-data
compressed-data: POSIX tar archive (GNU)
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ tar -xf compressed-data
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ ls
compressed-data  data5.bin  my-data.txt
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ fil
filan             filefrag          filelife-bpfcc    filetop-bpfcc
file              filegone-bpfcc    fileslower-bpfcc
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ file data5.bin
data5.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ tar -xf data5.bin
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ ls
compressed-data  data5.bin  data6.bin  my-data.txt
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ mv data6.bin data6.bin.bz2
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ bzip2 -d data6.bin.bz2
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ ls
compressed-data  data5.bin  data6.bin  my-data.txt
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ file data6.bin
data6.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ tar -xf data6.bin
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ ls
compressed-data  data5.bin  data6.bin  data8.bin  my-data.txt
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Fri Aug 15 13:15:53 2025, max compression, from Unix, original size modulo 2^32 49
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ mv data8.bin data8.bin.gz
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ gzip -d data8.bin.gz
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ ls
compressed-data  data5.bin  data6.bin  data8.bin  my-data.txt
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ file data8.bin
data8.bin: ASCII text
bandit12@bandit:/tmp/tmp.DVlfk18SPk$ cat data8.bin
The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
```

This was a lengthy one. First I made a temporal directory, copied `data.txt` intp that directory and renamed it to `my-data.txt`. After that I used `xxd` on `my-data.txt` to convert the hexdump into binary and writing it in `compressed-data`. After that I checked which type of file was `compressed-data` so I could rename it with the respective suffix to decompress wither with `bzip2`, `gzip` or `tar` (in the case of `tar` i did'nt have to rename it). I couldn't decompress the file without changing the name first, if that was the case I would've use `bzip2 -d -f file-name` or `gzip -d -f file-name`.


