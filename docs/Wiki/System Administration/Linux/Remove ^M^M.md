### Different methods to remove ^M^M

```
:%s/\r\(\n\)/\1/g
```
> May need to run this twice

```
sed -e "s/^M//" file > newfile
```

```
:set ff=unix
:set ff=dos
```

```
:1,$s/^M//g
