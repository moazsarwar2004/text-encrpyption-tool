# Short report: Web-Based Text Encryption Tool

The project is a single-page application built with HTML, CSS, and JavaScript. It accepts text, lets the user choose one of three encryption methods, and displays the ciphertext. The same page can also decrypt messages and copy results. All processing happens in the browser.

## Techniques used

**Caesar Cipher** shifts each English letter by a number from 1 to 25. For example, with a shift of 3, `HELLO` becomes `KHOOR`. Decryption shifts letters back. Spaces, punctuation, and other characters are left as entered. Its small key space makes it unsuitable for protecting private data.

**Vigenère Cipher** uses a keyword to choose a different shift for each English letter. With the keyword `KEY`, each successive letter uses the shifts for K, E, and Y, repeating as necessary. Decryption applies the same keyword in reverse. Spaces and punctuation do not advance the keyword. It is a classical cipher and is also unsuitable for sensitive data.

**AES-GCM** uses the browser's Web Crypto API for authenticated encryption. A password is converted into a 256-bit AES key with PBKDF2 and SHA-256 using 100,000 iterations and a random 16-byte salt. Each encryption also creates a random 12-byte IV. The output stores a version marker, salt, IV, and encrypted data in Base64 so the browser can decrypt it later with the same password. AES-GCM detects changed ciphertext or an incorrect password.

## Validation and use

The page rejects blank input, an unselected method, an invalid Caesar shift, a Vigenère keyword containing nonletters, or a missing AES password. The result is cleared before each operation, so a failed request cannot leave an earlier result on screen. AES runs on `localhost` or HTTPS because browsers restrict the Web Crypto API to secure contexts.
