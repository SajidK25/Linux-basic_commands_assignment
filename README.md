# Linux-basic commands assignment

## Create a user with user group
```shell
sudo adduser devops
sudo addgroup dev
sudo usermod -aG dev devops
getent group devops
getent group dev
```
## Create two directories in user's home directory named os-concepts and ubuntu-is-the-best
```shell
cd /home/devops
sudo mkdir os-concepts ubuntu-is-the-best
ls -al
total 28
drwxr-xr-x 4 devops devops 4096 অক্টোবর    7 19:17 .
drwxr-xr-x 8 root   root   4096 অক্টোবর    7 18:47 ..
-rw-r--r-- 1 devops devops  220 অক্টোবর    7 18:47 .bash_logout
-rw-r--r-- 1 devops devops 3771 অক্টোবর    7 18:47 .bashrc
drwxr-xr-x 2 root   root   4096 অক্টোবর    7 19:17 os-concepts
-rw-r--r-- 1 devops devops  807 অক্টোবর    7 18:47 .profile
drwxr-xr-x 2 root   root   4096 অক্টোবর    7 19:17 ubuntu-is-the-best
```
## Create two files on each directory
```shell
tech99@tech99:/home/devops$ sudo touch os-concepts/file1 ubuntu-is-the-best/file2
tech99@tech99:/home/devops$ ls -al os-concepts/
total 8
drwxr-xr-x 2 root   root   4096 অক্টোবর    7 22:42 .
drwxr-xr-x 4 devops devops 4096 অক্টোবর    7 19:17 ..
-rw-r--r-- 1 root   root      0 অক্টোবর    7 22:42 file1
tech99@tech99:/home/devops$ ls -al ubuntu-is-the-best/
total 8
drwxr-xr-x 2 root   root   4096 অক্টোবর    7 22:42 .
drwxr-xr-x 4 devops devops 4096 অক্টোবর    7 19:17 ..
-rw-r--r-- 1 root   root      0 অক্টোবর    7 22:42 file2
tech99@tech99:/home/devops$ sudo touch os-concepts/file3 ubuntu-is-the-best/file4
tech99@tech99:/home/devops$ ls -al os-concepts/
total 8
drwxr-xr-x 2 root   root   4096 অক্টোবর    7 22:45 .
drwxr-xr-x 4 devops devops 4096 অক্টোবর    7 19:17 ..
-rw-r--r-- 1 root   root      0 অক্টোবর    7 22:42 file1
-rw-r--r-- 1 root   root      0 অক্টোবর    7 22:45 file3
tech99@tech99:/home/devops$ ls -al ubuntu-is-the-best/
total 8
drwxr-xr-x 2 root   root   4096 অক্টোবর    7 22:45 .
drwxr-xr-x 4 devops devops 4096 অক্টোবর    7 19:17 ..
-rw-r--r-- 1 root   root      0 অক্টোবর    7 22:42 file2
-rw-r--r-- 1 root   root      0 অক্টোবর    7 22:45 file4
```
## List the files with detailed information ( including file permission )
```shell
tech99@tech99:/home/devops$ ls -al os-concepts/
total 8
drwxr-xr-x 2 root   root   4096 অক্টোবর    7 22:45 .
drwxr-xr-x 4 devops devops 4096 অক্টোবর    7 19:17 ..
-rw-r--r-- 1 root   root      0 অক্টোবর    7 22:42 file1
-rw-r--r-- 1 root   root      0 অক্টোবর    7 22:45 file3
tech99@tech99:/home/devops$ ls -al ubuntu-is-the-best/
total 8
drwxr-xr-x 2 root   root   4096 অক্টোবর    7 22:45 .
drwxr-xr-x 4 devops devops 4096 অক্টোবর    7 19:17 ..
-rw-r--r-- 1 root   root      0 অক্টোবর    7 22:42 file2
-rw-r--r-- 1 root   root      0 অক্টোবর    7 22:45 file4
```
## Update file permission so that owner can read,write and group can only read and others can not do anything
```shell
tech99@tech99:/home/devops$ sudo chmod 740 -R os-concepts/
tech99@tech99:/home/devops$ sudo chmod 740 -R ubuntu-is-the-best/
tech99@tech99:/home/devops$ ls -al os-concepts/
ls: cannot open directory 'os-concepts/': Permission denied
tech99@tech99:/home/devops$ sudo ls -al os-concepts/
total 8
drwxr----- 2 root   root   4096 অক্টোবর    7 22:45 .
drwxr-xr-x 4 devops devops 4096 অক্টোবর    7 19:17 ..
-rwxr----- 1 root   root      0 অক্টোবর    7 22:42 file1
-rwxr----- 1 root   root      0 অক্টোবর    7 22:45 file3
tech99@tech99:/home/devops$ sudo ls -al ubuntu-is-the-best/
total 8
drwxr----- 2 root   root   4096 অক্টোবর    7 22:45 .
drwxr-xr-x 4 devops devops 4096 অক্টোবর    7 19:17 ..
-rwxr----- 1 root   root      0 অক্টোবর    7 22:42 file2
-rwxr----- 1 root   root      0 অক্টোবর    7 22:45 file4
```
## Create another group
```shell
tech99@tech99:/home/devops$ sudo addgroup sqa
[sudo] password for tech99: 
Adding group `sqa' (GID 1007) ...
Done.
```
## Update file ownership to the newly created group
```shell
tech99@tech99:/home/devops$ sudo chown :sqa -R os-concepts/
tech99@tech99:/home/devops$ ls -al os-concepts/
ls: cannot open directory 'os-concepts/': Permission denied
tech99@tech99:/home/devops$ sudo ls -al os-concepts/
total 8
drwxr----- 2 root   sqa    4096 অক্টোবর    7 22:45 .
drwxr-xr-x 4 devops devops 4096 অক্টোবর    7 19:17 ..
-rwxr----- 1 root   sqa       0 অক্টোবর    7 22:42 file1
-rwxr----- 1 root   sqa       0 অক্টোবর    7 22:45 file3
tech99@tech99:/home/devops$ sudo ls -al ubuntu-is-the-best/
total 8
drwxr----- 2 root   root   4096 অক্টোবর    7 22:45 .
drwxr-xr-x 4 devops devops 4096 অক্টোবর    7 19:17 ..
-rwxr----- 1 root   root      0 অক্টোবর    7 22:42 file2
-rwxr----- 1 root   root      0 অক্টোবর    7 22:45 file4
tech99@tech99:/home/devops$ sudo chown :sqa -R ubuntu-is-the-best/
tech99@tech99:/home/devops$ sudo ls -al ubuntu-is-the-best/
total 8
drwxr----- 2 root   sqa    4096 অক্টোবর    7 22:45 .
drwxr-xr-x 4 devops devops 4096 অক্টোবর    7 19:17 ..
-rwxr----- 1 root   sqa       0 অক্টোবর    7 22:42 file2
-rwxr----- 1 root   sqa       0 অক্টোবর    7 22:45 file4
```
