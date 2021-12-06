# Broadcast Message

### Sign Message & Broadcast

Message, account and api\_server are required.

```javascript
import { signature } from "aleph-sdk-ts/messages/create";

(async() => {
  await signature.SignAndBroadcast({
    message: message_to_broadcast,
    account: account,
    APIServer: api_url
  })
})()
```

### Required parameters

| Parameter                                                  | Description                 |
| ---------------------------------------------------------- | --------------------------- |
| <mark style="color:green;">**message**</mark> - _object_   | Message to broadcast        |
| <mark style="color:green;">**account**</mark> - _Account_  | Account to sign the message |
| <mark style="color:green;">**APIServer**</mark> - _string_ | Target API server           |

{% hint style="info" %}
message object should have the following structure:

```
{
  _id?: MongoDBID;
  chain: ChainType;
  sender: string;
  type: MessageType;
  channel: string;
  confirmations?: MessageConfirmation[];
  confirmed: boolean;
  signature: string;
  size: number;
  time: number;
  item_type: StorageEngine | "INLINE";
  item_content: string;
  hash_type?: string;
  item_hash: string;
  content?: {address: string, time: number;};
}
```
{% endhint %}

### Optional parameters

None
