# 🔓 Encryption

Encryption in aleph.im uses the [ECIES standard](https://en.wikipedia.org/wiki/Integrated\_Encryption\_Scheme), using the [ECIES Js library](https://github.com/ecies/js) on SECP256K1.

Content is encrypted for a specific public key and can be decrypted with the same account private key that was used for encryption.

| ENDPOINTS             | functions                |
| --------------------- | ------------------------ |
| [Encrypt](encrypt.md) | [.encrypt()](encrypt.md) |
| [Decrypt](decrypt.md) | [.decrypt()](decrypt.md) |
