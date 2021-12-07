# 🌐 Accounts

`Accounts` are objects containing attributes referencing a blockchain account.&#x20;

They can be imported from an existing blockchain account or newly created but **they are needed** in order to write to the Aleph network, in particular, **to sign messages** when creating or updating a resource.

The API allows you to create or connect an account, sign messages and get message signatures.

| ENDPOINTS                                                |                                                                                   |
| -------------------------------------------------------- | --------------------------------------------------------------------------------- |
| [Generate & Connect a new chain account](new-account.md) | [.NewAccount()](new-account.md)                                                   |
| [Connect an existing chain account](import-account.md)   | [.ImportAccountFromMnemonic(), .ImportAccountFromPrivateKey()](import-account.md) |

