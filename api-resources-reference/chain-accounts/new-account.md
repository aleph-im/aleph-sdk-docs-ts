# Generate & Connect New Chain Account

To create a new account, use the `NewAccount` function. Aleph will create a blockchain account on the chain of your choice and import it as an `Account` object.&#x20;

Call the NewAccount() function on the corresponding chain module of your choice:

{% tabs %}
{% tab title="Ethereum" %}
```javascript
// FUNCTION SIGNATURE
await ethereum.NewAccount(derivationPath?: "m/44'/60'/0'/0/0")

-----------------------------------------------

//EXAMPLE
import { ethereum } from 'aleph-sdk-ts'

account = await ethereum.NewAccount()

// --> RETURNS THE ACCOUNT OBJECT
{ address: '<Address generated>',
  publicKey: '<PUBLIC KEY>',
  wallet: { } }
```
{% endtab %}

{% tab title="Solana" %}
```javascript
// FUNCTION SIGNATURE
await solana.NewAccount()

------------------------------------------------

//EXAMPLE
import { solana } from 'aleph-sdk-ts/accounts'
account = await solana.NewAccount()

// RETURNS THE ACCOUNT OBJECT
{ address: '<ADDRESS>',
  publicKey: '<PUBLIC KEY>',
  wallet: { <Wallet object> } }
```
{% endtab %}

{% tab title="Substrate" %}
```typescript
// FUNCTION SIGNATURE
await substrate.NewAccount()

------------------------------------------------

//EXAMPLE
import { substrate } from 'aleph-sdk-ts/accounts'
account = await substrate()

// RETURNS THE ACCOUNT OBJECT
{ address: '<ADDRESS>',
  publicKey: '<PUBLIC KEY>',
  wallet: { <Wallet object> } }
```


{% endtab %}
{% endtabs %}

Some of the chains allow for passing extra parameters to create the blockchain account. Below you will find a table of the optional parameters.

| Chain        | Parameters                                      | Default value        |
| ------------ | ----------------------------------------------- | -------------------- |
| **Ethereum** | <mark style="color:blue;">derivationPath</mark> | `"m/44'/60'/0'/0/0"` |
