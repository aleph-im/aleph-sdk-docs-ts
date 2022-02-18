---
description: >-
  Creates a FORGET Message referencing Messages where the content and
  item_content will be emptied.
---

# Forget a message

### Returns

A forget message object that is being sent to the network.

### Usage & Example

```typescript
import { forget } from 'aleph-sdk-ts'
import { ItemType } from "aleph-sdk-ts/messages/message"

(async() => {
  await forget.publish({
    account: account,
    channel: 'TEST',
    storageEngine: ItemType.inline,
    inlineRequested: true,
    APIServer: 'https://api2.aleph.im',
    hashes: ['<item_hash_here>']
  })
})()
```

### Required parameters

| <mark style="color:green;">**account**</mark> - _Account_         | <p>Account submitting the forget message. Should either be:</p><ul><li>The sender of the original message to forget OR the sender of the VM that created the message.</li><li>The address the original message was attributed to</li></ul> |
| ----------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <mark style="color:green;">**channel**</mark> - _string_          | Channel of the message. Ideally, an application would decide and use one channel.                                                                                                                                                          |
| <mark style="color:green;">**storageEngine**</mark> _- ItemType_  | The storage engine to use when storing the object (IPFS or Aleph)                                                                                                                                                                          |
| <mark style="color:green;">**inlineRequested**</mark> _- boolean_ | Will the message be inlined ?                                                                                                                                                                                                              |
| <mark style="color:green;">**APIServer**</mark> _- string_        | The API server endpoint used to carry the request to the Aleph's network.                                                                                                                                                                  |
| <mark style="color:green;">**hashes**</mark> - _array of strings_ | A list of original message item hashes to forget. Multiple can be passed at once.                                                                                                                                                          |

### Optional parameters

* <mark style="color:green;">**reason**</mark> - _string_\
  Optional description of why the messages should be forgotten.
