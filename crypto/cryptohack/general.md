# General

> Mr.cybe27ron | Sun 18 Oct 2020

## Encoding

**ASCII**
<p>ASCII is a 7-bit encoding standard which allows the representation of text using the integers 0-127.<br>

Using the below integer array, convert the numbers to their corresponding ASCII characters to obtain a flag.</p>

*solution* 
used python chr() to conver ascii to text.
```python3
#!/usr/bin/python3

list=[99, 114, 121, 112, 116, 111, 123, 65, 83, 67, 73, 73, 95, 112, 114, 49, 110, 116, 52, 98, 108, 51, 125]
flag = ""
for l in list:
    print(chr(l), end="")
```
> crypto{ASCII_pr1nt4bl3}

**Hex**
<p>When we encrypt something the resulting ciphertext commonly has bytes which are not printable ASCII characters. If we want to share our encrypted data, it's common to encode it into something more user-friendly and portable across different systems.<br>

Included below is a the flag encoded as a hex string. Decode this back into bytes to get the flag.<br>

63727970746f7b596f755f77696c6c5f62655f776f726b696e675f776974685f6865785f737472696e67735f615f6c6f747d</p>

*solution*
```python3
bytes.fromhex('63727970746f7b596f755f77696c6c5f62655f776f726b696e675f776974685f6865785f737472696e67735f615f6c6f747d').decode('utf-8')
```

> crypto{You_will_be_working_with_hex_strings_a_lot}

**Base64**
<p>Take the below hex string, decode it into bytes and then encode it into Base64.

72bca9b68fc16ac7beeb8f849dca1d8a783e8acf9679bf9269f7bf</p>

*Solution*
