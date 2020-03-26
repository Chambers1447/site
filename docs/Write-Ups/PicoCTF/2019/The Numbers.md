# The Numbers

## Challenge
The numbers... what do they mean?

## Solution
16 9 3 15 3 20 6 { 20 8 5 14 21 13 2 5 18 19 13 1 19 15 14 }

Character position in alphabet.
```
#!/usr/bin/evn python
  
numbers = [ 16, 9, 3, 15, 3, 20, 6, 20, 8, 5, 14, 21, 13, 2, 5, 18, 19, 13, 1, 19, 15, 14 ]
numberlist = ''

for i in numbers:
    numberlist+=chr(i+96)
print(numberlist).upper()
```

This gave me everything except the braces, which are easily put back in manually.

`PICOCTF{THENUMBERSMASON}`