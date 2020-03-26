# vault-door-1

## Challenge
This vault uses some complicated arrays! I hope you can make sense of it, special agent. The source code for this vault is here: VaultDoor1.java

## Solution

In the file each character is by a number so the password can be put back into order.  I just went through a bash one liner to get the correct output.

```
grep password VaultDoor1.java | awk '{print $1 $3}' | grep charAt| cut -d '(' -f2 | sed 's/)/ /g' | sort -n | cut -d' ' -f2 | sed 's/;//g' | sed "s/'//g" | tr -d '\n'
```

`picoCTF{d35cr4mbl3_tH3_cH4r4cT3r5_2487f0}`