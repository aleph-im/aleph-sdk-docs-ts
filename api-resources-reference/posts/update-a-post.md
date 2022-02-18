---
description: Uses the create post endpoint to update the original post.
---

# Update a post

Update the specific post by [creating a new post](create-a-post.md) with the `postType` `amend` and the original post __ `item_hash` as the `ref` along with the new `content.`

### Usage

```javascript
import { post } from 'aleph-sdk-ts'
import { ItemType } from "aleph-sdk-ts/messages/message"

(async() => {
  await post.Publish({
    account: account,
    postType: 'amend',
    content: {'body': 'test post written on Aug 17th edited'},
    channel: 'TEST',
    APIServer: 'https://api2.aleph.im',
    inlineRequested: true,
    storageEngine: ItemType.storage,
    ref: "63a77911a924f0d61632f2b74784af496fbd094a11fbeed76ad6455ffad18ef8"
  })
})()

// Returns the message that is being sent to the network
{
  chain: "<YOUR ACCOUNT CHAIN>",
  channel: "TEST",
  confirmed: false,
  item_content: "{\"type\":\"amend\",\"address\":\"0xEb19D760dAdFce03A27ef6460184C7976Fe5eFE0\",\"content\":{\"body\":\"test post written on Aug 17th edited\"},\"time\":1636144778.602,\"ref\":\"63a77911a924f0d61632f2b74784af496fb...",
  item_hash: ""f47f34ad2cd7ae011dd114abb2dd544502fe554be94586116799646f8d43ff74"",
  item_type: "INLINE",
  sender: "<YOUR ADDRESS APPEAR HERE>",
  signature: ""0x99dc18149d8c39391a16d999cf126e08a2a22a629c3855aefe5127c6235dfd43693b971e6d325459308ede7c903f00d3559ce153d0569e9d4bf914860f1a6af31b"",
  size: 0,
  time: 1636144778.602,
  type: "POST"
}
```
