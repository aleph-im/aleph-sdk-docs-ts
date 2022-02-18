---
description: Encrypt content for an address public key using the .encrypt() function.
---

# Encrypt

Encryption in aleph.im uses the [ECIES standard](https://en.wikipedia.org/wiki/Integrated\_Encryption\_Scheme), using the [ECIES Js library](https://github.com/ecies/js) on SECP256K1. Beta encryption for curve ed25519 available.

### Returns

This will return the encrypted content.

### Usage

```javascript
import { ethereum } from 'aleph-sdk-ts/accounts'

account = await ethereum.ImportAccountFromPrivateKey('<Your Private Key Here>')

await account.encrypt(content: <Buffer Content>)
```

.encrypt() is available on all accounts: ethereum, nuls, nuls2, solana and substrate.

{% hint style="info" %}
For Solana accounts:&#x20;

Encryption puts content into a tweetnacl secret box for a solana account. **THIS ENCRYPTION IS NOT SAFE** as the nonce is returned by the function.
{% endhint %}
