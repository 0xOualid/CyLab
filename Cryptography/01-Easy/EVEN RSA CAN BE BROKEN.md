# EVEN RSA CAN BE BROKEN Writeup

> This service provides you an encrypted flag. Can you decrypt it with just N & e?
> Connect to the program with netcat: 
> `$ nc verbal-sleep.picoctf.net 64108`
> The program's source code can be downloaded [here](https://challenge-files.picoctf.net/c_verbal_sleep/2b0f68c54cfcb2dafd4ca90c4abcbe73c208f09edf65af336fc7023e1c1314ca/encrypt.py).

## Solution

First let's get and see the program's source code.

```shell
wget "https://challenge-files.picoctf.net/c_verbal_sleep/2b0f68c54cfcb2dafd4ca90c4abcbe73c208f09edf65af336fc7023e1c1314ca/encrypt.py"
```

```shell
cat encrypt.py
```

```python
from sys import exit
from Crypto.Util.number import bytes_to_long, inverse
from setup import get_primes

e = 65537

def gen_key(k):
    """
    Generates RSA key with k bits
    """
    p,q = get_primes(k//2)
    N = p*q
    d = inverse(e, (p-1)*(q-1))

    return ((N,e), d)

def encrypt(pubkey, m):
    N,e = pubkey
    return pow(bytes_to_long(m.encode('utf-8')), e, N)

def main(flag):
    pubkey, _privkey = gen_key(1024)
    encrypted = encrypt(pubkey, flag) 
    return (pubkey[0], encrypted)

if __name__ == "__main__":
    flag = open('flag.txt', 'r').read()
    flag = flag.strip()
    N, cypher  = main(flag)
    print("N:", N)
    print("e:", e)
    print("cyphertext:", cypher)
    exit()
```

The core of this program is to understand how RSA work's.

Now let's try with `nc` to see what's happens.

```shell
nc verbal-sleep.picoctf.net 64108
```

```text
N: 13689430518429143288497405567521960154403992933813751657075019694392835235807039184068386323187484841569326788150850023771710667309807615545527986806058194

e: 65537

cyphertext: 7483533393699131072109662691980909370249526541858436350516781046655660575953506554109018199741643102098462254830554989799920991065397019327571526948953641
```

Here they give us `N, e, cyphertext`. But to decrypt the `cyphertext` and get the `m (message)`
we need `d`.

If we look closely into N, we find that `N` is a `even numbers`, which is unusual because N should always be odd (product of two odd primes). This anomaly hinted that one of the prime factors might be 2, the only even prime number.

```python
from Crypto.Util.number import long_to_bytes

N = 13689430518429143288497405567521960154403992933813751657075019694392835235807039184068386323187484841569326788150850023771710667309807615545527986806058194

e = 65537

cyphertext = 7483533393699131072109662691980909370249526541858436350516781046655660575953506554109018199741643102098462254830554989799920991065397019327571526948953641


# Calcul p and q
p = 2
q = N // p


# Calcul phi_N
# phi_N = (p − 1)(q − 1)
# phi_N = (2 − 1)(q − 1)
phi_N = q - 1


# Calcul the private key d
d = pow(e, -1, phi_N)


# Decrypt the ciphertext
m = pow(cyphertext, d, N)


# convert the message to flag string
flag = long_to_bytes(m)
print(flag)
```

```text
picoCTF{tw0_1$_pr!m31c9046c4}
```

