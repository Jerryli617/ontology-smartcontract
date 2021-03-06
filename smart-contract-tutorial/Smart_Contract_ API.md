## Smart Contract API Document

Query the data by blockchain API:

| API                                      | Return Value         | Description               |
| ---------------------------------------- | ----------- | ---------------- |
| Blockchain.GetHeight()                   | uint        | Get the current block height         |
| Blockchain.GetHeader(uint height)        | Header      | Get block header by block height     |
| Blockchain.GetBlock(byte[] hash)         | Block       | Get block by block hash   |
| Blockchain.GetTransaction(byte[] txid)   | Transaction | Get transaction by transaction ID      |
| Blockchain.GetContract(byte[] script_hash) | Contract    | Get contract content by contract hash     |
| Blockchain.GetTransactionHeight(byte[] txid) | uint64      | Get transaction height by transaction ID |

Block API：

| API                             | Return Value           | Description                         |
| ------------------------------- | ------------- | -------------------------- |
| Header.Hash                     | byte[]        | Get the hash of a block                    |
| Header.Version                  | uint          | Get block version number                    |
| Header.PrevHash                 | byte[]        | Get the hash of the previous block               |
| Header.Index                    | uint          | Get the height of a block                   |
| Header.MerkleRoot               | byte[]        | Get the root of the Merkle Tree for all transactions in a block |
| Header.Timestamp                | uint          | Get block timestamp                   |
| Header.ConsensusData            | ulong         | Get consensus data of a block (Pseudo-random number generated by consensus nodes)    |
| Header.NextConsensus            | byte[]        | Get the hash of the next bookkeeping contract           |

| API                             | Return Value           | Description                         |
| ------------------------------- | ------------- | -------------------------- |
| Block.GetTransactionCount()     | int           | Get the number of transactions in the current block              |
| Block.GetTransactions()         | Transaction[] | Get all transactions in the current block              |
| Block.GetTransaction(int index) | Transaction   | Get the specified transaction in the current block               |

Transaction API：

| API                       | Return Value                    | Description           |
| ------------------------- | ---------------------- | ------------ |
| Transaction.Hash          | byte[]                 | Get the hash of the current transaction |
| Transaction.Type          | byte                   | Get the type of the current transaction     |
| Transaction.GetAttributes | TransactionAttribute[] | Query all attributes of the current transaction  |



Contract API：

| API                                      | Return Value            | Description          |
| ---------------------------------------- | -------------- | ----------- |
| Contract.Script                          | byte[]         | Get the script of a contract    |
| Contract.Create(byte[] script, bool need_storage, string name, string version, string author, string email, string desc) | Contract       | Create a smart contract      |
| Contract.Migrate(byte[] script, bool need_storage, string name, string version, string author, string email, string desc) | Contract       | Migrate / Update a smart contract |
| Contract.Destroy()                       | void           | Deatroy a smart contract        |
| Contract.StorageContext                  | StorageContext | Get the contract's storage context  |

Storage API：

| API                                      | Return Value            | Description                               |
| ---------------------------------------- | -------------- | -------------------------------- |
| Storage.CurrentContext                   | StorageContext | Get the current storage context                       |
| Storage.Get(StorageContext,string)       | byte[]         | Query operation, query the corresponding value by key in the persistent storage area   |
| Storage.Get(StorageContext,byte[])       | byte[]         | Query operation, query the corresponding value by key in the persistent storage area   |
| Storage.Put(StorageContext, string,string) | void       |Insert operation, inserting data as key-value format into a persistent storage area |
| Storage.Put(StorageContext, byte[],byte[]) | void       | Insert operation, inserting data as key-value format into a persistent storage area |
| Storage.Put(StorageContext, byte[],string) | void       | Insert operation, inserting data as key-value format into a persistent storage area |
| Storage.Put(StorageContext, string,byte[]) | void       | Insert operation, inserting data as key-value format into a persistent storage area |
| Storage.Put(StorageContext, string,BigInteger) | void       | Insert operation, inserting data as key-value format into a persistent storage area |
| Storage.Put(StorageContext, byte[],BigInteger) | void       | Insert operation, inserting data as key-value format into a persistent storage area |
| Storage.Delete(StorageContext, byte[])   | void           | Delete operation, delete the corresponding value by key in the persistent storage area  |
| Storage.Delete(StorageContext, string)   | void           | Delete operation, delete the corresponding value by key in the persistent storage area  |

Runtime API：

| API                          | Return Value  | Description                                       |
| ---------------------------- | ---- | ---------------------------------------- |
| Runtime.Time                 | uint | Get current block time                                |
| Runtime.CheckWitness(byte[]) | bool | Verify operational permissions of people or contract                   |
| Runtime.Notify(object[])     | void | In smart contract, sending notifications (including socket notifications or rpc queries) to clients that are executing this smart contract |
| Runtime.Log(string)          | void | In smart contract, sending logs ( including socket notifications) to clients that are executing this smart contract       |
 

System API：

| API                        | Return Value              | Description                         |
| -------------------------- | ---------------- | -------------------------- |
| ExecutionEngine.ScriptContainer     | IScriptContainer | Get script container of a smart contract              |
| ExecutionEngine.ExecutingScriptHash | byte[]           | Get the script hash that a smart contract executes          |
| ExecutionEngine.CallingScriptHash   | byte[]           | Get the script hash of the invoker of a smart contract         |
| ExecutionEngine.EntryScriptHash     | byte[]           | Get the script hash of the entry point (start of the contract invocation chain) of a smart contract |


System API：

| API                                      | Return Value    | Description                                       |
| ---------------------------------------- | ------ | ---------------------------------------- |
| Native.Invoke(byte version, byte[] address, byte[] method, object args) | byte[] | Invokes a native contract. 1. version - version number， 2. address - contract address 3. method - contract method 4. contract parameters |






