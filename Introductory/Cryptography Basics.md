<p align="center">
  <img src="https://tryhackme-images.s3.amazonaws.com/room-icons/5f04259cf9bf5b57aed2c476-1725523498749" alt="Room Icon" width="200"/>
</p>

# Cryptography Basics
Created by <a href="https://tryhackme.com/p/tryhackme">tryhackme</a>, <a href="https://tryhackme.com/p/strategos">strategos</a>

## Task 2: Importance of Cryptography
- Cryptography ensures secure communication in presence of adversaries.
- Cryptography is a practice and study of techniques for secure communication and data protection.
- Confidentiality, Integrity, and Availability.
- PCI DSS (Payment Card Industry Data Security Standard) is an example of real-world applications of cryptography.
  - Minimum level of security to store, process, and transmit data related to credit cards.
- HIPAA (Health Insurance Portability and Accountability Act) - Considers handling of medical records.

<br>

#### Q1: What is the standard required for handling credit card information?
<pre>PCI DSS</pre>

<br>

## Task 3: Plaintext to Ciphertext
- Plaintext is readable data; data we want to encrypt.
- Encryption function is part of a cipher (algorithm to convert plaintext to ciphertext).
- Ciphertext is scrambled, unreadable data.
- Key is a string cipher used to encrypt or decrypt data.

<br>

#### Q1: What do you call the encrypted plaintext?
<pre>ciphertext</pre>
<br>

#### Q2: What do you call the process that returns the plaintext?
<pre>decryption</pre>

## Task 4: Historical Ciphers
- One of the simple historical ciphers is the Caesar Cipher.
  - Shifts each letter by a certain number to encrypt message.
  - Today it is considered insecure.
- More examples include Vigenere cipher from 16th century, Engima machine from WW2, and one-time pad from Cold War.
<br>

#### Q1: Knowing that ```XRPCTCRGNEI``` was encrypted using Caesar Cipher, what is the original plaintext?
<pre>ICANENCRYPT</pre>
You can use an online Caesar Cipher decryption tool (i.e., <a href="https://cryptii.com/pipes/caesar-cipher">Cryptii</a>) or do it manually by hand. Eventually you will find out shift 15 was used to encode the text.

<br>

## Task 5: Types of Encryption
- Two types of encryption are **symmetric** and **asymmetric**.
  - Symmetric: Uses same key for encryption and decryption.
    - Examples: DES, 3DES, AES
  - Asymmetric: Uses one key to encrypt, another key for decryption.
    - Examples: RSA, Diffie-Hellman, Elliptic Curve Cryptography (ECC).
    - Tends to be slower than symmetric.
- "Extremely difficult" means practically infeasible (in terms of encryption).

<br>

#### Q1: Should you trust DES? (Yea/Nay)
<pre>Nay</pre>
DES is insecure.
<br>

#### Q2: When was AES adopted as an encryption standard?
<pre>2001</pre>
<br>

## Task 6: Basic Math
- Two mathematical operators are used in various algorithms: XOR and Modulo operation.
- XOR short for "exclusive OR" - compares two bits - returns 1 if different, 0 if they are the same.
- Modulo is the remainder when X is divided by Y.
  - i.e., 25%5 = 0 because 25 divided by 5 is 5 with remainder of 0.

<br>

#### Q1: What's 1001 ⊕ 1010?
<pre>0011</pre>
Compare each bit on the left to the right. If they are different, then the value is 1. Otherwise 0.
<br>

#### Q2: What's 111813842%9091?
<pre>3565</pre>
Use a calculator to get the remainder (modulo).
<br>

#### Q3: What's 60%12?
<pre>0</pre>
Use a calculator to get the remainder (modulo).
<br>

