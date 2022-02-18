# The forget Object

The forget object inherits from the `Message` object's structure as follows:

```javascript
// Message info
channel:
time:
type:

// Sender info
chain:
sender:

// Content
hash_type:
item_content:
  resason:
  hashes:
item_hash:
item_type:
```

| Attributes                                                                          | Description                                                                                                                                                                    |
| ----------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <mark style="color:blue;">**channel**</mark> - _text_                               | Channel of the message. Ideally, an application would decide and use one channel.                                                                                              |
| <mark style="color:blue;">**time**</mark> _- float_                                 | Unix timestamp when the message was published (in seconds).                                                                                                                    |
| <mark style="color:blue;">**type**</mark> _- text_                                  | <p>Text representing the message object type.</p><p>Value is <code>FORGET</code></p>                                                                                           |
|                                                                                     |                                                                                                                                                                                |
| <mark style="color:blue;">**chain**</mark>** ** _- text_                            | <p>The chain used by the sender's account. <br>Value can be <code>NULS2</code>, <code>ETH</code>, <code>DOT</code>, <code>CSDK</code>, <code>SOL</code>, <code>AVAX</code></p> |
| <mark style="color:blue;">**sender**</mark> _- text_                                | Chain address who sent and is signing the Post Message.                                                                                                                        |
|                                                                                     | -                                                                                                                                                                              |
| <mark style="color:blue;">**hash\_type**</mark> _- optional text_                   | Defaults to sha256. This is the only supported value for now.                                                                                                                  |
| <mark style="color:blue;">**item\_content**</mark>** ** _- JSON text_               | <p>JSON string representing the content of the aggregate. </p><p>See below for the content of the string.</p>                                                                  |
|                                                                                     |                                                                                                                                                                                |
| item\_content.<mark style="color:blue;">**reason**</mark>** ** _- string_           | A description of why the messages are being forgotten.                                                                                                                         |
| item\_content.<mark style="color:blue;">**hashes**</mark>** ** _- list of strings_  | List of message item hashes to be removed.                                                                                                                                     |
|                                                                                     |                                                                                                                                                                                |
| <mark style="color:blue;">**item\_hash**</mark> _- hash_                            | The hash of the item\_content encrypted with SHA256.                                                                                                                           |
| <mark style="color:blue;">**item\_type**</mark> - _optional text_                   | `ipfs`, `inline` or `storage`                                                                                                                                                  |

