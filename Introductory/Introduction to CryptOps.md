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

## Task 3: Best Practices in Key Generation
1. Use strong RNGs - Check FIPS-140-X for algorithms and best practices.
2. Adhere to industry standards and algorithms (i.e., NIST).
3. Secure key generation environment.
4. Validate key generation parameters.
- Bastion hosts (aka jump servers) are cloud instances that act as an access point between external and internal network resources.
  - Ideal for secure key generation.

<br>

#### Q1: What does RNGs stand for?
<pre>Random number generators</pre>
<br>

#### Q2: In the context of key generation, what do you call securely configured cloud hosts or jump servers?
<pre>bastion hosts</pre>
<br>

## Task 4: Key Distribution
### Best Practices
1. Secure transmission channels (i.e., TLS).
2. Employ PKI (public, private keys).
3. Use trusted delivery methods (i.e., using a secure email exchange).
4. Implement robust authentication mechanisms.
5. Provide secure key storage solutions.
- Kerberos is an example of a KDC (key distribution center) system for key exchange.
- Pre-Shared Key (PSK) often used in VPNs or wireless networks.

<br>

#### Q1: What does PKI stand for?
<pre>Public Key Infrastructure</pre>
<br>

#### Q2: What's an example protocol for KDC?
<pre>Kerberos</pre>
<br>

#### Q3: What types of keys are used in VPNs? (Use the acronym)
<pre>PSK</pre>
<br>

## Task 5: Secure Storage and Usage
### Secure Storage Options
- **Hardware Security Module** (HSM): Physical device that generates, stores, and manages cryptographic keys securely.
- **Cloud-Based Key Management Services**: AWS Key Management Service (KMS), Azure Key Vault, Google Cloud Key Management Service.
  - Cloud offers scalability, high availability, and built-in compliance.
- **Encrypted Databases and Keystores**

<br>

### Access Control Mechanisms
- **Role-Based Access Control (RBAC)**: Segregate responsibilities with roles for users.
- **Attribute-Based Access Control (ABAC)**: Permissions granted based on user attributes.
  - Allows for dynamic access control policies.
### Authentication
- Multi-factor authentication greatly reduces risk of unauthorized access.
### Accountability
- Auditing and monitoring allows for detection of unauthorized access attempts and ensure compliance.

<br>

#### Q1: What access control strategy relies on user attributes, resources, and the current environment? 
<pre>ABAC</pre>
<br>

#### Q2: What storage solution offers tamper-resistant hardware? 
<pre>HSM</pre>
<br>

## Task 6: Key Rotation and Revocation Strategies
- Key rotation involves removal of old keys with new ones - minimizes window of opportunity for attackers.
### Implementing Rotation Policies
- **Define a cryptoperiod**: Establish a span of time after which a key should be rotated.
- **Automate rotation processes**: Ensures key rotation happens consistently, reducing human error.
- **Use versioning and backward compatiibility**: Maintain access to historical data, and avoid disruption of services.
### Revocation Mechanisms
- **Certificate Revocation Lists (CRLs) and Online Certificate Status Protocol (OCSP)**: Checks revocation status of certificates; verify if key is still valid.
- **Key Status Checks**: Check status of keys before use.
### Communicating Revocation
- Notify stakeholders.
- Update access controls.

<br>

#### Q1: What are CRLs?
<pre>certificate revocation lists</pre>
<br>

#### Q2: What term refers to a key's lifespan before rotation?
<pre>cryptoperiod</pre>
<br>

## Task 7: Vault Config
- ```Sealed -> True``` means the vault is sealed.
  - Vault can be unsealed using keys (# of keys is based on the configured **Threshold** line).
-  You will instructed to configure a policy such that only you and your desginated crypto engineers can create the secrets.

<br>

#### Q1: What command checks the overall vault information?
<pre>vault status</pre>
<br>

#### Q2: What is the token_accessor value after logging in with the root token?
<pre>uSIMacGCxh8Hj14YHTYg6j0o</pre>
<br>

#### Q3: What's the default Time To Live (TTL) for a token in Vault? (in hours)
<pre>768</pre>
After creating the token, look at the ```token_duration``` field. 768 is the default value.
