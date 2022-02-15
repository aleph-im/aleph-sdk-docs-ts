---
description: >-
  Get up and running with our Aleph Typescript SDK and start developing your
  Aleph integration.
---

# Getting Setup

{% hint style="success" %}
Integrating with Aleph requires two steps:

1. Install the client library in your application so that you can interact with the Aleph API
2. Make an API request
{% endhint %}

### 1. Import aleph-sdk-ts in your dApp

We provide an official typescript library. Open your terminal window and navigate into your project's root folder and install the library:

```
$ yarn add aleph-sdk-ts
```

### 2. Make an API request

To check the integration is working, make a basic API request within your project.&#x20;

Here we are retrieving all Posts that were made with a post type of "chat" and with a reference of "hall". We'll go into more details about post types and references in the [Post Resource Reference](../api-resources-reference/posts/).

{% code title="index.js" %}
```javascript
import { post } from 'aleph-sdk-ts'

(async() => {
  await post.Get({
    types: 'chat', 
    pagination: 200,
    page: 1,
    refs: ['hall'], 
    addresses: [],
    tags: [],
    hashes: [],
    APIServer: "https://api2.aleph.im"
  })
})()
```
{% endcode %}

Aleph returns an object with a `posts` key containing an array of all the posts that were made with the query params we requested.

The response should look like this:&#x20;

```javascript
{
  pagination_item: "posts",
  pagination_page: 1,
  pagination_per_page: 200,
  pagination_total: 457,
  posts: [
    {
      address: "0xa00C60b5Ea6c6d0C277680fE66b5c864fBF66945"
      chain: "ETH"
      channel: "TEST"
      confirmed: false
      content: {body: 'Trying to learn Aleph im\nand blockchain\n'}
      hash: "e909fe197355327ac529211e25d1cb254922851eac1bbce7c0e7d7d24b056e5b"
      item_content: "{\"type\":\"chat\",\"address\":\"0xa00C60b5Ea6c6d0C277680fE66b5c864fBF66945\",\"content\":{\"body\":\"Trying to learn Aleph im\\nand blockchain\\n\"},\"time\":1635864095.033,\"ref\":\"hall\"}"
      item_hash: "e909fe197355327ac529211e25d1cb254922851eac1bbce7c0e7d7d24b056e5b"
      item_type: "inline"
      original_item_hash: "e909fe197355327ac529211e25d1cb254922851eac1bbce7c0e7d7d24b056e5b"
      original_ref: "hall"
      original_signature: "0x3ca1de98e513e5ee668c0065f50a5190ce01d6b957f97dbd5aa997d6d6e65be344c560f41a02397873ac34aaf3ae5d2ae9f4ec5f8af8fd7304685ef3fc37e5cd1b"
      original_type: "chat"
      ref: "hall"
      sender: "0xa00C60b5Ea6c6d0C277680fE66b5c864fBF66945"
      signature: "0x3ca1de98e513e5ee668c0065f50a5190ce01d6b957f97dbd5aa997d6d6e65be344c560f41a02397873ac34aaf3ae5d2ae9f4ec5f8af8fd7304685ef3fc37e5cd1b"
      size: 169
      time: 1635864095.033
      type: "chat"
      _id: {$oid: '61814e3416d179f0c1741e7a'}
    },
    
    { ... },
    
    ... 199 more items
    
    ]
  }
```

### 3. Next Steps - Writing to the Network

Once you have successfully made an API _GET_ request, **connect a blockchain account and write to the aleph.im network (**[**Posting to the Network**](posting-to-the-network.md)**).**
