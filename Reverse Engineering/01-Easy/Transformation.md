# Transformation Writeup

> I wonder what this really is...
> [enc](https://challenge-files.picoctf.net/c_wily_courier/c54640eb53abf2f31d27f53f1547faf619e26b013130e3b506905cdc8f9aea2d/enc) ''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])

## Solution

```shell
wget "https://challenge-files.picoctf.net/c_wily_courier/c54640eb53abf2f31d27f53f1547faf619e26b013130e3b506905cdc8f9aea2d/enc"
```

```shell
cat enc
```

```text
灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸形㝦㘲捡㕽
```

Here we got a weird CJK characters with no sense.

They also provide us with a small Python code snippet, which helps you understand how the flag was encoded.

```python
''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])
```

What the code does:
- It walks through `flag` two characters at a time (`i` and `i+1`).
- `ord(flag[i])` gets the byte value of the first character, shifts it left 8 bits (into the "high byte" position).
- Adds `ord(flag[i+1])` (the second character, as the "low byte").
- `chr(...)` turns that combined 16-bit number back into a single Unicode character.

To reverse it:

```python
enc_flag = "灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸形㝦㘲捡㕽"
flag = ""

for ch in enc_flag:
    cp = ord(ch)  # cp => (code pointer)

    first_ch = cp >> 8
    second_ch = cp & 0xFF

    flag += chr(first_ch) + chr(second_ch)

print(flag)
```

```text
picoCTF{16_bits_inst34d_of_8_b7f62ca5}
```

