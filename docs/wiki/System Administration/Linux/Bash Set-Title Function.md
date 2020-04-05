# If you're forced to use `gnome-terminal`

## Add this to `~/.bashrc`

```
function set-title() {
	if [[ -z "$ORIG" ]]; then
		ORIG=$PS1
	fi
	TITLE="\[\e]2;$*\a\]"
	PS1=${ORIG}${TITLE}
}
```

## You then need to source your `~/.bashrc` or restart your terminals

```
source .bashrc
```

## You can now run the following command to set the title to `newtitle`

```
set-title newtitle
```
