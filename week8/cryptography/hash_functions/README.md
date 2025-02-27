---
description: >-
    Hash functions are a fundamental building block of cryptography. They are used
    to map arbitrary data to a fixed-length digest. This digest can be used to
    verify the integrity of the data, or to verify that the data has not been
    tampered with. In this chapter, we will learn about the basics of hash
    functions, and how they are used in practice.
---

In computer programming hash functions map text (or other data) to integer numbers. Usually different inputs maps to different outputs, but sometimes a collision may happen (different input with the same output).

Cryptographic hash functions transform text or binary data to fixed-length hash value and are known to be collision-resistant and irreversible. Example of cryptographic hash function is SHA3-256:

```sh
SHA3-256("hello") = "3338be694f50c5f338814986cdf0686453a888b84f424d792af4b9202398f392"
```

The above SHA3-256 hash calculation can be coded in Python like this:

```python
import hashlib, binascii

data = b"hello"
hash = hashlib.sha3_256(data).digest()
print(binascii.hexlify(hash))
```
# Hashing (in Software Engineering)
The process of calculating the value of certain hash function is called "hashing".

![Hashing example](https://60896510-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LhlOQMrG9bRiqWpegM0%2Fuploads%2Fgit-blob-0f0ddfddcd3f1514f3c619167d896267d22b4d37%2Fhash-function.jpg?alt=media)

In the above example the text John Smith is hashed to the hash value 02 and Lisa Smith is hashed to 01. The input texts John Smith and Sandra Dee both are hashed to 02 and this is called "collision".

Hash functions are irreversible by design, which means that there is no fast algorithm to restore the input message from its hash value.

In programming hash functions are used in the implementation of the data structure "hash-table" (associative array) which maps values of certain input type to values of another type, e.g. map product name (text) to product price (decimal number).

A naive hash function is just to sum the bytes of the input data / text. It causes a lot of collisions, e.g. hello and ehllo will have the same hash code. 

Better hash functions may use the Merkle–Damgård construction scheme, which takes the first byte as state, then transforms the state (e.g. multiplies it by a prime number like 31), then adds the next byte to the state, then again transforms the state and adds the next byte, etc. This significantly reduces the rate of collisions and produces better distribution.

# Cryptographic Hash Functions
In cryptography, hash functions transform input data of arbitrary size (e.g. a text message) to a result of fixed size (e.g. 256 bits), which is called hash value (or hash code, message digest, or simply hash). Hash functions (hashing algorithms) used in computer cryptography are known as "cryptographic hash functions". Examples of such functions are SHA-256 and SHA3-256, which transform arbitrary input to 256-bit output.

![Cryptographic Hash Functions](https://60896510-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LhlOQMrG9bRiqWpegM0%2Fuploads%2Fgit-blob-117671d5576ceee0211790605de60e2c17219521%2Fcrypto-hash-function.jpg?alt=media)

## Cryptographic Hash Functions - Examples
As an example, we can take the cryptographic hash function SHA-256 and calculate the hash value of certain text message hello:

```sh
SHA-256("hello") = "2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824"
```

The above SHA-256 calculation can be coded in Python like this:

```python
import hashlib, binascii

sha256hash = hashlib.sha256(b'hello').digest()
print("SHA-256('hello') = ", binascii.hexlify(sha256hash))
```

There is no efficient algorithm to find the input message (in the above example hello) from its hash value (in the above example `2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824`). It is well-known that cryptographic hash functions cannot be reversed back, so they are used widely to encode an input without revealing it (e.g. encode a private key to a blockchain address without revealing the key).
As another example, we can take the cryptographic hash function SHA3-512 and calculate the hash value of the same text message hello:

```sh
SHA3-512("hello") = "75d527c368f2efe848ecf6b073a36767800805e9eef2b1857d5f984f036eb6df891d75f72d9b154518c1cd58835286d1da9a38deba3de98b5a53e5ed78a84976"
```
## Cryptographic Hash Functions - Live Demo
Play with most popular cryptographic hash functions online: https://www.fileformat.info/tool/hash.htm.

![Cryptographic Hash Functions - Live Demo](https://60896510-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LhlOQMrG9bRiqWpegM0%2Fuploads%2Fgit-blob-224bd88017f2073a5a5f81d42b51a2ff3a56d91c%2Fhash-functions-online.png?alt=media)

Cryptographic hash functions are widely used in cryptography, in computer programming and in blockchain systems.