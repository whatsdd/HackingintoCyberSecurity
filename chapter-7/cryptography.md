# Cryptography

## The Oldest Arms Race in History

Julius Caesar shifted every letter in his messages three positions forward in the alphabet. A became D. B became E. Enemies who intercepted the message saw gibberish. Those who knew the shift could read it instantly.

The Caesar cipher is trivially broken today. A modern computer cracks it in microseconds by trying all 25 possible shifts. But Caesar's approach captured something fundamental: hide a message by transforming it according to a rule that only authorized parties know. That principle -- transformation by shared secret -- runs unbroken from Caesar's military dispatches to the TLS encryption protecting your banking session right now.[1]

What changed is the mathematics. Simple substitution ciphers can be broken by analyzing letter frequency patterns. Modern cryptography uses mathematical problems that are computationally infeasible to reverse without the key -- problems involving large prime factorization, discrete logarithms, and elliptic curves that even the fastest computers cannot brute-force in any meaningful timeframe.

Cryptography is the foundation of digital security. Without it, there is no private communication, no authentication, no trusted e-commerce, no secure remote access. Every other security control either uses cryptography or depends on infrastructure that does.

---

## Core Concepts

Before diving into specific algorithms, these terms appear in every cryptographic discussion and must be precise.

| Term | Definition |
|---|---|
| **Plaintext** | The original, readable data before encryption |
| **Ciphertext** | The encrypted, unreadable output |
| **Encryption** | The process of converting plaintext to ciphertext using an algorithm and key |
| **Decryption** | The reverse: converting ciphertext back to plaintext using the correct key |
| **Key** | The secret value that controls the encryption and decryption process |
| **Algorithm (cipher)** | The mathematical function used for encryption/decryption |
| **Key space** | The total number of possible keys; larger key spaces mean harder brute-force attacks |

**Kerckhoffs's principle**, formulated by Auguste Kerckhoffs in 1883, states that a cryptographic system should be secure even if everything about it -- except the key -- is public knowledge.[2] This is why the AES algorithm is published in full. Security comes from the secrecy of the key, not the secrecy of the algorithm. Systems that depend on algorithm secrecy ("security through obscurity") have a poor track record.

---

## Symmetric Encryption

Symmetric encryption uses the same key for both encryption and decryption. Both parties must possess the key before secure communication can begin.

### AES (Advanced Encryption Standard)

AES is the dominant symmetric encryption algorithm in use today. NIST selected it in 2001 after a five-year international competition, replacing the older DES (Data Encryption Standard) which had become vulnerable to brute-force attacks with its 56-bit key.[3]

AES operates on 128-bit blocks of data and supports three key sizes:

| Key Size | Rounds | Status |
|---|---|---|
| AES-128 | 10 | Secure for most purposes |
| AES-192 | 12 | Secure |
| AES-256 | 14 | Recommended for top-secret and post-quantum resilience |

AES-256 encrypting a 128-bit block requires an attacker to try 2^256 possible keys to brute-force it. At a trillion attempts per second, that would take longer than the age of the universe. It is not practically breakable by brute force with any technology that exists today.

### Modes of Operation

AES is a block cipher -- it encrypts fixed-size blocks. The mode of operation determines how it handles data longer than one block, and the choice of mode has major security implications.

| Mode | How It Works | Use Case | Notes |
|---|---|---|---|
| **ECB** (Electronic Codebook) | Each block encrypted independently | Almost never appropriate | Identical plaintext blocks produce identical ciphertext -- patterns leak |
| **CBC** (Cipher Block Chaining) | Each block XORed with previous ciphertext before encryption | File encryption, legacy TLS | Requires random IV; vulnerable to padding oracle attacks if misimplemented |
| **GCM** (Galois/Counter Mode) | Counter-based stream cipher + authentication tag | TLS 1.3, disk encryption | Provides both confidentiality and integrity; the modern standard |

{% hint style="danger" %}
**Never use ECB mode.** ECB encrypts identical plaintext blocks to identical ciphertext blocks. The famous "ECB penguin" -- a bitmap image of a penguin encrypted with ECB mode that still shows the clear outline of the penguin in the ciphertext -- makes this concrete. If you can see the pattern, the encryption has failed. ECB mode is present in many libraries for backward compatibility; that does not mean it should be used.
{% endhint %}

### The Key Distribution Problem

Symmetric encryption has one fundamental weakness: both parties need the same key before secure communication can happen. How do you securely share that key in the first place? If you could already communicate securely, you would not need encryption. This is the key distribution problem, and it is why symmetric encryption alone cannot secure the internet.

The solution is asymmetric encryption.

---

## Asymmetric Encryption

Asymmetric encryption (also called public-key cryptography) uses mathematically linked key pairs: a **public key** that anyone can possess and use to encrypt data, and a **private key** that only the owner holds and uses to decrypt it.

The magic: what the public key encrypts, only the private key can decrypt. And critically, knowing the public key does not let you derive the private key -- that derivation would require solving a computationally infeasible mathematical problem.

This solves the key distribution problem. To receive encrypted messages, you publish your public key to the world. Anyone can encrypt a message for you. Only you can decrypt it.

### RSA (Rivest-Shamir-Adleman)

RSA, published in 1977, was the first practical public-key cryptosystem.[4] Its security rests on the difficulty of factoring the product of two large prime numbers. Given the number N = p × q (where p and q are large primes), finding p and q from N alone is computationally infeasible for sufficiently large numbers.

RSA key sizes:

| Key Size | Status |
|---|---|
| 512-bit | Broken -- factorable in hours on modern hardware |
| 1024-bit | Deprecated -- not recommended; factoring feasible with significant resources |
| 2048-bit | Minimum acceptable today; recommended through ~2030 |
| 4096-bit | Strong; preferred for long-term security |

### Elliptic Curve Cryptography (ECC)

ECC provides equivalent security to RSA with much smaller key sizes, based on the difficulty of the elliptic curve discrete logarithm problem.[5]

| Security Level | RSA Key Size | ECC Key Size |
|---|---|---|
| 80-bit | 1024-bit | 160-bit |
| 128-bit | 3072-bit | 256-bit |
| 256-bit | 15360-bit | 512-bit |

A 256-bit ECC key provides the same security as a 3072-bit RSA key. Smaller keys mean faster operations and less bandwidth -- which is why ECC dominates in TLS, mobile devices, and embedded systems.

**ECDSA** (Elliptic Curve Digital Signature Algorithm) and **ECDH** (Elliptic Curve Diffie-Hellman) are the primary ECC algorithms in use. The curves P-256, P-384, and Curve25519 are the most widely deployed.

### Diffie-Hellman Key Exchange

Diffie-Hellman (DH), published in 1976, solved the key distribution problem before RSA even existed.[6] It allows two parties to establish a shared secret over an insecure channel, without ever transmitting the secret itself -- using modular arithmetic that an eavesdropper cannot reverse.

In TLS, Diffie-Hellman (specifically ECDHE -- Elliptic Curve Diffie-Hellman Ephemeral) is used to establish the session key. The "ephemeral" part is critical: a new key pair is generated for every session, so recording encrypted traffic today does not help an attacker who later compromises the server's private key. This property is called **forward secrecy** (or perfect forward secrecy).

---

## Cryptographic Hashing

A cryptographic hash function takes an input of any size and produces a fixed-size output (the hash or digest) with three critical properties:

1. **Deterministic**: The same input always produces the same hash
2. **One-way**: Given the hash, it is computationally infeasible to reconstruct the input
3. **Collision-resistant**: It is computationally infeasible to find two different inputs that produce the same hash

Hashes are not encryption -- there is no key, and there is no intended reversal. They are used to verify integrity.

| Algorithm | Output Size | Status |
|---|---|---|
| **MD5** | 128-bit | Broken -- collisions can be generated; do not use for security |
| **SHA-1** | 160-bit | Deprecated -- collision demonstrated in 2017 (SHAttered attack); do not use |
| **SHA-256** | 256-bit | Secure; current standard for most uses |
| **SHA-3** | Variable | Secure; different construction from SHA-2, providing algorithm diversity |
| **bcrypt / Argon2** | Variable | Specifically designed for password hashing; intentionally slow |

{% hint style="warning" %}
**Password hashing is not the same as data hashing.** SHA-256 is fast -- a modern GPU can compute billions of SHA-256 hashes per second. For password storage, fast is bad: it means an attacker can test billions of password guesses per second against stolen hashes.

Password hashing functions (bcrypt, scrypt, Argon2) are intentionally slow and memory-intensive. Argon2 won the Password Hashing Competition in 2015 and is the current recommendation. If you are storing user passwords, use Argon2id. Never store passwords as plaintext, never use MD5 or SHA-1, and never use fast hash functions like SHA-256 directly.
{% endhint %}

### Hash-Based Integrity Verification

```bash
# Generate SHA-256 hash of a downloaded file
sha256sum kali-linux-2024.1-installer-amd64.iso

# Output:
# 3d9cdb...  kali-linux-2024.1-installer-amd64.iso

# Compare to the hash published by Kali
# If they match, the file is unmodified
```

This is how software publishers verify that distributed files have not been tampered with. An attacker who modifies the binary cannot reproduce the original hash -- so a mismatch alerts the user.

---

## Digital Signatures

Digital signatures combine asymmetric cryptography with hashing to provide three guarantees: **authentication** (the message came from the claimed sender), **integrity** (the message was not modified), and **non-repudiation** (the sender cannot deny sending it).

How it works:

1. The sender computes a hash of the message
2. The sender encrypts that hash with their **private key** -- this is the signature
3. The sender transmits the message and the signature
4. The recipient decrypts the signature with the sender's **public key**, recovering the hash
5. The recipient computes the hash of the received message independently
6. If the two hashes match, the signature is valid -- the message is authentic and unmodified

```
Sender:  Message → Hash → Encrypt(hash, private_key) → Signature
Recipient: Message → Hash
           Signature → Decrypt(signature, public_key) → Hash
           Compare: if hashes match → authentic and unmodified
```

Digital signatures underpin code signing, email signing (S/MIME, PGP), document signing, and certificate authorities.

---

## Public Key Infrastructure (PKI)

Asymmetric encryption solves key distribution but creates a new problem: how do you know that a public key actually belongs to who you think it does? An attacker could publish their own public key while claiming to be your bank.

PKI solves this through **digital certificates** -- documents that bind a public key to an identity, signed by a trusted third party called a **Certificate Authority (CA)**.

When you connect to `https://yourbank.com`:

1. The server presents a certificate containing its public key
2. The certificate is signed by a CA (e.g., DigiCert, Let's Encrypt)
3. Your browser has a pre-installed list of trusted root CAs
4. Your browser verifies the certificate signature chain back to a trusted root
5. If valid, the browser trusts that the public key belongs to `yourbank.com`

The trust model relies on root CAs being trustworthy. When they fail -- as happened with the DigiNotar CA breach in 2011, where attackers issued fraudulent certificates for Google and dozens of other domains -- the entire PKI model for affected certificates collapses.[7]

Let's Encrypt, launched in 2016, provides free, automated, domain-validated certificates and has dramatically increased HTTPS adoption across the web. As of 2024, over 80% of web traffic is encrypted.[8]

---

## TLS: Cryptography in Practice

TLS (Transport Layer Security) is the protocol that secures the majority of internet communication. Every HTTPS connection uses it. Understanding TLS is the most practical application of everything in this chapter.

**TLS 1.3** (RFC 8446, 2018) is the current standard. It eliminated support for weak cipher suites, mandatory forward secrecy for all sessions, and reduced handshake latency.[9]

A TLS 1.3 handshake:

```
Client → Server: ClientHello (supported ciphers, key share)
Server → Client: ServerHello (chosen cipher, key share, certificate)
Client → Server: Finished (session keys derived; encrypted from here)
Server → Client: Finished (handshake complete)
```

The session keys are derived using ECDHE, ensuring forward secrecy. After the handshake, all data is encrypted with AES-GCM. The certificate is verified against the CA chain. The entire handshake completes in one round trip.

TLS 1.0 and 1.1 are deprecated. TLS 1.2 is still widely used but should be configured to use only strong cipher suites. Any server still supporting SSLv3 or early TLS versions has a misconfiguration.

---

## Cryptographic Attacks

Understanding how cryptographic systems fail is as important as understanding how they work.

| Attack | Description | Defense |
|---|---|---|
| **Brute force** | Try every possible key | Use sufficiently large key sizes (AES-128+ for symmetric, 2048+ RSA) |
| **Birthday attack** | Exploit collision probability in hash functions | Use hash functions with large output sizes (SHA-256+) |
| **Padding oracle** | Exploit error messages to decrypt ciphertext byte by byte | Use authenticated encryption (AES-GCM); never leak padding errors |
| **Downgrade attack** | Force negotiation of weaker cipher suites | Disable all deprecated protocol versions and cipher suites |
| **Side-channel attack** | Extract key material from timing, power consumption, or EM emissions | Hardware mitigations; constant-time implementation |
| **Harvest now, decrypt later** | Record encrypted traffic to decrypt after quantum computers arrive | Migrate to post-quantum algorithms now for long-lived secrets |

### The Quantum Threat

Quantum computers, using Shor's algorithm, can theoretically break RSA and ECC by solving the underlying mathematical problems (integer factorization and discrete logarithms) in polynomial time. A sufficiently powerful quantum computer would render current public-key cryptography obsolete.

That computer does not exist today. But the "harvest now, decrypt later" threat is real: nation-state actors are likely recording encrypted traffic now, intending to decrypt it once quantum computing matures. For data that must remain confidential for 10+ years, the quantum threat is already relevant.

NIST completed its post-quantum cryptography standardization process in 2024, selecting:[10]

| Algorithm | Purpose | Based On |
|---|---|---|
| **CRYSTALS-Kyber (ML-KEM)** | Key encapsulation (replaces ECDH) | Module lattice problems |
| **CRYSTALS-Dilithium (ML-DSA)** | Digital signatures | Module lattice problems |
| **SPHINCS+ (SLH-DSA)** | Digital signatures (hash-based alternative) | Hash functions |

TLS 1.3 and major cloud providers are already beginning hybrid deployments -- running classical and post-quantum algorithms simultaneously during the transition period.

---

## Applied Cryptography: What Practitioners Need to Know

Cryptography is complex enough that implementing it from scratch is almost always the wrong answer. The correct approach is using well-vetted libraries and following current best-practice configurations.

{% hint style="success" %}
**Use these; don't reinvent them:**
- **Symmetric encryption**: AES-256-GCM (provides confidentiality + integrity in one operation)
- **Asymmetric encryption**: RSA-2048+ or ECC with P-256/Curve25519
- **Key exchange**: ECDHE (with forward secrecy)
- **Hashing**: SHA-256 or SHA-3 for integrity; Argon2id for passwords
- **TLS**: TLS 1.3; disable TLS 1.0, 1.1, and all SSLv3
- **Libraries**: libsodium (C), PyNaCl (Python), Go's crypto/tls, AWS/GCP/Azure KMS for key management
{% endhint %}

{% hint style="danger" %}
**Never do these:**
- Roll your own cryptographic algorithm ("I'll use a custom cipher")
- Use MD5 or SHA-1 for security-sensitive applications
- Use ECB mode for anything
- Hardcode encryption keys in source code
- Reuse nonces (initialization vectors) with stream ciphers or GCM mode -- this is catastrophic
- Trust "military-grade encryption" as a marketing claim without verifying the actual algorithm
{% endhint %}

---

## References

[1] Kahn, D. (1996). *The Codebreakers: The Comprehensive History of Secret Communication from Ancient Times to the Internet* (revised ed.). Scribner. ISBN 978-0-684-83130-5.

[2] Kerckhoffs, A. (1883). La cryptographie militaire. *Journal des sciences militaires*, 9, 5--38.

[3] National Institute of Standards and Technology. (2001). *Advanced Encryption Standard (AES)*. FIPS Publication 197. doi:10.6028/NIST.FIPS.197

[4] Rivest, R. L., Shamir, A., & Adleman, L. (1978). A method for obtaining digital signatures and public-key cryptosystems. *Communications of the ACM*, 21(2), 120--126. doi:10.1145/359340.359342

[5] Miller, V. S. (1985). Use of elliptic curves in cryptography. In *Advances in Cryptology -- CRYPTO 1985*. Lecture Notes in Computer Science, vol 218. Springer. doi:10.1007/3-540-39799-X_31

[6] Diffie, W., & Hellman, M. E. (1976). New directions in cryptography. *IEEE Transactions on Information Theory*, 22(6), 644--654. doi:10.1109/TIT.1976.1055638

[7] Langley, A. (2011). *Distrust of the Netherlands DigiNotar CA*. Google Security Blog. Retrieved from https://security.googleblog.com/2011/09/update-on-diginotar.html

[8] Let's Encrypt. (2024). *Let's Encrypt Stats*. Internet Security Research Group. Retrieved from https://letsencrypt.org/stats/

[9] Rescorla, E. (2018). *The Transport Layer Security (TLS) Protocol Version 1.3*. RFC 8446. Internet Engineering Task Force. doi:10.17487/RFC8446

[10] National Institute of Standards and Technology. (2024). *Post-Quantum Cryptography Standardization*. NIST. Retrieved from https://csrc.nist.gov/projects/post-quantum-cryptography

---

## Further Reading

| Resource | What It Covers |
|---|---|
| [Cryptopals Challenges](https://cryptopals.com) | Hands-on cryptography challenges that teach attack techniques by breaking real systems. The best practical crypto education available. |
| [A Graduate Course in Applied Cryptography](https://toc.cryptobook.us) | Free textbook by Dan Boneh and Victor Shoup; rigorous but accessible. |
| Schneier, B. (1996). *Applied Cryptography* (2nd ed.). Wiley. | The classic reference; some algorithms are dated but the conceptual foundation is excellent. |
| [NIST Post-Quantum Cryptography](https://csrc.nist.gov/projects/post-quantum-cryptography) | Official NIST resource tracking the PQC standardization process and new algorithm standards. |
| [TLS 1.3 RFC 8446](https://www.rfc-editor.org/rfc/rfc8446) | The TLS 1.3 specification; dense but authoritative. |

---

*Questions about cryptography, TLS configuration, or post-quantum migration? Join the community on [Discord](https://discord.gg/vkXWVFdFe) or reach out on [LinkedIn](https://www.linkedin.com/in/ahmadscience/). If this chapter helped, contribute back -- this book is open source and your additions are welcome.*
