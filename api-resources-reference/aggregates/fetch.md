# List all keys & values

### Returns

An object of keys and corresponding content found for the address Aggregate Message.&#x20;

If no aggregate is found, a 404 error "no aggregate found" will be returned.

{% hint style="info" %}
Up to 1,000 results will be returned.
{% endhint %}



### Usage & Example

```javascript
import { aggregate } from 'aleph-sdk-ts'

(async() => {
  await aggregate.Get({
    address: account.address,
  })
})();

// Returns all the keys found for this address
{
  test_key: { key_1: 'value_1'},
  test_key_2: { key_name: 'value for key'},
  ... 
}
```



### Required parameters

|                                                          | Description                                        |
| -------------------------------------------------------- | -------------------------------------------------- |
| <mark style="color:green;">**address**</mark> - _string_ | Address for which the aggregate should be returned |



### Optional parameters

*   <mark style="color:green;">**keys**</mark> - _array of strings_\
    `DEFAULT: []`\
    If none are passed, all keys and their content found for the address will be returned.

    If some are passed, only the key value pairs with those keys will be returned for the address.\

* <mark style="color:green;">**APIServer**</mark> - _string_\
  `DEFAULT: https://api2.aleph.im`\
