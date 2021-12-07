# Connect Existing Chain Account

Existing blockchain accounts can be imported through the library in an Account object to allow for the use of the private key to sign messages.&#x20;

Different options are available to make the connection:&#x20;

* the chain account private key&#x20;
* the chain account secret phrase

Not all options are available on each chain module. Please refer below to see the connecting methods available for the needed chain.

### From Private key or Mnemonics

You can connect with **any existing blockchain account** by using the relevant import function and passing in either the private key or the mnemonics of the account depending on the chain used.

{% tabs %}
{% tab title="Ethereum" %}
```javascript
// FUNCTION SIGNATURE
await ethereum.ImportAccountFromMnemonic(mnemonic: null, derivationPath: "m/44'/60'/0'/0/0")
                    -----------------------
                    
// EXAMPLE FROM MNEMONICS
import { ethereum } from 'aleph-js'

account = await ethereum.ImportAccountFromMnemonic('<Your Mnemonic Here>')

-----------------------------------------------------------------
-----------------------------------------------------------------

// FUNCTION SIGNATURE
await ethereum.ImportAccountFromPrivateKey(privateKey: null)

                    -----------------------

// EXAMPLE FROM PRIVATE KEY
import { ethereum } from 'aleph-sdk-ts/accounts'
account = await ethereum.ImportAccountFromPrivateKey('<Your Private Key Here>')

// RETURNS THE ACCOUNT OBJECT
{
  public_key: '<PUBLIC KEY>',
  address: '<ADDRESS>',
  wallet: <Wallet object { }>
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
  public_key: '<PUBLIC KEY>',
  address: '<ADDRESS>',
  wallet: <Wallet object { }>
}
```
{% endtab %}
{% endtabs %}

###
