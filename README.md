# Fext
Secure and Serverless File Encryption.



  [![Status](https://img.shields.io/badge/status-active-success.svg)](#)
  [![Build](https://travis-ci.org/whichbuffer/Fext.svg?branch=master&status=passed)](https://travis-ci.org/whichbuffer/Fext)
  [![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](#)
  
  ## How to use
just simply browse a file, type a decryption key or use random secure key generator, and encrypt or decrypt.

## Installation

Download or clone the repository

 

    $ git clone https://github.com/whichbuffer/Fext.git  Fext

go to the app directory

    cd [app directory]

open terminal and install the node modules that are in the package.json file

    sudo npm install


## Browser Compatibility
We officially support the last two versions of every major browser. Specifically, we test on the following 
-   **Chrome**  on Windows, macOS, and Linux , IOS, Android
-   **Firefox**  on Windows, macOS, and Linux
-   **Safari**  on iOS and macOS
-   **Edge**  on Windows
-   **IE 11**  on Windows

for more info see [WebCryptoAPI](https://developer.mozilla.org/en-US/docs/Web/API/Web_Crypto_API) home page
![enter image description here](https://i.imgur.com/hJveblf.png)


## Crypto Examples

#### AES-GCM - generateKey
```javascript
  window.crypto.subtle.generateKey(
    {
      name: "AES-GCM",
      length: 256,
    },
    true,
    ["encrypt", "decrypt"]
  )
.then(function(key){
    console.log(key);
})
.catch(function(err){
    console.error(err);
});
```
#### AES-GCM - importKey
```javascript
function importSecretKey(rawKey) {
    return window.crypto.subtle.importKey(
      "raw",
      rawKey,
      "AES-GCM",
      true,
      ["encrypt", "decrypt"]
    );
  }
.then(function(key){
    console.log(key);
})
.catch(function(err){
    console.error(err);
});
```
#### AES-GCM - exportKey
```javascript
async function exportCryptoKey(key) {
    const exported = await window.crypto.subtle.exportKey(
      "raw",
      key
    )
.then(function(keydata){
    console.log(keydata);
})
.catch(function(err){
    console.error(err);
});
```
#### AES-GCM - encrypt
```javascript
async function encryptMessage(key) {
    let encoded = getMessageEncoding();
    // The iv must never be reused with a given key.
    iv = window.crypto.getRandomValues(new Uint8Array(12));
    ciphertext = await window.crypto.subtle.encrypt(
            {
                name: "AES-GCM",
                iv: iv
            },
            key,
            encoded
        )
        .then(function (encrypted) {
            console.log(new Uint8Array(encrypted));
        })
        .catch(function (err) {
            console.error(err);
        });
}
```
#### AES-GCM - decrypt
```javascript
async function decryptMessage(key) {
    let encoded = getMessageEncoding();
    let decrypted = await window.crypto.subtle.decrypt({
            name: "AES-GCM",
            iv: iv
        },
        key,
        ciphertext
       )
       .then(function (decrypted) {
            console.log(new Uint8Array(encrypted));
        })
        .catch(function (err) {
            console.error(err);
        });
}
```


## Used Open Source Libraries
[zxcvbn.js](https://github.com/dropbox/zxcvbn) for Smart Password Strength Estimation

[bootstrap](https://github.com/twbs/bootstrap) for the responsive css layout

[font-awesome](https://github.com/FortAwesome/Font-Awesome) for the icons
