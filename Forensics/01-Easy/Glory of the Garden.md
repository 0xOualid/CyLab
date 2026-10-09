# Glory of the Garden Writeup

> This file contains more than it seems.
> Get the flag from [garden.jpg](https://challenge-files.picoctf.net/c_fickle_tempest/b67cf664cdf2557bea4f1d6079bc099037bc6ea5322afbfc80c5dcf4440c5e7d/garden.jpg).

## Solution

```shell
wget "https://challenge-files.picoctf.net/c_fickle_tempest/b67cf664cdf2557bea4f1d6079bc099037bc6ea5322afbfc80c5dcf4440c5e7d/garden.jpg"
```

It's a normal image so let's check the data of the image.

```shell
strings garden.jpg | grep -i "pico"
```

```text
picoCTF{more_than_m33ts_the_3y398ee229a}
```

