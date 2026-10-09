# PW Crack 2 Writeup

> Can you crack the password to get the flag?
> Download the password checker [here](https://artifacts.picoctf.net/c/13/level2.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/13/level2.flag.txt.enc) in the same directory too.

## Solution

```shell
wget "https://artifacts.picoctf.net/c/13/level2.py"
wget "https://artifacts.picoctf.net/c/13/level2.flag.txt.enc"
```

You have first to understand the source code of the file to find the password.

```shell
cat level2.py
```

```python
### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
    
###############################################################################

flag_enc = open('level2.flag.txt.enc', 'rb').read()

def level_2_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36) ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")

level_2_pw_check()
```

The password is in `0x (hex representation)` in python. So we have to recreate the it.

```shell
python3
```

```python
print(chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36))
de76
```

```shell
python3 level2.py
```

```text
de76
```

```text
picoCTF{tr45h_51ng1ng_489dea9a}
```

