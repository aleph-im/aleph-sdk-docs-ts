# Update one key

Use the [create endpoint](create-an-aggregate.md) to update a specific key content from an existing `Aggregate`.

Since creating an `Aggregate` message mutates the value of the specific key, if the key exists, the value object will be updated (mutated) with the object you are saving.

### Example

To illustrate the update process, below we are creating an aggregate, updating it, and showing you what the aggregate looks like through the calls.

```javascript
import { aggregate } from 'aleph-sdk-ts'
import { StorageEngine } from "aleph-sdk-ts/messages/message"

// CREATE NEW AGGREGATE WITH KEY "MY KEY" --------------------------

(async () => {
  await aggregate.Publish({
    account: account,
    key: 'test_key',
    content: {'a': 1, 'b': 2 },
    channel: "TEST",
    storageEngine: StorageEngine.STORAGE,
    inlineRequested: true,
    APIServer: "https://api2.aleph.im"
  })
})();

    // >> Returns undefined

    // RETRIEVE THE KEY "test_key" -------------------------------------
    await aggregate.Get(address: account.address, keys: ['test_key'])

    // >> { 'a': 1, 'b': 2 }

  ---------------------------------------------------------------------

  // UPDATE THE KEY "MYKEY" -------------------------------------------
  await aggregate.Publish({
      address: account.address, 
      key: 'mykey', 
      content: {'a': 3, 'c': 5}, 
      channel: 'TEST',
      storageEngine: "STORAGE",
      inlineRequested: true,
      APIServer: "https://api2.aleph.im"
    }
  )

  // >> Returns the Aggregate object with the item_content key and
  // content that were passed in
  // {
  //   chain: 'ETH',
  //   channel: 'TEST',
  //   sender: '<ADDRESS WOULD DISPLAY HERE>',
  //   type: 'AGGREGATE',
  //   time: 1629242218.859,
  //   item_type: 'inline',
  //   item_content: '{"address":"<ADDRESS WOULD DISPLAY HERE>",
  //                    "key":"mykey",
  //                    "content":{'a': 3, 'c': 5},
  //                    "time":1629242218.859}',
  //   item_hash: 'd1a71b97cff51d9a1623a85c847675e85b36b5eb30239a715249b17698d6b7dc',
  //   signature: '0xdc7f26dd94f58b50cba058c6c47dc57f750b83149b94e5007a83f7feed11252774b620593c17daa7cf39ec9206d150a53b4bbbac8a7f1629894d30d583b742c61c'
  // }

  ---------------------------------------------------------------------

  // RETRIEVE THE KEY------- -------------------------------------------
 await aggregate.Get({address: account.address, keys: ['mykey']})

  // >> { 'a': 3, 'b': 2, 'c': 5 }
  
})();
```

