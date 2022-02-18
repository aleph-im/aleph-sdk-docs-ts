# 🗑 Forget

`Forget` objects are `Messages` that allow Aleph.im network users to remove content from a Post message across the network.

Multiple messages can be referenced in the same forget message for their content to be removed.&#x20;

Forgetting a Message does:

* empty the message content field
* empty the item\_content field
* add a forgotten\_by field referencing the forget message item hash which initiated the removal.

If the message to be "forgotten" was referencing a `Store` file, the file from the store message will be deleted from the database or unpinned by the node once there are no messages left referencing the file.

The API allows you to create a forget message:

| Create a forget message | .publish() |
| ----------------------- | ---------- |
