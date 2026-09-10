# Generate-and-Use-a-Digital-Signature
# Lab - Generate and Use a Digital Signature

## Overview

This lab demonstrates how digital signatures provide **authentication**, **integrity**, and **non-repudiation** using OpenSSL. An RSA key pair was generated, a document was digitally signed with the private key, and the signature was successfully verified using the corresponding public key. After modifying the signed document, signature verification failed, proving that the document's integrity had been compromised.

## Objectives

- Generate an RSA private key.
- Create a corresponding public key.
- Digitally sign a document using SHA-256.
- Verify the authenticity and integrity of the signed document.
- Demonstrate how modifying a signed document invalidates its digital signature.

## Technologies Used

- OpenSSL
- Linux Terminal
- RSA Public-Key Cryptography
- SHA-256 Hashing

## Lab Steps

### 1. Generated RSA Key Pair
- Created an RSA private key (`private_key.pem`)
- Generated the corresponding public key (`public_key.pem`)

### 2. Created a Document
Created a file named `contract.txt` containing a sample financial agreement.

### 3. Digitally Signed the Document
Used the private key and SHA-256 to generate a digital signature:

```bash
openssl dgst -sha256 -sign private_key.pem -out signature contract.txt
```

### 4. Verified the Digital Signature
Verified the document using the public key:

```bash
openssl dgst -sha256 -verify public_key.pem -signature signature contract.txt
```

Output:

```
Verified OK
```

### 5. Modified the Document
Changed the recipient's name in `contract.txt` from **Mr. Jester** to **Mr. Viper**.

### 6. Verified Again
Ran the verification command after modifying the file.

Output:

```
Verification Failure
```

This demonstrates that even a small modification changes the document's hash, causing the digital signature verification to fail.

## Key Concepts Learned

- Public and private key cryptography
- Digital signatures
- SHA-256 hashing
- Data integrity verification
- Authentication
- Non-repudiation
- Tamper detection

## Conclusion

This lab demonstrated how digital signatures protect data from unauthorized modifications. A document signed with a private key can be verified using the corresponding public key, ensuring both the sender's authenticity and the document's integrity. Any alteration to the signed document causes verification to fail, providing a reliable method for detecting tampering.
