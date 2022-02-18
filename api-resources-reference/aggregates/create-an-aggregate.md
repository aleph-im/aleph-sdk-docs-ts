---
description: >-
  Call the .Publish function to create an aggregate of a key-value pair for an
  account.
---

# Create an aggregate key

### Returns

An aggreagte message object that is being sent to the network.

### Usage & Example

```javascript
import { aggregate } from 'aleph-sdk-ts'
import { StorageEngine } from "aleph-sdk-ts/messages/message"

(async () => {
  await aggregate.Publish({
    account: account,
    key: 'test_key',
    content: {'a': 1, 'b': 2 },
    channel: "TEST",
    storageEngine: ItemType.storage,
    inlineRequested: true,
    APIServer: "https://api2.aleph.im"
  })
})();
```

### Required parameters

| Parameter                                                         | Description                                                                                                                                     |
| ----------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:green;">**account**</mark> - _Account_         | Sender's account to use for signing.                                                                                                            |
| <mark style="color:green;">**key**</mark> - _string_              | Key to mutate                                                                                                                                   |
| <mark style="color:green;">**content**</mark>  - _object_         | <p>The value content object to save for the key. Must be of the following format:</p><p><code>{k_1: v_1, k_2: v_2}</code></p>                   |
| <mark style="color:green;">**channel**</mark> - _string_          | Channel of the message. Ideally, an application would decide and use one channel.                                                               |
| <mark style="color:green;">**storageEngine**</mark> - _ItemType_  | <p>Storage engine to use, either Aleph storage or IPFS. </p><p>Possible values: <code>ItemType.storage</code> or <code>ItemType.ipfs</code></p> |
| <mark style="color:green;">**inlineRequested**</mark> - _boolean_ | Should the message be stored as a separate file or inserted inline? :information\_source: Set it to false for data that could fall under GDPR.  |
| <mark style="color:green;">**APIServer**</mark> - _string_        | The API server endpoint used to carry the request to the Aleph's network                                                                        |

