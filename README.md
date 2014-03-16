helper-guides
=============

Collection of stuff learned

Problem: Increase linux open file limits.
Use case: Python throws ```OSError: [Errno 24] Too many open files``` when opening a file.
Solution:

1) Open ```/etc/security/limits.conf```
2) Add the following lines at the end of the file
```
    account_username soft nofile new_hard_limit_number
    account_username hard nofile new_soft_limit_number
```
3) Save and close
4) Open ```/etc/pam.d/common-session``` and ```/etc/pam.d/common-session-noninteractive```
5) Add the following line at the end of both files
```
session required                        pam_limits.so
```
5) Save and close
6) Log out and Log back in
7) Test with ```ulimit -n```
