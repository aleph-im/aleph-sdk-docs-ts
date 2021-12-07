---
description: >-
  Writing to the network requires a blockchain account which will serve as the
  referenced account on the resource generated.
---

# Posting to the Network

{% hint style="success" %}
Posting to the network is done in two steps:

1. Connect a blockchain account
2. Create a resource
{% endhint %}

### 1. Connect a blockchain account

The aleph typescript SDK currently supports the following chains:

* Ethereum
* Solana
* Substrate

Whether you connect to an existing blockchain account or create a new one, the account returned by the library is an object having:

* an `address`
* a `publicKey`
* a `wallet` object

#### ➡️  With an existing blockchain account

You can connect **any existing blockchain account** by using the `ImportAccount` function and passing in either the **private key** or the **mnemonics** of the account depending on the chain used.

{% tabs %}
{% tab title="Ethereum" %}
```typescript
import { ethereum } from 'aleph-sdk-ts/accounts'

// Import account from mnemonics
account = await ethereum.ImportAccountFromMnemonic('<YOUR PASSPHRASE HERE>')

// Import account from private key
account = await ethereum.ImportAccountFromPrivateKey("<YOUR PRIVATE KEY HERE>")

```
{% endtab %}

{% tab title="Solana" %}
```typescript
import { solana } from 'aleph-sdk-ts/accounts'

// Import account from private key
account = await solana.ImportAccountFromPrivateKey('<YOUR PRIVATE KEY>')
```
{% endtab %}

{% tab title="Substrate" %}
```typescript
import { substrate } from 'aleph-sdk-ts/accounts'

// Import account from private key
account = await substrate.ImportAccountFromPrivateKey('<YOUR PRIVATE KEY>')

// Import account from mnemonic
account = await substrate.ImportAccountFromMnemonic('<YOUR MNEMONICS>')
```
{% endtab %}
{% endtabs %}



#### ➡️  With a newly created account

If your application user does not have a chain account yet, an account can be created for them with the `NewAccount` function.

Make sure the user has access and save the details of the account created for them.

{% tabs %}
{% tab title="Ethereum" %}
```javascript
import { ethereum } from 'aleph-sdk-ts/accounts'

(async() => {
    account = await ethereum.NewAccount()
})()
```
{% endtab %}

{% tab title="Solana" %}
```javascript
import { solana } from 'aleph-sdk/accounts'

(async() => {
    account = await solana.NewAccount()
})()
```
{% endtab %}

{% tab title="Substrate" %}
```typescript
import { substrate } from 'aleph-sdk/accounts'

(async() => {
    account = await substrate.NewAccount()
})()
```
{% endtab %}
{% endtabs %}

{% hint style="success" %}
More details on importing and creating an account are available [here](../api-resources-reference/chain-accounts/).&#x20;
{% endhint %}

### 2. Create a resource

```javascript
import { post } from 'aleph-sdk'
import { ethereum } from 'aleph-sdk/accounts'
import { StorageEngine } from "aleph-sdk-ts/messages/message"

(async() => {
  // Import account from the correct chain to post to Aleph
  account = await ethereum.ImportAccountFromMnemonic('<YOUR PASSPHRASE HERE>')
  
  await post.Publish({
    account: account,
    postType: 'mytype',
    content: {'body': 'test post written on Aug 17th'},
    channel: 'TEST',
    APIServer: 'https://api2.aleph.im',
    inlineRequested: true,
    storageEngine: StorageEngine.STORAGE
  })
 })()
```

🎉 A `Message` object, with a POST type, has been created and is returned.

```javascript
{
  chain: "<YOUR ACCOUNT CHAIN>",
  channel: "TEST",
  confirmed: false,
  item_content: "{\"type\":\"mytype\",\"address\":\"<YOUR ADDRESS APPEAR HERE>\",\"content\":{\"body\":\"test post written on Aug 17th\"},\"time\":1636137569.869}",
  item_hash: "8671a9bb4dac018a0bd8b5c56ac883fd551f43af2b01d34e60215a8419d555b0",
  item_type: "INLINE",
  sender: "<YOUR ADDRESS APPEAR HERE>",
  signature: "0x0338f9c3ae1eb4715a923094f4ee5459a3131e54b393b9640c137f11cb5fc8c131299723fb19c2cdd971ee60c6cd68bb9643c93d92e918e8be1ec787657da9631b",
  size: 0,
  time: 1636137569.869,
  type: "POST"
}
```

{% hint style="info" %}
All <mark style="color:purple;">posts</mark>, <mark style="color:purple;">aggregates</mark> and <mark style="color:purple;">stores</mark> resources created in Aleph are inherently <mark style="color:purple;">**Message**</mark> Objects. <mark style="color:purple;">Depending on the type of resource created, the item\_content object keys will differ</mark>.
{% endhint %}

### 3. Going further

Learn more about how you can create, update and query [Post](../api-resources-reference/posts/), [Aggregate](../api-resources-reference/aggregates/) and [Store](../api-resources-reference/store/) objects.&#x20;
