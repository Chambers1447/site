# dont-use-client-side

## Challenge
Can you break into this super secure portal? https://2019shell1.picoctf.com/problem/12280/ (link) or http://2019shell1.picoctf.com:12280

## Solution
If you browse to the page and check the source, you'll see the following and will be able to just piece it back together.

```
    if (checkpass.substring(0, split) == 'pico') {
      if (checkpass.substring(split*6, split*7) == '7743') {
        if (checkpass.substring(split, split*2) == 'CTF{') {
         if (checkpass.substring(split*4, split*5) == 'ts_p') {
          if (checkpass.substring(split*3, split*4) == 'lien') {
            if (checkpass.substring(split*5, split*6) == 'lz_5') {
              if (checkpass.substring(split*2, split*3) == 'no_c') {
                if (checkpass.substring(split*7, split*8) == '1}') {
                  alert("Password Verified")
```

`picoCTF{no_clients_plz_577431}`