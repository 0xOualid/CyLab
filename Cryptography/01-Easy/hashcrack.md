# hashcrack Writeup

> A company stored a secret message on a server which got breached due to the admin using weakly hashed passwords. Can you gain access to the secret stored within the server?
> Access the server using `nc verbal-sleep.picoctf.net 63298`

## Solution

```shell
nc verbal-sleep.picoctf.net 63298
```

```text
Welcome!! Looking For the Secret?

We have identified a hash: 482c811da5d5b4bc6d497ffa98491e38
Enter the password for identified hash:
```

Here they give us a hash, and we have to enter the password for this hash (the password before being hashed).

We have to find the hash type first with a `hash analyzer` then crack it using some tools like `hashcat` using a word list.

But we can easily use `web sites` that use a big databases and tables to crack hashes fast. in my case i'm using `https://crackstation.net/`.

| Hash                             | Type | Result      |
| -------------------------------- | ---- | ----------- |
| 482c811da5d5b4bc6d497ffa98491e38 | md5  | password123 |

```text
Flag is yet to be revealed!! Crack this hash: b7a875fc1ea228b9061041b7cec4bd3c52ab3ce3
Enter the password for the identified hash:
```

| Hash                                     | Type | Result  |
| ---------------------------------------- | ---- | ------- |
| b7a875fc1ea228b9061041b7cec4bd3c52ab3ce3 | sha1 | letmein |

```text
Almost there!! Crack this hash: 916e8c4f79b25028c9e467f1eb8eee6d6bbdff965f9928310ad30a8d88697745
Enter the password for the identified hash:
```

| Hash                                                             | Type   | Result    |
| ---------------------------------------------------------------- | ------ | --------- |
| 916e8c4f79b25028c9e467f1eb8eee6d6bbdff965f9928310ad30a8d88697745 | sha256 | qwerty098 |

```text
Correct! You've cracked the SHA-256 hash with a secret found. 
The flag is: picoCTF{UseStr0nG_h@shEs_&PaSswDs!_4c95d69f}
```

