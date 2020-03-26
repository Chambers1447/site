# First Grep: Part II.md

## Challenge
Can you find the flag in /problems/first-grep--part-ii_3_b4bf3244c2886de1566a28c1b5a465ae/files on the shell server? Remember to use grep.

## Solution
Just need to recursive grep on the directory.

```
grep -r picoCTF /problems/first-grep--part-ii_3_b4bf3244c2886de1566a28c1b5a465ae/files
```

`picoCTF{grep_r_to_find_this_3675d798}`