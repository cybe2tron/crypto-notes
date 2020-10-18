# Encryption - Crypto 101

* * * 

> ./Mr.cybe27ron  |  Friday 16 Oct 2020


### Key-term 

**Ciphertext** - The result of encrypting a plaintext, encrypted data

**Cipher** - A method of encrypting or decrypting data. Modern ciphers are cryptographic, but there are many non cryptographic ciphers like Caesar.

**Plaintext** - Data before encryption, often text but not always. Could be a photograph or other file

**Encryption** - Transforming data into ciphertext, using a cipher.

**Encoding** - NOT a form of encryption, just a form of data representation like base64. Immediately reversible.

**Key** - Some information that is needed to correctly decrypt the ciphertext and obtain the plaintext.

**Passphrase** - Separate to the key, a passphrase is similar to a password and used to protect a key.

**Asymmetric encryption** - Uses different keys to encrypt and decrypt.

**Symmetric encryption** - Uses the same key to encrypt and decrypt

**Brute force** - Attacking cryptography by trying every different password or every different key

**Cryptanalysis** - Attacking cryptography by finding a weakness in the underlying maths

**Alice and Bob** - Used to represent 2 people who generally want to communicate. They’re named Alice and Bob because this gives them the initials A and B. https://en.wikipedia.org/wiki/Alice_and_Bob for more information, as these extend through the alphabet to represent many different people involved in communication.

* * * 

### type of Encryption

* * *

> *Symmetric encryption* uses the same key to encrypt and decrypt the data.

> *Asymmetric encryption* uses a pair of keys, one to encrypt and the other in the pair to decrypt.


### RSA


* * *

### How Does HTTPS Acutually Works

* * * 

### SSH Authentication 

 <p> SSH is authenticated using usernames and passwords. sometimes ssh also configure to use key authentication. by default ssh use <u>RSA key</u> . You can add  passphrase to encrypt the SSH key. ssh-keygen is the program used to generate pairs of keys . </p>

##### ssh private key 
 <p>  private keys are like password . we dont share them with anyone. while conneting the remote machine we copy public key over remote machine.</p>

 <p> The <code>authorized_keys</code> file in <code>.ssh</code> directory holds public keys that are allowed to access the server if key authentication is enabled</p>


* * * 