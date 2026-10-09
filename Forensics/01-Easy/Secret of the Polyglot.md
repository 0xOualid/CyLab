# Secret of the Polyglot Writeup

> The Network Operations Center (NOC) of your local institution picked up a suspicious file, they're getting conflicting information on what type of file it is. They've brought you in as an external expert to examine the file. Can you extract all the information from this strange file?
> Download the suspicious file [here](https://artifacts.picoctf.net/c_titan/99/flag2of2-final.pdf).

## Solution

```shell
wget "https://artifacts.picoctf.net/c_titan/99/flag2of2-final.pdf"
```

First we open that PDF normally, and we see that there is the second part of the flag on it as the name of the file says `1n_pn9_&_pdf_2a6a1ea8}`.

Now we have to found the first part.

```shell
file flag2of2-final.pdf
```

```text
flag2of2-final.pdf: PNG image data, 50 x 50, 8-bit/color RGBA, non-interlaced
```

We notice that the file is `PNG image data` which is weird because the file is PDF. 

So i try to change his extension from `.pdf` to `.png`. And that's it when you open the image you found the first part of the flag `picoCTF{f1u3n7_`.

```text
picoCTF{f1u3n7_1n_pn9_&_pdf_2a6a1ea8}
```

