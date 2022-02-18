# Decrypt

### Returns

Decrypt content with the account the content was encrypted for. This will return the decrypted content.

### Usage

```javascript
import { ethereum } from 'aleph-sdk-ts/accounts'

account = await ethereum.ImportAccountFromPrivateKey('<Your Private Key Here>')

await account.decrypt(encryptedContent: <Buffer Content>)

```

Available for ethereum, nuls, nuls2, solana and substrate accounts.

{% hint style="info" %}
For Solana accounts, the function returns a promise.
{% endhint %}
