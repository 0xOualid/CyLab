# The Numbers Writeup

> [numbers.png](https://challenge-files.picoctf.net/c_fickle_tempest/7b39deba4212c233b1628c93f16639ed02ad90f51436d2a8914bb11f74a982d3/the_numbers.png)

## Solution

```shell
wget "https://challenge-files.picoctf.net/c_fickle_tempest/7b39deba4212c233b1628c93f16639ed02ad90f51436d2a8914bb11f74a982d3/the_numbers.png"
```

We can see it is a normal image, including some numbers on it.

Putting the numbers in `CyberChef` with removing the `{}` give us that it is a `A1Z26 cipher` it is a very simple substitution cipher where each letter of the alphabet is replaced by its corresponding numerical position.

```text
picoctf{thenumbersmason}
```

