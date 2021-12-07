# 📑 Posts

`Posts` are unique documents, posted in a certain channel and for a certain post type.&#x20;

Post objects allow you to store the content of a certain type associated with an address.

They can be searched through with:

* reference attribute `ref`.&#x20;
* tags assigned within the content object
* item or transaction hash
* addresses of the post or the sender

The reference attribute is useful for a few things:

* To reference another post (as a comment for example).
* To reference something else (an address, a transaction hash, a location ID, etc), and specify what the post is about.
* To reference another post to amend (edit) it. If you create a post with type `amend` and the `ref` of the original post: all new occurrences of the original post (granted you are authorized to do it) will be shown with new content, like an "amend and replace".

The API allows you to create, update (through create with set parameters), and retrieve a list of posts.

| ENDPOINTS                                              |                                |
| ------------------------------------------------------ | ------------------------------ |
| [create](create-a-post.md), [update](update-a-post.md) | [.Publish()](create-a-post.md) |
| [list all](list-all-posts.md)                          | [.Get()](list-all-posts.md)    |

