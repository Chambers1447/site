# Remove ^M^M

## Different methods to remove ^M^M
```sh
:%s/\r\(\n\)/\1/g
```
> May need to run this twice

```sh
sed -e "s/^M//" file > newfile
```

```sh
:set ff=unix
:set ff=dos
```

```sh
:1,$s/^M//g
