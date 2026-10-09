# strings it Writeup

> Can you find the flag in [file](https://challenge-files.picoctf.net/c_fickle_tempest/094a1db42d5ae681cd9e513dcbea2d997495dd3763d50c643b939923ca86e29b/strings) without running it?

## Solution

```shell
wget "https://challenge-files.picoctf.net/c_fickle_tempest/094a1db42d5ae681cd9e513dcbea2d997495dd3763d50c643b939923ca86e29b/strings"
```

```shell
strings strings | grep "pico"
```

```text
picoCTF{5tRIng5_1T_47948C73}
```

