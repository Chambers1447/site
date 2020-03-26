# Based

## Challenge
To get truly 1337, you must understand different data encodings, such as hexadecimal or binary. Can you get the flag from this program to prove you are on the way to becoming 1337? Connect with nc 2019shell1.picoctf.com 20836.

## Solution

I used a bash script that utilized perl to convert binary to ascii. I would paste the array in as arguments.
```
#!/bin/bash
  
array=("$@")
string=''

for i in "${array[@]}"
do
        string+=$(echo $i | perl -lape '$_=pack"(B8)*",@F')
done

echo $string
```

A second string is needed and it is octal, so I created another bash script that would take the input and convert it hex, then to ascii, mainly relying on `xxd` to do the ascii conversion.

```
#!/bin/bash
  
array=("$@")
string=''

for i in "${array[@]}"
do
        hex=$(echo "obase=16;ibase=8;$i" | bc)
        string+=$(echo "0x$hex" | xxd -r)
done

echo $string
```

Next portion was hex, and that was just a stripped version of the previous script.

```
#!/bin/bash

array=("$@")
string=''

for i in "${array[@]}"
do
        string+=$(echo "0x$i" | xxd -r)
done

echo $string
```

`picoCTF{learning_about_converting_values_6cdcad0d}`