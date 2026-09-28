# Text Encryption Tool

A single-page web application for encrypting and decrypting text using Caesar Cipher, Vigenère Cipher, and AES-GCM. It validates the input and method, displays the result, and lets you copy it.

## Run locally

Requires a recent browser and Python 3 for the local server. From this folder:

```bash
python -m http.server 8000
```

Open http://localhost:8000. The browser's Web Crypto API requires `localhost` or HTTPS for AES-GCM.

## Use

1. Enter text and select a method.
2. Enter a shift, keyword, or password as requested.
3. Click **Encrypt**. To decrypt, paste the ciphertext into **Input text**, use the same method and key, and click **Decrypt**.
4. Click **Copy result** if you need the output elsewhere.

Caesar and Vigenère are educational ciphers and should not protect sensitive information. AES-GCM is the secure encryption option; keep its password because the application does not store it.

## Files

- `index.html` — page structure
- `style.css` — styling
- `script.js` — validation and algorithms
- `REPORT.md` — short report on the techniques
- `DEMO_SCRIPT.md` — walkthrough for the required demo recording
