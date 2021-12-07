# Put Content

The .PutContentToStorageEngine() function:&#x20;

* serializes or saves the content object of the message to either ipfs or storage server&#x20;
* adds the item\_hash from the content to the message object.

All parameters are required.&#x20;

`inlineRequested` can be either true or false. If true, the content will be serialized otherwise the content is saved to:&#x20;

* ipfs if "IPFS" is passed as `storage_engine`&#x20;
* storage otherwise.

```javascript
import { PutContentToStorageEngine } from "aleph-sdk-ts/messages/create/publish"
import { StorageEngine } from "aleph-sdk-ts/messages/message"

(async() => {
  await PutContentToStorageEngine({
    message: message,
    content: content,
    inlineRequested: true,
    storageEngine: StorageEngine.STORAGE,
    APIServer: "https://api2.aleph.im"
  })
})()
```

| Parameter                                                             | Description                                                                                                                                               |
| --------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:green;">**message**</mark> - _Message_             | Message the item\_hash will be added to.                                                                                                                  |
| <mark style="color:green;">**content**</mark> - _object_              | Content to save to storage.                                                                                                                               |
| <mark style="color:green;">**inlineRequested**</mark> - _boolean_     | Whether to serialize the content or not.                                                                                                                  |
| <mark style="color:green;">**storageEngine**</mark> - _StorageEngine_ | <p>Storage engine to use, either Aleph storage or IPFS. </p><p>Possible values: <code>StorageEngine.STORAGE</code> or <code>StorageEngine.IPFS</code></p> |
| <mark style="color:green;">**APIServer**</mark> - _string_            | Target API server                                                                                                                                         |
