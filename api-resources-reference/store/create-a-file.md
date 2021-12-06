---
description: Call the .submit() function to create a store object and save a file.
---

# Create a store

### Returns

The hash of the file that was just pushed to the Storage Engine.



### Usage & Example

```javascript
import { store } from 'aleph-sdk-ts'
import { StorageEngine } from "aleph-sdk-ts/messages/message"

(async() => {

  const file = new File(
      ["This is just a test v2."],
      "test.txt",
      {
        type: "text/plain"
      }
    );

  const confirmation = await store.Publish({
    channel: "TEST",
    account: account,
    fileObject: file,
    storageEngine: StorageEngine.STORAGE,
    APIServer: DEFAULT_API_V2,
  });
  
  // returns the file hash that was stored:
  // "81607cfaab2de2774f837fe006e9b3cec4632388ed2738457d4e88f7429d7e83"
      
})()

```



### Required parameters

| Parameter                                                                       | Description                                                                                                                                                                                                                     |
| ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:green;">**account**</mark> - _account_                       | Account to use for signing.                                                                                                                                                                                                     |
| <mark style="color:green;">**channel**</mark> - _string_                        | Channel of the message. Ideally, an application would decide and use one channel.                                                                                                                                               |
| <mark style="color:green;">**fileObject**</mark> - _file_ or _blob_ or _string_ | The file you want to store.                                                                                                                                                                                                     |
| <mark style="color:green;">**storageEngine**</mark> - _StorageEngine_           | <p>Storage engine to use, either Aleph storage or IPFS. </p><p>Possible values: <code>StorageEngine.STORAGE</code> or <code>StorageEngine.IPFS</code></p>                                                                       |
| <mark style="color:green;">**APIServer**</mark> - _string_                      | <p>Select an API server accepting files.</p><p>ex: <a href="https://api2.aleph.im">https://api1.aleph.im</a> and "<a href="https://api2.aleph.im">https://api2.aleph.im</a>" are two available API servers accepting files.</p> |

###

### Retrieve file via direct url

{% hint style="info" %}
In the response, **item\_hash** can be used to **retrieve** the stored file **via** a **direct URL** as follow:

**https://\<API SERVER URL>/api/v0/storage/raw/\<File Item Hash Here>**

Api server can be any api server accepting files.



Or at the IPFS URL: **https://ipfs.io/ipfs/\<File Item Hash Here>**
{% endhint %}

```javascript
// item_hash
// => QmQkv43jguT5HLC8TPbYJi2iEmr4MgLgu4nmBoR4zjYb3L

To retrieve file via direct url:

https://ipfs.io/ipfs/QmQkv43jguT5HLC8TPbYJi2iEmr4MgLgu4nmBoR4zjYb3L

https://api2.aleph.im/api/v0/storage/raw/QmQkv43jguT5HLC8TPbYJi2iEmr4MgLgu4nmBoR4zjYb3L
```
