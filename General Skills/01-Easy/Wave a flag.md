# Wave a flag Writeup

> Can you invoke help flags for a tool or binary? This program has extraordinarily helpful information...
> [warm](https://challenge-files.picoctf.net/c_wily_courier/5a478d0b24d6a4f4185e3adb7a78c41cdad626fb02fe80e083dc33bf8b197d3d/warm)

## Solution

```shell
wget "https://challenge-files.picoctf.net/c_wily_courier/5a478d0b24d6a4f4185e3adb7a78c41cdad626fb02fe80e083dc33bf8b197d3d/warm"
```

```shell
strings warm | grep "flag"
```

```text
picoCTF{b1scu1ts_4nd_gr4vy_ac5832c}
```

