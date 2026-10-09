# Super SSH Writeup

> Using a Secure Shell (SSH) is going to be pretty important.
> Can you ssh as ctf-player to titan.picoctf.net at port 53656 to get the flag?
> You'll also need the password 84b12bae. If asked, accept the fingerprint with yes.

## Solution

```shell
ssh ctf-player@titan.picoctf.net -p 53656
84b12bae
```

```text
picoCTF{s3cur3_c0nn3ct10n_07a987ac}
```

