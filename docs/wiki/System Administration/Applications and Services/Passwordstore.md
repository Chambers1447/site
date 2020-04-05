### Setting up:

```
gpg2 --full-gen-key	
pass init user@email.com
pass git init
```

> Might have to use `gpg` on certain distributions

### Set up Git:
#### ***On Git server***

```
apt install git
adduser git
```

#### ***Local Machine***

```
ssh-keygen -t ed25519
ssh-copy-id git@serverIP
```

#### ***On Git server***

```
git init --bare pass-repo
```

#### ***Local Machine***

```
pass git remote add origin ssh://git@serverIP:/home/git/pass-repo
pass git push -u --all
```

### ***To set up on another machine:***

```
gpg2 --export-secret-keys > secret.gpg 	#might have to use gpg on older kernels
ssh-keygen -t ed25519
ssh-copy-id git@serverIP
git clone ssh://git@serverIP:/home/git/pass-repo ~/.password-store
```
