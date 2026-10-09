# Mod 26 Writeup

> Cryptography can be easy, do you know what ROT13 is?
> [values.txt](https://challenge-files.picoctf.net/c_wily_courier/d4899156ecebad9890f21e626e1b2f06459a8973cc4ac7310e85bb5f155216d0/values.txt)

## Solution

```shell
wget "https://challenge-files.picoctf.net/c_wily_courier/d4899156ecebad9890f21e626e1b2f06459a8973cc4ac7310e85bb5f155216d0/values.txt"
```

```shell
cat values.txt
```

```text
cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_45559noq}
```

After trying... It's `rot13` you can use `CyberChef`. Or also you can use terminal to decode it.

```shell
cat values.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

```text
picoCTF{next_time_I'll_try_2_rounds_of_rot13_45559abd}
```

