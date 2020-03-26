# caesar

## Challenge
Decrypt this message. You can find the ciphertext in /problems/caesar_3_33108a6b0f87eb4b3606437d06290815 on the shell server.

## Solution
Quick bash script to find something that look readible.
```
#!/bin/bash
  
str='ynkooejcpdanqxeykjrubvtagp'

for i in {1..20}; do
        echo $str | caesar $i
done
```
`picoCTF{crossingtherubiconvyfzxekt}`