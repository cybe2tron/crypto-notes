# General

> Mr.cybe27ron | Sun 18 Oct 2020

## Encoding

* **ASCII**
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

* **Hex**
<p>When we encrypt something the resulting ciphertext commonly has bytes which are not printable ASCII characters. If we want to share our encrypted data, it's common to encode it into something more user-friendly and portable across different systems.<br>

Included below is a the flag encoded as a hex string. Decode this back into bytes to get the flag.<br>

63727970746f7b596f755f77696c6c5f62655f776f726b696e675f776974685f6865785f737472696e67735f615f6c6f747d</p>

*solution*
```python3
bytes.fromhex('63727970746f7b596f755f77696c6c5f62655f776f726b696e675f776974685f6865785f737472696e67735f615f6c6f747d').decode('utf-8')
```

> crypto{You_will_be_working_with_hex_strings_a_lot}

* **Base64**
<p>Take the below hex string, decode it into bytes and then encode it into Base64.

72bca9b68fc16ac7beeb8f849dca1d8a783e8acf9679bf9269f7bf</p>

*Solution*

* **Bytes and bit integer**

Cryptosystems like RSA works on numbers, but messages are made up of characters. How should we convert our messages into numbers so that mathematical operations can be applied?


The most common way is to take the ordinal bytes of the message, convert them into hexadecimal, and concatenate. This can be interpreted as a base-16 number, and also represented in base-10.

Convert the following integer back into a message:

11515195063862318899931685488813747395775516287289682636499965282714637259206269

```python3

// hex with slicing 0x
hex_string = "0x63727970746f7b336e633064316e365f346c6c5f3768335f7734795f6430776e7d"[2:]

// convert to bytes objext
byte_ob = bytes.fromhex(hexString)

//convert into ascii
asciistring = bytes_ob.decode("ASCII")
print(asciistring)
crypto{3nc0d1n6_4ll_7h3_w4y_d0wn}
```

## XOR

* **XOR Starter**


