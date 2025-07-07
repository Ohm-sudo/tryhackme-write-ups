<p align="center">
  <img src="https://tryhackme-images.s3.amazonaws.com/room-icons/61a7523c029d1c004fac97b3-1720691829028" alt="Room Icon" width="200"/>
</p>

# Introduction to CryptOps
Created by <a href="https://tryhackme.com/p/tryhackme">tryhackme</a>, <a href="https://tryhackme.com/p/melmols">melmols</a>

## Task 2: Key Management in DevSecOps
- Cryptographic keys are crucial for encrypting sensitive data.
- DevSecOps - integrate security practices early in development cycle.
- PCI DSS, GDPR, and HIPAA outline guidelines for strict data protection.
### Key Management Lifecycle (KML)
<img src="https://tryhackme-images.s3.amazonaws.com/user-uploads/61a7523c029d1c004fac97b3/room-content/d2f2cd7385ad25ba6c0d391d48bc7bf2.svg"/>

1. Key Generation - Keys created with secure and compliant methods.
2. Key Distribution - Keys distributed to intended users or systems securely.
3. Key Storage - Encrypted databases, hardware security modules (HSMs).
4. Key Usage - Monitor and control how keys are used.
5. Key Backup and Recovery - Old keys may be archived for decrypting old data.
6. Key Revocation - Invalidating a key before expiration.
7. Key Destruction

<br>

#### Q1: Which key process might involve using HSMs?
<pre>key storage</pre>
<br>

#### Q2: What can you set so that a key is recoverable after x days?
<pre>purge period</pre>
<br>

#### Q3: What process invalidates a key before its expiry date?
<pre>Key Revocation</pre>
<br>

## Best Practices in Key Generation
1. Use strong RNGs - Check FIPS-140-X for algorithms and best practices.
2. Adhere to industry standards and algorithms (i.e., NIST).
3. Secure key generation environment.
4. Validate key generation parameters.
