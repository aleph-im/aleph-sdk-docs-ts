# Connect Existing Chain Account

Existing blockchain accounts can be imported through the library in an Account object to allow for the use of the private key to sign messages.&#x20;

Different options are available to make the connection:&#x20;

* the chain account private key&#x20;
* the chain account secret phrase

Not all options are available on each chain module. Please refer below to see the connecting methods available for the needed chain.

### From Private key

You can connect with **any existing blockchain account** by using the relevant import function and passing in either the private key of the account depending on the chain used.

{% tabs %}
{% tab title="Ethereum" %}
```javascript
// FUNCTION SIGNATURE
await ethereum.ImportAccountFromPrivateKey(privateKey: null)

                    -----------------------

// EXAMPLE FROM PRIVATE KEY
import { ethereum } from 'aleph-sdk-ts/accounts'
account = await ethereum.ImportAccountFromPrivateKey('<Your Private Key Here>')

// RETURNS THE ACCOUNT OBJECT
{
  address: "<address>", 
  publicKey: "<public key>",
  wallet: <wallet object>
}
```
{% endtab %}

{% tab title="Solana" %}
```javascript
// FUNCTION SIGNATURE
await solana.ImportAccountFromPrivateKey(privateKey: null)

-----------------------------------------------------------

// EXAMPLE FROM PRIVATE KEY
import { solana } from 'aleph-sdk-ts/accounts'

// Import account from private key
account = await solana.ImportAccountFromPrivateKey('<Your Private Key>')

// RETURNS THE ACCOUNT OBJECT
{
  publicKey: '<PUBLIC KEY>',
  address: '<ADDRESS>',
  wallet: <Wallet object { }>
}
```
{% endtab %}

{% tab title="Substrate" %}
```typescript
// FUNCTION SIGNATURE
await substrate.ImportAccountFromPrivateKey(privateKey: null)

-----------------------------------------------------------

// EXAMPLE FROM PRIVATE KEY
import { substrate } from 'aleph-sdk-ts/accounts'

// Import account from private key
account = await substrate.ImportAccountFromPrivateKey('<Your Private Key>')

// RETURNS THE ACCOUNT OBJECT
{
  publicKey: '<PUBLIC KEY>',
  address: '<ADDRESS>',
  pair: <pair object { }>
}
```
{% endtab %}

{% tab title="Nuls/Nuls2" %}
```typescript
// FUNCTION SIGNATURE
await nuls.ImportAccountFromPrivateKey(privateKey: null, {chain_id =1, prefix=1})
await nuls2.ImportAccountFromPrivateKey(privateKey: null, {chain_id =1, prefix="NULS"})

-----------------------------------------------------------

// EXAMPLE FROM PRIVATE KEY
import { nuls } from 'aleph-sdk-ts/accounts'

// Import account from private key
account = await nuls.ImportAccountFromPrivateKey('<Your Private Key>')

// RETURNS THE NULSAccount OBJECT
{
  address: "<address>",
  publicKey: "<Public key>",
  privateKey: "<Private key>"
}
```
{% endtab %}
{% endtabs %}

### From Mnemonics

You can connect with **any existing blockchain account** by using the relevant import function and passing in the mnemonics of the account depending on the chain used.\


{% tabs %}
{% tab title="Ethereum" %}
```typescript
// FUNCTION SIGNATURE
await ethereum.ImportAccountFromMnemonic(mnemonic: null, derivationPath: "m/44'/60'/0'/0/0")
                    
                    -----------------------
                    
// EXAMPLE
import { ethereum } from 'aleph-js'

account = await ethereum.ImportAccountFromMnemonic("<Your Mnemonic Here>")

// RETURNS THE ACCOUNT OBJECT
{
  address: "<address>", 
  publicKey: "<public key>",
  wallet: <wallet object>
}

```
{% endtab %}

{% tab title="Substrate" %}
```typescript
// FUNCTION SIGNATURE
await substrate.ImportAccountFromMnemonic(mnemonic: null)

-----------------------------------------------------------

// EXAMPLE FROM PRIVATE KEY
import { substrate } from 'aleph-sdk-ts/accounts'

// Import account from private key
account = await substrate.ImportAccountFromMnemonic('<Your Mnemonic>')

// RETURNS THE ACCOUNT OBJECT
{
  publicKey: '<PUBLIC KEY>',
  address: '<ADDRESS>',
  pair: <pair object { }>
}
```
{% endtab %}

{% tab title="Nuls/Nuls2" %}
```typescript
// FUNCTION SIGNATURE
await nuls.ImportAccountFromMnemonic(mnemonic: null, {chain_id =1, prefix=1})
await nuls2.ImportAccountFromMnemonic(mnemonic: null, {chain_id =1, prefix="NULS"})

-----------------------------------------------------------

// EXAMPLE FROM PRIVATE KEY
import { nuls } from 'aleph-sdk-ts/accounts'

// Import account from private key
account = await nuls.ImportAccountFromMnemonic('<Your Mnemonic>')

// RETURNS THE NULSAccount OBJECT
{
  address: "<address>",
  publicKey: "<Public key>",
  privateKey: "<Private key>"
}
```
{% endtab %}
{% endtabs %}
