# introduction 

> Mr.cybe27ron | Sat 17 Oct 2020

*** 

### challenge 1.

**Finding Flags** : <p>Each challenge is designed to help introduce you to a new piece of cryptography. Solving a challenge will require you to find a "flag".

These flags will usually be in the format crypto{y0ur_f1rst_fl4g}.</p>

*Solution* : <p>just copy paste the flag.</p>

### Challenge 2.

**Great snakes** : <p>Modern cryptography involves code, and code involves coding. CryptoHack provides a good opportunity to sharpen your skills. Run the attached Python script and it will output your flag.
</p>

*Solutions* : <p>run python script to get flag. ```crypto{z3n_0f_pyth0n}```</p>

### Challenge 3.

**Network Attacks** : <p>For this challenge, connect to socket.cryptohack.org on port 11112. Send a JSON object with the key buy and value flag.</p>

*Solutions* : <p> connect to [socket.cryptohack.org](socket.cryptohack.org:11112) using nc and send json data with key *buy* and value *flag*.</p>

```
nc socket.cryptohack 11112

Welcome to netcat's flag shop!
What would you like to buy?
I only speak JSON, I hope that's ok.

{"buy": "flag"}
{"flag": "crypto{sh0pp1ng_f0r_fl4g5}"}

```
