# SUDO MAKE ME A SANDWICH Writeup

> Can you read the flag? I think you can!
> ssh -p 53351 ctf-player@green-hill.picoctf.net using password 430838f7

## Solution

First we have to login with SSH.

```shell
ssh -p 53351 ctf-player@green-hill.picoctf.net
430838f7
```

```shell
ls -lh flag.txt
```

This shows that only `root` can read the file. So let's check the `sudo` permissions.

```shell
sudo -l
```

```text
User ctf-player may run the following commands on challenge: (ALL) 
NOPASSWD: /bin/emacs
```

This means the user can run `Emacs` as root without password.

```shell
sudo emacs flag.txt
```

```text
picoCTF{ju57_5ud0_17_c2c0d2e2}
```

