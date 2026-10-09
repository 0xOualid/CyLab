# Python Wrangling Writeup

> Python scripts are invoked kind of like programs in the Terminal...
> Can you run [ende.py](https://challenge-files.picoctf.net/c_wily_courier/2946b2b767f2d6792cb13dcfc9312c0fd5888dcabaf4196f2d88ae6d46f2a62c/ende.py) using [password.txt](https://challenge-files.picoctf.net/c_wily_courier/2946b2b767f2d6792cb13dcfc9312c0fd5888dcabaf4196f2d88ae6d46f2a62c/password.txt) to get [flag.txt.en](https://challenge-files.picoctf.net/c_wily_courier/2946b2b767f2d6792cb13dcfc9312c0fd5888dcabaf4196f2d88ae6d46f2a62c/flag.txt.en)?

## Solution

```shell
wget "https://challenge-files.picoctf.net/c_wily_courier/2946b2b767f2d6792cb13dcfc9312c0fd5888dcabaf4196f2d88ae6d46f2a62c/ende.py"
wget "https://challenge-files.picoctf.net/c_wily_courier/2946b2b767f2d6792cb13dcfc9312c0fd5888dcabaf4196f2d88ae6d46f2a62c/password.txt"
wget "https://challenge-files.picoctf.net/c_wily_courier/2946b2b767f2d6792cb13dcfc9312c0fd5888dcabaf4196f2d88ae6d46f2a62c/flag.txt.en"
```

First to know what to do, ask for `help`.

```shell
python ende.py -h
```

```text
Usage: ende.py (-e/-d) [file]
Examples:
  To decrypt a file named 'pole.txt', do: '$ python ende.py -d pole.txt'
```

Then let's cat the `password.txt`.

```shell
cat password.txt
```

```text
720b6ad346f84cd483c60c7464dd95d4
```

And now decrypt it.

```shell
python ende.py -d flag.txt.en
```

```text
Please enter the password:720b6ad346f84cd483c60c7464dd95d4
```

```text
picoCTF{4p0110_1n_7h3_h0us3_9c5f9bcf}
```

