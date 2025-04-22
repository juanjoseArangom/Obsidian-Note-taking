# Database Transactions: ACID Properties and Locking Mechanisms

## ACID Properties
Database transactions are sequences of operations performed as a single logical unit of work. To ensure data integrity and reliability, transactions must exhibit the following *ACID* properties:

### 1. Atomicity
Atomicity ensures that all operations within a transaction are completed successfully. If any part of the transaction fails, the entire transaction is rolled back, leaving the database unchanged.

### 2. Consistency
Consistency guarantees that a transaction brings the database from one valid state to another, maintaining the defined rules, constraints, and relationships.

### 3. Isolation
Isolation ensures that the execution of concurrent transactions results in a system state that would be obtained if the transactions were executed sequentially. It prevents transactions from interfering with each other.

### 4. Durability
Durability means that once a transaction has been committed, its changes are permanent, even in the event of a system failure.

## Lock Matrix in Databases
To enforce isolation and manage concurrent access, databases use locking mechanisms. The *lock matrix* defines the compatibility between different types of locks:

|     | S (Shared) | X (Exclusive) |
| --- | ---------- | ------------- |
| *S* | Yes        | No            |
| *X* | No         | No            |

- *S (Shared) Lock*: Allows multiple transactions to read a resource simultaneously but prevents any from writing to it.
- *X (Exclusive) Lock*: Allows a transaction to both read and write to a resource but blocks all other transactions from accessing it.

## Commit and Rollback
- *Commit*: Finalizes a transaction, making all its changes permanent in the database.
- *Rollback*: Undoes all operations of a transaction, restoring the database to its previous consistent state.

These mechanisms together ensure data integrity and concurrency control in database systems.

## Arquitectura
## Ventajas de un SGBD
## Desventajas
