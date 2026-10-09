# Tab, Tab, Attack Writeup

> Using tabcomplete in the Terminal will add years to your life, esp. when dealing with long rambling directory structures and filenames.
> [Addadshashanammu.zip](https://challenge-files.picoctf.net/c_wily_courier/730d9106a6ce1d52c6463b90937ec89f5eb661388954fbd15cfa0c8a2eec012f/Addadshashanammu.zip)

## Solution

```shell
wget "https://challenge-files.picoctf.net/c_wily_courier/730d9106a6ce1d52c6463b90937ec89f5eb661388954fbd15cfa0c8a2eec012f/Addadshashanammu.zip"
```

```shell
unzip Addadshashanammu.zip
```

```shell
tree Addadshashanammu
```

You have to use `tap` to autocomplete for sure.

```shell
cd Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku/
```

```shell
cat fang-of-haynekhtnamet.c
```

```text
picoCTF{l3v3l_up!_t4k3_4_r35t!_fc588427}
```

