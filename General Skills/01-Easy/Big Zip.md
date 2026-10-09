# Big Zip Writeup

> Unzip this archive and find the flag.
> [Download zip file](https://artifacts.picoctf.net/c/505/big-zip-files.zip)

## Solution

```shell
wget "https://artifacts.picoctf.net/c/505/big-zip-files.zip"
```

```shell
unzip big-zip-files.zip/
```

Here we see a lot of files and directories. So the best command in this case is `grep`.

```shell
grep -ri "picoctf" big-zip-files/
```

```text
picoCTF{gr3p_15_m4g1c_ef8790dc}
```

