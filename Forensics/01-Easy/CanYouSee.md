# CanYouSee Writeup

> How about some hide and seek?
> Download this file [here](https://artifacts.picoctf.net/c_titan/5/unknown.zip).

## Solution

First you have to download the image and see if you find something in the image visually. Using some online tools.

Then try on the terminal. after a while i found something interesting in the metadata using `exiftool`.

```shell
wget "https://artifacts.picoctf.net/c_titan/5/unknown.zip"
```

```shell
unzip unknown.zip
```

```shell
file ukn_reality.jpg
```

```text
ukn_reality.jpg: JPEG image data, JFIF standard 1.01, resolution (DPI), density 72x72, segment length 16, baseline, precision 8, 4308x2875, components 3
```

```shell
exiftool ukn_reality.jpg
```

Here i found a base64 format in the `Attribution URL`.

```shell
echo "cGljb0NURntNRTc0RDQ3QV9ISUREM05fNGRhYmRkY2J9Cg==" | base64 -d
```

```text
picoCTF{ME74D47A_HIDD3N_4dabddcb}
```

