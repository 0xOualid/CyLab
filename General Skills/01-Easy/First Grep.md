# First Grep Writeup

> Can you find the flag in the file? This would be really tedious to look through manually, something tells me there is a better way. 
> The flag is in this [file](https://challenge-files.picoctf.net/c_fickle_tempest/b8915fc817a2cd58e83d7e779515ed3f898738d12cf1974086f8ba3f515ae3cf/file).

## Solution

```shell
wget "https://challenge-files.picoctf.net/c_fickle_tempest/b8915fc817a2cd58e83d7e779515ed3f898738d12cf1974086f8ba3f515ae3cf/file"
```

```shell
cat file | grep -oP "pico.*}"
```

```text
picoCTF{grep_is_good_to_find_things_beD770f5}
```

