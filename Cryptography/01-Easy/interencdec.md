# interencdec Writeup

> Can you get the real meaning from this file.
> Download the file [here](https://artifacts.picoctf.net/c_titan/109/enc_flag)

## Solution

```shell
wget "https://artifacts.picoctf.net/c_titan/109/enc_flag"
```

```shell
cat enc_flag
```

```text
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclgyMHdNakV5TnpVNGZRPT0nCg==
```

We see that it's a base64 encoding.

```shell
base64 -d enc_flag
```

```text
b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX20wMjEyNzU4fQ=='
```

We see that it's still base64.

```shell
echo "d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX20wMjEyNzU4fQ==" | base64 -d
```

```text
wpjvJAM{jhlzhy_k3jy9wa3k_m0212758}
```

So here it's like the flag format, but it's still encoded. Here we will try `caesar cypher` because it's in the title.

I used this site here `https://www.dcode.fr/caesar-cipher` because he's testing all the possible shifts.

```text
picoCTF{caesar_d3cr9pt3d_f0212758}
```

