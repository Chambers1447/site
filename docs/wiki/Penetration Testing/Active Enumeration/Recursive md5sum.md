# Recursive `md5sum`

Will run `find` in the current directory and execute an `md5sum` on all files it finds and output to a file named `md5sum.txt`, but will ignore the `md5sum.txt` as it is recursing.

```
find -type f \( -not -name "md5sum.txt" \) -exec md5sum '{}' \; > md5sum.txt
```