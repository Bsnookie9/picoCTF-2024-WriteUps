# Overview
- Tags: `picoCTF 2024` `Cryptography` `browser_webshell_solvable`
- `300 points`

# Description
Can you abuse the oracle?  

An attacker was able to intercept communications between a bank and a fintech company.  

They managed to get the [message](https://artifacts.picoctf.net/c_titan/149/secret.enc) (ciphertext) and the [password](https://artifacts.picoctf.net/c_titan/149/password.enc) that was used to encrypt the message.  

After some intensive reconassainance they found out that the bank has an oracle that was used to encrypt the password and can   
be found here `nc titan.picoctf.net 52249`. Decrypt the password and use it to decrypt the message.  

The oracle can decrypt anything except the password.

# Hints
* Crytography Threat models: chosen plaintext attack.
* OpenSSL can be used to decrypt the message. e.g `openssl enc -aes-256-cbc -d ...`
* The key to getting the flag is by sending a custom message to the server by taking advantage of the RSA encryption algorithm.
* Minimum requirements for a useful cryptosystem is CPA security.

# Solution
