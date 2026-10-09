# PW Crack 5 Writeup

> Can you crack the password to get the flag?
> Download the password checker [here](https://artifacts.picoctf.net/c/31/level5.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/31/level5.flag.txt.enc) and the [hash](https://artifacts.picoctf.net/c/31/level5.hash.bin) in the same directory too. Here's a [dictionary](https://artifacts.picoctf.net/c/31/dictionary.txt) with all possible passwords based on the password conventions we've seen so far.

## Solution

```shell
wget "https://artifacts.picoctf.net/c/31/level5.py"
wget "https://artifacts.picoctf.net/c/31/level5.flag.txt.enc"
wget "https://artifacts.picoctf.net/c/31/level5.hash.bin"
wget "https://artifacts.picoctf.net/c/31/dictionary.txt"
```

```shell
cat level5.py
```

```python
import hashlib

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

flag_enc = open('level5.flag.txt.enc', 'rb').read()
correct_pw_hash = open('level5.hash.bin', 'rb').read()

def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()

def level_5_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    user_pw_hash = hash_pw(user_pw)
    
    if( user_pw_hash == correct_pw_hash ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")

level_5_pw_check()
```

Here they give you a file of passwords, so first you need to know how to loop through a file in Python and then write a code.

So here I add new lines of code. That makes you try all the passwords in the list then print the correct password before you enter it.

```shell
nano level5.py
```

```python
import hashlib

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

flag_enc = open('level5.flag.txt.enc', 'rb').read()
correct_pw_hash = open('level5.hash.bin', 'rb').read()

def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()

# This is the part of the code I added
# ==============================================
with open("dictionary.txt", "r") as file:
    for pw in file:
        my_hash = hash_pw(pw.strip())
        if my_hash == correct_pw_hash:
            print(pw.strip())
# ==============================================

def level_5_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    user_pw_hash = hash_pw(user_pw)
    
    if( user_pw_hash == correct_pw_hash ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")

level_5_pw_check()
```

```shell
python3 level5.py
```

```text
9581
Please enter correct password for flag:
```

```text
9581
```

```text
picoCTF{fl45h_5pr1ng1ng_cf341ff1}
```

