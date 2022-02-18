---
description: Register a program to run on Aleph.im virtual machines.
---

# Create a Program

### Returns

A Program message object that is being sent to the network.

### Usage & Example

```typescript
import { program } from 'aleph-sdk-ts'
import { ItemType } from "aleph-sdk-ts/messages/message"

(async() => {
  const file = new File(<Your Program Here>);
      
  program.publish({
    account: ,
    channel: ,
    storageEngine: ItemType.storage, 
    inlineRequested: false,
    APIServer: "https://api2.aleph.im",
    file: file,
    entrypoint: "main:app"
  })
})
```

### Required Parameters

| <mark style="color:green;">**account**</mark> - _Account_         | Account to use for signing.                                                                                                                                                                                                                                                                                           |
| ----------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:green;">**channel**</mark> - _string_          | Channel of the message. Ideally, an application would decide and use one channel.                                                                                                                                                                                                                                     |
| <mark style="color:green;">**storageEngine**</mark> - _ItemType_  | The storage engine to use when storing the object (IPFS or ALeph)                                                                                                                                                                                                                                                     |
| <mark style="color:green;">**inlineRequested**</mark> - _boolean_ | Will the message be inlined ?                                                                                                                                                                                                                                                                                         |
| <mark style="color:green;">**APIServer**</mark> - _string_        | The API server endpoint used to carry the request to the Aleph's network.                                                                                                                                                                                                                                             |
| <mark style="color:green;">**file**</mark> - _Buffer_ _or_ _Blob_ | File with the program to run on a VM                                                                                                                                                                                                                                                                                  |
| <mark style="color:green;">**entrypoint**</mark> - _string_       | <p>The entrypoint is composed of two values:</p><p>• The name of the main file that is running the program</p><p>• The name of the object in the program that inits FastApi<br><br>Ex: "mainFile:FastApiObject". Learn more about FastApi <a href="https://fastapi.tiangolo.com/tutorial/first-steps/">here</a>. </p> |

### Optional Parameters

* <mark style="color:green;">**subscription**</mark> - _Record\<string, unknown>\[]_\
  _`DEFAULT: { http: true }`_\
  _``_Signals that trigger an execution of the VM, by default it's triggered by HTTP, but it can be by an Aleph Message.\
  Ex: _Record_<"message", \[{"sender: "0x...", "channel": "TEST"}]>\

* <mark style="color:green;">**memory**</mark> - _number_\
  _`DEFAULT: 128`_\
  _``_The memory you give to your VM, this param is contained in the MachineResources struct.\

* <mark style="color:green;">**runtime**</mark> - _string_\
  _`DEFAULT: "bd79839bf96e595a06da5ac0b6ba51dea6f7e2591bb913deccded04d831d29f4"`_ \
  _``_This param refers to the `root filesystem` used by the Aleph VM\
  and this param is a path to them, you can find the official Aleph runtimes [here](https://github.com/aleph-im/aleph-vm/tree/main/runtimes)\

* <mark style="color:green;">**volumes**</mark> - _array of MachineVolume_\
  _`DEFAULT: []`_\
  _``_MachineVolume can either be: ImmutableVolume | EphemeralVolume | PersistentVolume.\
  Explanation of those types are here: [https://github.com/aleph-im/aleph-vm/blob/main/tutorials/ADVANCED.md#volumes](https://github.com/aleph-im/aleph-vm/blob/main/tutorials/ADVANCED.md#volumes)\
  You can also find their definition here: [https://github.com/aleph-im/aleph-sdk-ts/blob/main/src/messages/program/programModel.ts](https://github.com/aleph-im/aleph-sdk-ts/blob/main/src/messages/program/programModel.ts)
