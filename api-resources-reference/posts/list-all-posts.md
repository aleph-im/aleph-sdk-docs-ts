---
description: >-
  Use the .Get() function to get the latest version of each post sorted by most
  recent
---

# List all posts

### Returns

The function **returns an object** containing a **posts array** as well as **details on the number** of posts and pages returned:

{% code title="Returned object structure" %}
```javascript
{ 
  posts: [ { ... }, { ... }, { ... }], 
  pagination_page: 1,
  pagination_total: 3,
  pagination_per_page: 200,
  pagination_item: 'posts'
 }
```
{% endcode %}

The "post objects" within the array returned are made of a combination of:

* the post message object
* additional details to help reference the original post (original\_...)
* the `post.item_content` object attributes (`type, content, address, time`) are merged in at the top level of the post result

{% code title="Post object in returned array" %}
```javascript
// Regular Post Message
channel:
time:
chain:
sender:
hash_type:
item_content:
  type:
  address:
  content:
  time:
  ref:
item_hash:
item_type:

// Details from original
original_item_hash
original_signature
original_tx_hash
original_type
original_ref
hash

// item_content object merged in
type:
content:
address:
time:
ref:

// Additional info from server
size:
confirmations:
confirmed:

```
{% endcode %}



### Usage & Example

```javascript
import { post } from 'aleph-sdk-ts'

(async() => {
  await post.Get({
    types: 'mytype', 
    pagination: 200,
    page: 1,
    refs: [], 
    addresses: [],
    tags: [],
    hashes: [],
    APIServer: "https://api2.aleph.im"
  })
})()
```

###

### Required parameters

| Parameter                                                                  | Description                                                                                                                                                                                                                                                                                                                                                                            |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:green;">**types**</mark> - _string or array of strings_ | <p>Posts with the "post_types" in the<code>item_content.type</code> as well as any last amended post where the original post type was "post_types"</p><p><br><mark style="background-color:yellow;">The value is a <strong>string</strong> of one type or <strong>multiple types separated with commas without extra space</strong>.</mark> </p><p>ex: <code>"blog,comment"</code></p> |
| <mark style="color:green;">**refs**</mark> - _array of strings_            | Array of Refs listed in the post `item_content.ref`                                                                                                                                                                                                                                                                                                                                    |
| <mark style="color:green;">**addresses**</mark> - _array of strings_       | <p>Array of addresses listed in the content address (<code>item_content.address</code>).</p><p>If multiple addresses are passed, any message with one of the queried addresses in the content address or sender attribute will be returned.</p>                                                                                                                                        |
| <mark style="color:green;">**tags**</mark> - _array of strings_            | <p>Array of Message content content tag. (<code>item_content.content.tags</code>).</p><p>If multiple tags are passed, messages with at least one of the tags present in the content content tags will be returned.</p>                                                                                                                                                                 |
| <mark style="color:green;">**hashes**</mark> - _array of strings_          | Array of hashes listed in the item hash (`item_hash`) or transaction hash (`tx_hash`).                                                                                                                                                                                                                                                                                                 |
| <mark style="color:green;">**APIServer**</mark> - string                   | Target API server.                                                                                                                                                                                                                                                                                                                                                                     |
| <mark style="color:green;">**pagination**</mark> - _number_                | The number of posts returned per page                                                                                                                                                                                                                                                                                                                                                  |
| <mark style="color:green;">**page**</mark> - _number_                      | <p>The page to be returned. </p><p>ex: page 1 or page 2</p>                                                                                                                                                                                                                                                                                                                            |

###

### Optional parameters

No optional parameters are available for this function.

###

### Example: .Get()

{% code title="GET_POSTS" %}
```javascript
let response = await post.Get({
    types: 'mytype', 
    pagination: 3,
    page: 1,
    refs: [], 
    addresses: [],
    tags: [],
    hashes: [],
    APIServer: "https://api2.aleph.im"
})
```
{% endcode %}

{% hint style="info" %}
In the response, the `item_content` object attributes (`type, content, address, time`) are merged in the post message object to be easily reachable. `Item_content` is still available in the message object as well.
{% endhint %}

{% hint style="info" %}
The `original_` fields are here in case you amended the post.&#x20;
{% endhint %}

{% hint style="info" %}
This function retrieves the latest version of all posts. If a post was updated twice after the original version was created, only the last updated post will show.&#x20;

To see all the changes made to a post, check [the next header item](list-all-posts.md#history-for-a-post) (To retrieve all changes made to a post)
{% endhint %}

{% code title="RESPONSE" %}
```javascript
{ posts:
 [
  {
    address: "0xEb19D760dAdFce03A27ef6460184C7976Fe5eFE0"
    chain: "ETH"
    channel: "TEST"
    confirmed: false
    content: {body: 'test post written on Aug 17th edited'}
    hash: "63a77911a924f0d61632f2b74784af496fbd094a11fbeed76ad6455ffad18ef8"
    item_content: "{\"type\":\"amend\",\"address\":\"0xEb19D760dAdFce03A27ef6460184C7976Fe5eFE0\",\"content\":{\"body\":\"test post written on Aug 17th edited\"},\"time\":1636144778.602,\"ref\":\"63a77911a924f0d61632f2b74784af496fbd094a11fbeed76ad6455ffad18ef8\"}"
    item_hash: "f47f34ad2cd7ae011dd114abb2dd544502fe554be94586116799646f8d43ff74"
    item_type: "inline"
    original_item_hash: "63a77911a924f0d61632f2b74784af496fbd094a11fbeed76ad6455ffad18ef8"
    original_signature: "0x724509a5aae2d1d126231f71915356f9e5420730d7183c52b8030ee9d1e7d9042e6418896c23a5d9cc46b53039985599c3d95ef4f355ac75e8a761f04e630cd31c"
    original_type: "mytype"
    ref: "63a77911a924f0d61632f2b74784af496fbd094a11fbeed76ad6455ffad18ef8"
    sender: "0xEb19D760dAdFce03A27ef6460184C7976Fe5eFE0"
    signature: "0x99dc18149d8c39391a16d999cf126e08a2a22a629c3855aefe5127c6235dfd43693b971e6d325459308ede7c903f00d3559ce153d0569e9d4bf914860f1a6af31b"
    size: 224
    time: 1636144778.602
    type: "amend"
    _id: {$oid: '6185968a16d179f0c1c2d8c5'}
  },
  {...},
  {...}
 ],
 pagination_page: 1,
 pagination_total: 3,
 pagination_per_page: 248,
 pagination_item: 'posts'
}
```
{% endcode %}

### History for a post

{% hint style="danger" %}
**To retrieve all updates made to a specific post** and the original post, **use** **list all messages** **endpoint** rather than list all posts referencing the original item hash.\
\
When using list all posts with the item\_hash reference, any updated posts, including amends of amends will get displayed whether or not they were performed by the account address. \
In addition, the original post cannot be retrieved by this endpoint.&#x20;
{% endhint %}

