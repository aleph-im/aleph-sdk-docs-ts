# Retrieve a file

Files can be retrieved **using the item\_hash** returned after creating the file in the api server **or** with a **request to the following endpoint**:



### Usage

```javascript
import { store } from 'aleph-sdk-ts'

(async() => {
    await store.Get({
        fileHash: file_hash
        APIServer: "https://api2.aleph.im"
    })
})()
```



### Required parameters

| Parameter                                                  | Description                                                                            |
| ---------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| <mark style="color:green;">**fileHash**</mark> - _string_  | `content.item_hash` generated from  creating the file on the api server                |
| <mark style="color:green;">**APIServer**</mark> - _string_ | API server accepting files. Examples: "https://api1.aleph.im", "https://api2.aleph.im" |



### Example: Retrieve from endpoint

{% code title="REQUEST" %}
```javascript
import { store } from 'aleph-sdk-ts'

(async() => {
    var my_buffer = await store.Get({
        fileHash: 'QmQkv43jguT5HLC8TPbYJi2iEmr4MgLgu4nmBoR4zjYb3L',
        APIServer: 'https://api2.aleph.im'
      })
})()
```
{% endcode %}

{% code title="RESPONSE" %}
```javascript
// Buffer can be converted back to a string like so:
new TextDecoder().decode(response)
// => 'This is just a test.'
```
{% endcode %}

###

### Example: Retrieve from an API server

If stored on aleph storage:

```javascript
// https://<FILE API_SERVER>/api/v0/storage/raw/<FILE ITEM HASH HERE>

https://api2.aleph.im/api/v0/storage/raw/QmQkv43jguT5HLC8TPbYJi2iEmr4MgLgu4nmBoR4zjYb3L
```

If stored on ipfs compatible server, the file is also available on:&#x20;

```javascript
// https://ipfs.io/ipfs/<FILE ITEM HASH HERE>

https://ipfs.io/ipfs/QmQkv43jguT5HLC8TPbYJi2iEmr4MgLgu4nmBoR4zjYb3L
```

