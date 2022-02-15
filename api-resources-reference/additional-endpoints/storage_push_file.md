---
description: Call the .PushFileToStorageEngine() to push file to storage or IPFS.
---

# Push Files

### Returns

The function returns the file\_hash for the stored file or null if the file could not be stored.

```javascript
import { PushFileToStorageEngine } from "aleph-sdk-ts/messages/create/publish"
import { StorageEngine } from "aleph-sdk-ts/messages/message"

(async() => {
  await PushFileToStorageEngine({
    file: file, 
    APIServer: api_url,
    storageEngine: StorageEngine.STORAGE
  })
})()
```

### Required parameters

| Parameter                                                             | Description                                                                                                                                               |
| --------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:green;">**file**</mark> - _File or Blob or string_ | File to push to storage or ipfs                                                                                                                           |
| <mark style="color:green;">**APIServer**</mark> - _string_            | Target API server                                                                                                                                         |
| <mark style="color:green;">**storageEngine**</mark> - _StorageEngine_ | <p>Storage engine to use, either Aleph storage or IPFS. </p><p>Possible values: <code>StorageEngine.STORAGE</code> or <code>StorageEngine.IPFS</code></p> |

