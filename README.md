# PQP: Quantum-Resistant Encryption Tool

PQP is a work-in-progress encryption tool designed to provide robust security using post-quantum cryptographic algorithms. It serves as a potential future-proof alternative to traditional cryptographic systems like OpenPGP. By utilizing the NIST finalist algorithms `Kyber` for key encapsulation and `Dilithium` for digital signatures, PQP aims to protect data against potential quantum computing threats.

## Features
- **🔑 Key Generation:** Create quantum-resistant key pairs using `Dilithium` (signing) and `Kyber` (encryption).
- **🔐 Key Management:** Securely save and load keys with AES-GCM encryption, protected by a passphrase.
- **🛡️ Quantum-Resistant Encryption:** Use hybrid encryption with `Kyber512` KEM and AES-256-GCM for robust data protection.
- **🔓 Decryption:** Recover encrypted messages using the encapsulated shared secret.
- **✍️ Digital Signatures:** Sign messages with `Dilithium3` and verify signatures using public keys for message integrity.
- **🗝️ Secure Key Storage:** Encrypt private keys using a passphrase-derived key (via Argon2) for added security.

## How It Works
1. **Key Generation:**  
   - Uses the `Dilithium3` algorithm for creating digital signature key pairs.
   - Employs `Kyber512` for generating key encapsulation key pairs.
   
2. **Encryption:**  
   - Utilizes `Kyber512` to encapsulate a symmetric AES-256 key.
   - Encrypts the message with AES-256-GCM using the derived key.
   - Ensures integrity with HMAC and random nonces.

3. **Signing & Verification:**  
   - Signs messages with the `Dilithium3` private key.
   - Verifies signatures using the corresponding public key, ensuring authenticity.

4. **Key Storage:**  
   - Saves keys encrypted with AES-GCM, using a passphrase-derived key generated by Argon2.
   - Supports loading and decrypting keys with the correct passphrase for subsequent operations.