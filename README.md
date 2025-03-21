# AES-GCM Encryption Example

I learned this algorithm so I could implement it in a Chrome extension that stores sensitive user data in Chrome local storage. Since a Chrome extension’s source code is public via "Inspect Element" and the stored data is accessible through Chrome's storage API, I needed to find an algorithm that would let me secure this data through encryption. This example demonstrates how to encrypt and decrypt data using AES-GCM combined with a PBKDF2-derived key.

## Overview

- **Encryption Method:** Uses AES-GCM for authenticated encryption.
- **Key Derivation:** Utilizes PBKDF2 with a random salt to derive a secure key from a user passphrase.
- **Components:** Generates a random initialization vector (IV) and separates the encrypted output into ciphertext and an authentication tag.

## How It Works

1. **Key Derivation:** A user passphrase is converted into a cryptographic key using PBKDF2 along with a random salt.
2. **Encryption:** The plaintext (e.g., a diary entry) is encrypted using AES-GCM with the derived key and a random IV. The encrypted output is split into ciphertext and an authentication tag.
3. **Decryption:** The ciphertext and authentication tag are recombined and decrypted with the same key to retrieve the original plaintext.

## Usage

1. Open the HTML file in a modern web browser.
2. Open the browser console to see the following:
   - The original user passphrase and plaintext.
   - The generated ciphertext, IV, authentication tag, and salt.
   - The decrypted data, which should match the original plaintext.
