---
description: Call the .submit() function to create a Post
---

# Create a post

### Returns

A base message object that is being sent to the network.

{% hint style="success" %}
**Tips** \
Pass a **ref** in the optional object parameter and/or **tags** in your content to take full advantage of the filtering abilities later on.
{% endhint %}



### Usage & Example

```javascript
import { post } from 'aleph-sdk-ts'
import { StorageEngine } from "aleph-sdk-ts/messages/message"

(async() => {
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

// Returns the message that is being sent to the network
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

###

### Required parameters

| Parameter                                                             | Description                                                                                                                                                                                                                               |
| --------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:green;">**account**</mark> - _Account_             | <p>Address the Post should be associated with <br>or the address that submitted the Post.</p>                                                                                                                                             |
| <mark style="color:green;">**postType**</mark> - _string_             | <p>A lowercase string of your choice for the <code>item_content.type</code> of the post message.<br> ex: <code>amend</code>,<code>blog</code>, <code>chat</code>, <code>comment</code></p>                                                |
| <mark style="color:green;">**content**</mark> - _object_              | <p>The content object to save to the <code>item_content.content</code> of the post message.</p><p><mark style="background-color:yellow;">If <code>tags</code> are passed within the object, they can be searched for later on.</mark></p> |
| <mark style="color:green;">**channel**</mark> - _string_              | Channel of the message. Ideally, an application would decide and use one channel.                                                                                                                                                         |
| <mark style="color:green;">**inlineRequested**</mark> - _boolean_     | <p>Should the message be stored as a separate file or inserted inline? </p><p><span data-gb-custom-inline data-tag="emoji" data-code="2139">ℹ</span> Set it to false for data that could fall under GDPR.</p>                             |
| <mark style="color:green;">**storageEngine**</mark> - _StorageEngine_ | <p>Storage engine to use, either Aleph storage or IPFS. </p><p>Possible values: <code>StorageEngine.STORAGE</code> or <code>StorageEngine.IPFS</code></p>                                                                                 |
| <mark style="color:green;">**APIServer**</mark> - _string_            | Target API server                                                                                                                                                                                                                         |

###

### Optional parameters

* <mark style="color:green;">**ref**</mark> - _string or object with the following structure_

```typescript
{ chain: string; 
channel? : string;
item_content: string;
item_hash: string;
item_type: string;
sender: string;
signature: string;
time: number;
type:string; }
```

A searchable reference string of your choice to save to the `item_content.ref`.\
Can be the reference to another post, an address, transaction hash, etc.

