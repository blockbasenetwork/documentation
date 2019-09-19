# BlockBase White Paper
If you just want to skim it here's the [short tl;dr version](https://github.com/blockbasenetwork/documentation/blob/master/WhitePaper-tldr.md)
## Abstract
Information security is paramount. It is never total, and is always subject to a tension between the need to protect it and the need to use/share it. Secure storage of data is provided through encryption, however, data is usually maintained in an unencrypted format to allow for its processing and analysis, and its access and use governed through established policies that dictate the rules for setting up a secure environment. But this relies on a human implementation of these policies and that’s where many security flaws are found. These security flaws may be exploited for information theft, for its destruction or disguised alteration, or denial of access to it. Systems that ensure, by design, the security of the information they store, and which comply with the CIA triad ("Confidentiality", "Integrity", and "Availability"), were non-existent until the creation of Bitcoin in 2008. Satoshi Nakamoto was responsible for designing a system that displayed security qualities never seen before, through the use of an innovative mixing of some well-known computer science concepts. The advent of Bitcoin led to the birth of a whole new area of research in blockchain systems, within which this project was born. Here we present BlockBase, a distributed system that applies many of blockchain related paradigms to provide secure and distributed database storage services. Traditional blockchain systems aren’t easily scalable by design and as such storing all database related operations on it is impracticable. For these reasons, a new blockchain architecture is proposed here, that relies on smart contracts for the management and operation of sidechains to a main blockchain, which in turn will serve to store those database and data operations. Each sidechain exists for the sole purpose of storing data related database operations. It stores all database management operations, such as database creation, table creation, update and deletion, column creation, update and deletion, and all data management operations, such as data insertion, update and deletion. Each sidechain is born from the agreement on a sidechain service request that specifies its servicing and financial accounting rules, which must be agreed upon by the service requester and service providers through staking of BlockBase tokens that will be lost if the rules aren’t met. All database related data is encrypted and decrypted by the service requester, without revealing any information to the service providers. The proposed implementation uses the Advanced Encryption Standard (AES) extensively for data encryption and key generation. A hierarchical key generation method is proposed, that enables the sharing of access to subsets of the database, without giving access to all of its data. BlockBase requires a main blockchain that has smart contracts capabilities and that has a high throughput of blocks. After careful analysis, we chose to use the EOS blockchain for this project. BlockBase is currently in pre alpha phase.

## Introduction
Information security is paramount. It is never total, and is always subject to a tension between the need to protect it and the need to use/share it. In today's organizations, this tension is especially exacerbated. We live in an extremely interconnected society, where valuable information is shared between diverse organizations, ranging from governments to businesses.

Much of information security focuses on secure data storage and its transmission. This is essentially provided through encryption. However, encrypted data is, by its nature, unusable for any activity related to its processing or analysis. Encrypted data eliminates the possibility of being used for those activities. This is a problem for any organization that wants to benefit from the data it holds from third parties. Third party data security is in direct conflict to their interests. Furthermore, information security is cumbersome and many fail to implement it adequately.

Data is usually maintained in an unencrypted format, and its access and use is governed through established policies that dictate the rules for setting up a secure environment. Conceptually, these policies follow the CIA triad ("Confidentiality", "Integrity", and "Availability"), where confidentiality determines the rules of access to information; integrity determines how validity and authenticity of the information is assured; and availability determines how information is made accessible.

However, it’s in the human implementation of these policies that many security flaws are found, where human aspects such as ignorance, neglect, apathy, disinterest, and deceit are at the root of the problem. It’s the human element that is mostly responsible for security flaws resulting in hacking attacks. These may be aimed at information theft, its destruction or disguised alteration, or denial of access to it. The situation has gotten so serious that, according to Privacy Rights Clearinghouse, more than 10 billion records have been breached since 2005. It is important to note that this information refers to only cases that have been made public. It remains to know all the other cases that were never reported.

We believe that in order to address this problem, the goal should be to minimize the human responsibility in ensuring the security of the system, by delegating it to the system itself. Systems that ensure, by design, the security of the information they store, and which comply with the CIA triad, were non-existent until the creation of Bitcoin in 2008. Satoshi Nakamoto was responsible for designing a system that displayed security qualities never seen before, through the use of an innovative mixing of some well-known computer science concepts. In fact, Bitcoin exists for more than 10 years, keeps billions of dollars in Bitcoin, and has never been hacked.

The advent of Bitcoin led to the birth of a whole new area of research in blockchain systems, within which this project was born, a system for safe and distributed storage of relational databases. BlockBase itself isn’t relational like a typical database, but the operations that it stores are related to operations performed on relational databases. What this means is that, generally, what is stored on BlockBase are typical database operations, such as creating databases, defining the tables that make up those databases, defining the columns of each one of those tables, and finally the addition, updating, and removal of records from those tables.

## Security Features
BlockBase is a distributed system that applies many of blockchain related paradigms to provide secure and distributed database storage services. Specifically, it’s a system that promotes, by default, the CIA triad of computer security. In these terms, the system has the following fundamental security features:

### Confidentiality
* The system promotes the confidentiality of data. All data registered in the system is, by default, pre-encrypted.
* The system provides different levels of access to data, starting from the individual record level at the bottom, to the whole database level at the top, through the use of multiple cryptographic layers on stored data.
* The system does not encrypt or decrypt the data that it stores. Any data insertion contains previously encrypted data, and any data search returns the data as it was inserted. It is the responsibility of the owner of the data to have the necessary cryptographic elements to encrypt and decrypt the data.
* Encrypted data is searchable, without disclosing any relevant information about what it contains.

### Integrity
* The system maintains a historical record of all changes made to the data structure and the data itself that is impossible to be altered or deleted.
* All changes made to the data structure and the data itself are digitally signed assuring their authenticity and non-repudiation.

### Availability
* The system is resilient to hardware and software faults, and electricity and internet shortages; to natural disasters such as earthquakes and floods; to human error or deceit; to DDos attacks.
* The system is horizontally scalable and allows for an unlimited number of users without compromising its availability.

## Main Blockchain Structure
Traditional blockchain systems aren’t easily scalable by design. Trying to store all database and data management operations inside a traditional blockchain leads to an immediate problem of scalability: its throughput is limited by the blockchain block size and block time, and is also limited by transaction costs. Storing the information of just one large database inside a traditional blockchain would prove impossible on blockchains with a similar paradigm to the Bitcoin blockchain. Costs, memory space and execution times, make such blockchains completely inappropriate for this purpose.

For these reasons, a new blockchain architecture is proposed here, that relies on smart contracts for the management and operation of sidechains to a main blockchain, which will serve to store those database and data operations. In the scope of this work, a sidechain consists of a normal blockchain structure, that “runs parallel to” the main blockchain. It’s a chain of blocks that is spawned from the main blockchain, but that exists outside of the main chain. A sidechain isn’t a fork. A fork consists of two or more possible paths running up the chain of blocks on a blockchain. Sidechains are a completely different thing. They don’t necessarily have the same structure as the main chain, or store the same data, or have an equal consensus method to the main chain. In fact, a sidechain may be completely different from the main chain. The only thing that makes them sidechains and not blockchains is that they are in some way connected to the main blockchain.

The concept of sidechains presents an interesting approach to scaling a blockchain because instead of storing all data on the main blockchain, it may be distributed through many sidechains. Also, the set of nodes that store the main blockchain may not be the same set of nodes that store the sidechains - in the case that they were, the scalability problem would remain but with more management overhead. But if a subset of nodes, or an altogether different set of nodes stores each sidechain, the situation becomes more interesting. In this case each sidechain may be stored by a completely different group of nodes. With this type of approach, the system becomes more scalable. However, it may become less secure per sidechain. Nonetheless, it presents more configuration choices for the scalability and security of individual sidechains, instead of an “all-or-nothing” approach with a single main chain.

Here, each sidechain exists for the sole purpose of storing data related databases. It stores all database management operations, such as database creation, update and deletion, table creation, update and deletion, column creation, update and deletion, and all data management operations, such as data insertion, update and deletion. Since a sidechain stores all these operations, executing all stored operations in order, from the sidechain’s genesis block to the latest block, on a traditional database server, would lead to reaching the current up-to-date state of the databases.

The most effective way to “connect” a sidechain to a main chain is through the use of smart contracts. The exact way they work is detailed further ahead in this document. But this implies that the main chain must support smart contracts.

## Sidechain-as-a-Service Economic Model
Since sidechains exist for the purpose of storing database related information, they can be serviced to parties interested in acquiring it, by parties interested in servicing it, provided there is an economic model that benefits both service buyers and service sellers. Thus, each sidechain is born from the agreement on a sidechain service request that specifies its servicing and financial accounting rules, such as: the service level requirements, the financial commitment of the service requester and service provider, the financial incentives for participating as a service provider, and the financial penalties of not complying with the requirements. Service level requirements define various rules such as the minimum number of participants and average blocktime, the financial commitment defines the stakes provided by the service requester and service provider,  the financial incentives define the reward per block production, and the financial penalties define the losses in case the requirements aren’t met. 

As described above, both service requester and service providers must stake tokens in order to participate. The service requester stakes tokens in the service request, which ensures its distribution to the service providers according to block production, and service providers must stake tokens to participate in the service provision, which they will lose if service requirements aren’t met. In such a model, there is no emission of tokens per block produced. Instead, each block produced is paid with a fixed amount of tokens that are taken from the stake of the service requester. Therefore, the service requester and the service provider must acquire tokens in order to participate. These tokens are of finite supply, and are traded on the open market, as any other cryptocurrency or digital asset.

## EOS for the Main Blockchain
This system requires a main blockchain that has smart contracts capabilities and that has a high throughput of blocks. After careful analysis, we chose to use the EOS blockchain for this project. Nonetheless, its smart contract technology may be ported to other blockchains that support smart contracts with equivalent capabilities. This system requires two smart contracts, one for managing the sidechains, which we will call here the *operations contract*, and one for managing the sidechains financial accounting, which we will call here the *accounting contract*. For more information on EOS, please check [EOSIO](https://eos.io/).

## BlockBase Token
BlockBase will use its own token, the BlockBase Token. This is the token that will be used by the *accounting contract*, such as adding stakes and receiving payments for the services provided to sidechain owners.

## Smart Contracts
The *operations contract* is a pivotal piece for the consensus, it is the link between the EOS main chain and every BlockBase sidechain. Each producer running the BlockBase client will regularly communicate with the main chain through this contract, and it is also the means to discover requests for service providers from different sidechains.

### Operations Contract Role in the Consensus
The operations contract is responsible for keeping track of the latest block headers that have been accepted as valid by the network. Every time a new block is produced, the other producers in the chain will need to validate it for it to be accepted as valid and to become irreversible in the contract. Since the contract keeps a record of the latest block headers in a chain, a new producer joining the network can easily synchronize and validate every previous block.

Producers who fail to produce blocks during their turn to produce will get flagged in the contract, and added to the blacklist of the sidechain they were producing. If a producer is expelled from the sidechain network, he won’t be able to get its stake back.

### Accounting Contract Role in the Consensus
The accounting contract is based on the EOS token contract, retaining all of its functions, as well as security measures. This means that users can expect the token to have the same behavior as the EOS token.

The main reason to have a separate contract for accounting is because we predict that the accounting contract will need a lot less maintenance work (ideally none) than the operations contract. The big advantage of this approach is allowing us to change the accounting contract owner permission to a more secure solution, as will be explained later.

### Sidechain Account and Permissions
Each sidechain will be associated to a unique EOS account, it's not possible to have more than one sidechain linked to a single account. The name of this account is used to identify the sidechain, so it will be recommended that sidechain requesters create a new account for the sole purpose of staking the tokens and creating a new sidechain.

In order to run the sidechain, the account associated with it will need to add the eosio.code permission to the contract. It is recommended that the account only acts as a host for the sidechain, and never holds any tokens other than the ones staked to run the sidechain.

Verifying blocks in the sidechain will use a multiple signature permission created as a child of the active permission of the account associated with the sidechain, and the smart contract will be responsible of managing this permission. Since the producers that are currently active in the sidechain can change at any time, the keys and threshold needed will be dynamically calculated inside the smart contract. The threshold needed to execute the action will be half the number of producers plus one.

<p align="center"><img src="https://github.com/blockbasenetwork/documentation/blob/master/images/hier.png"></p>

### Requesting a Sidechain Service
Requesting a new sidechain requires a requester to allocate stake, which will be the source of tokens used to pay the providers working on the sidechain. The requester will be responsible for making sure the stake is enough to pay every producer until the next settlement phase (explained further ahead). If the stake isn’t enough, the sidechain requester will risk losing everything stored in the sidechain as the block producers will stop producing and leave the network.

When configuring a sidechain, the requester will be able to configure the desired time between blocks, the block size, the payment per block, the minimum stake from service providers, and the number of blocks that should be produced between each settlement phase. This information allows potential providers to decide if they want to place a stake in the sidechain to become a candidate to produce blocks.

A higher number of producers working on the sidechain will result in the data being more secure with a lower chance of being lost in the case of some of the producers deciding to leave the sidechain, but with more producers it also means that they will expect a higher pay per block produced, so the requester will naturally have to choose how they want to use their funds.

## Sidechains Lifecycle Management
All sidechains are managed through the use of the two smart contracts. It requires various phases, each with specific steps as follows:
* Sidechain Request Phase:
  * A sidechain requester registers a unique sidechain name on the accounting contract.
  * The sidechain requester stakes a fixed amount of tokens on the accounting contract associated with the sidechain name he registered.
  * The sidechain requester configures the sidechain request and posts it on the operations contract.
* Application Phase:
  * A service provider that wants to participate in servicing the sidechain stakes at least the minimum amount of tokens required by the sidechain request, on the accounting contract.
  * The service provider posts on the operations contract a sidechain participation request containing the unique sidechain name, a hashed secret, a public key, and the duration he wants to participate in servicing the sidechain.
* Secret Reveal Phase: Every applicant reveals its secret by posting it on the smart contract. Applicants that don’t post their secret or post a wrong secret are excluded from the applicant list.
* Applicants Selection Phase:
  * If the number of applicants is lower than the number of required service providers, the process ends. If the number of applicants are equal to the number of required service providers, all are chosen. If the number of applicants is higher than the number of service providers required, a selection contest begins.
  * Applicants are ordered by stake ascendingly. The two applicants with lowest stake enter a competition. Their secrets are concatenated and then hashed. If the most significant bit of the resulting hash is 0, then the first applicant is chosen, otherwise the second is chosen. This results in a new list of applicants, also ordered by stake, where one of the two applicants with lowest stake was excluded. If the number of applicants is still higher than the required number of service providers, the process is repeated. This process favors the applicants that provide the highest stake.
* Connection Phase:
  * Having selected the service providers, they remain ordered by stake. Each service provider has then to establish a connection with a calculated number of service providers to their right. If they reach the end of the list, they continue from the beginning. In order to establish a connection without publicly revealing their IPs on the smart contract, each service provider encrypts its IP with a AES secret key derived from their private key and the public key of the provider they want to reveal it to. It is then published on the operations contract, associated to the public key of the receiving service provider. The receiving service provider, may decrypt the IP by deriving the AES secret key from its private key and the public key of the sender. Thus, each service provider has to encrypt its IP as many times as the number of adjacent service providers it needs to connect to, and publish the encrypted result on the operations contract. Furthermore, each service provider has to retrieve all encrypted IPs attributed to him, and decrypt them locally, thus obtaining the list of service providers that need to connect to him.

In order to maintain consensus, the following steps must be taken:
* Every service provider is responsible for block production. Each service provider produces one block per turn. The order for block production is determined by the ordered list of selected service providers on the operations contract. Block production starts on the service provider with the least stake on the list. He produces a block and broadcasts it to its peers for block validation, execution, and storage. Block production is then passed to the next service provider on the list. When the last service provider has produced and broadcasted his block, the block production returns to the first service provider on the list.
* In order to get a block validated by its peers, a producer has to first create the block, then post its header on the operations contract, and then broadcast it to its peers. Each peer will validate the block, and compare it to the proposed block header on the operations contract. If everything is valid, the peers sign the approval transaction to be executed in the operations contract, thus stating their acceptance. After accepting the block, the producers execute locally the block transactions. Hence, every producer should execute locally all transactions of all approved blocks in correct order.
* A block is considered valid if the following checks are passed: (1) the header of the sent block should match the block header on the operations contract. (2) the account name of the block producer stated inside the block header should match the account name of the current block producer as stated by the operations contract. (3) the block hash should be correct. (4) the block signature should produce a valid result when tested against the public key of the current block producer, which is stored in the operations contract. (5) the merkle root should be correctly constructed. (6) the previous block hash should match the hash of the previous block. (7) all transactions should have a valid structure and have the signature of the service requester. (8) the hash of a specific database record selected through a function that receives the previous block hash as input should be correct.
* If a block header doesn’t receive the required minimum amount of signatures to be accepted, the block is discarded and the block production is passed to the next producer in line. Similarly, if a producer doesn’t produce a block during the time threshold for its turn, block production is passed to the next producer in line. In both cases, the failure on producing a correct block is counted on the operations contract, where any producer that fails more than the defined maximum of times, will be penalized by being expelled from the producers list and also by losing its stake.
* After a predefined amount of rounds of block production, block production is halted and the settlement phase is started. The settlement phase is the moment where all operations since the previous settlement are accounted for. Producers are paid according to block production, by transferring tokens staked by the service requester to the block producers. Producers that failed too many times to produce blocks at their turns are expelled from the production list and their stakes are taken from them. Also, during settlement, producers may leave the production pool if their announced production time is up. Also, further block production may be halted, if the remaining staked coins of the service requester are not enough to pay for block production until the next scheduled settlement.
* For every producer that leaves the pool during a settlement, its place may be filled by another producer. The first producers chosen are the applicants that applied for production but weren’t chosen. If those aren’t enough, a new application phase is started for receiving new producers. Block production isn’t halted during this new application phase, unless the number of remaining producers is lower than a specified limit.

## Staking
In addition to the regular records of the EOS token contract, the BlockBase accounting contract will also keep a record of all of the tokens that are being staked in each Sidechain, and will provide actions that allow producers and sidechain owners to add and recover stake from a sidechain. Recovering stake from a sidechain is only possible if it is not in active block production, for example, the sidechain could have ended its intended duration, or the number of producer candidates is lower than the number requested by the sidechain owner. Being punished for bad behavior in any sidechain also means that the stakeholders will lose some or even all of their staked tokens.

## Receiving Payments
After each settlement phase in the consensus, a part of the stake of the sidechain owner is reserved to each block producer. The number of tokens each producer gets is based on the number of blocks produced between phases. To receive the tokens on their accounts, producers will need to call an action in the accounting contract.

This action will automatically check every sidechain where the producer is active and collect all of the rewards that they have earned since the last time they claimed the reward.

## Permissions
The lack of visible security in the accounting contract owner permissions is one of the leading concerns of alternative tokens in the EOS mainnet. Twelve of the leading fifteen tokens currently have a single key associated with the owner permission (According to data from bloks.io). This means it is theoretically possible that anyone with access to that key is able to update the code for the token smart contract at any moment in a way that could work in their favor. As such, we will implement multiple signature permissions that will help improve the trust in the BlockBase token.

After the creation of the token, the owner permission of contract account will be associated to multiple keys owned by different members of the BlockBase team. This is done only because we predict the possibility of security fixes being necessary and urgent in the following months after the token launch. The owner permission will remain unchanged while the contract becomes more stable.

Once it’s deemed that the contract doesn't need any further changes, we will change the owner permission to the eosio.producers active permission. This is a special permission in EOS that will always require 15/21 producers to approve a transaction (as seen in eosio’s source code), effectively making the token associated with the same permissions as the main EOS token.

## Data Storage and Security
Encryption of sensitive information is very important. Unfortunately, this isn’t the practice on most traditional businesses. Information is usually kept in a non encrypted format, and instead barriers are mounted around the sensitive information, for the purpose of preventing unauthorized access to it. Intranets and user accounts with special privileges are a clear example of this. This usually results in a situation where a small group of people have all access and power over the stored information.

With BlockBase, the system is designed to allow any unknown third-party to participate as a sidechain producer and hence as a data keeper. In this scenario, anyone who wishes to benefit from the security qualities of integrity, availability, and accountability provided by BlockBase, is required to adopt the highest confidentiality standards. Information must be encrypted by default, because it will be available to strangers by default.

There are many strategies for data encryption when stored in a database. One could easily encrypt everything in such a way as to render completely useless any querying functionalities on the database. In such an extreme case, the database owner would have to fetch all the data from all the tables he needed, decrypt all records from each table, and only then proceed to finding the required data. Almost all of the retrieved records would have been unnecessarily fetched for satisfying the given query. This situation is very limitative and in most cases undesired. But in order to reduce the number of unnecessarily fetched records per query, one has to lower the encryption of the data, and consequently its security. This also applies to query variety. The more types of queries allowed, the less secure the data must be.

Hence, data querying is in direct conflict with data security. The goal is to achieve an adequate balance between data querying capabilities and data security. Less important table columns may be more exposed, thus providing better filtering capabilities through them. This subject has been studied extensively, with the development of various types of technical solutions, such as CryptDB, for example. However, the decision of choosing which columns to expose is left to the user of the technology.

Here we present our solution which follows some of the strategies of CryptBD. It will be implemented in the application used by the service requester, e.g. the database owner and the client of the service. This implementation isn’t in any way mandatory for BlockBase to work. Different variants from the client application may be implemented, that could provide different encryption strategies for the data. The service providers have no say on how the data is encrypted.

The proposed implementation uses the Advanced Encryption Standard (AES) extensively for data encryption and key generation, with the use of Cypher Block Chaining (CBC) method with random Initialization Vectors (IV) for data encryption, and with the use of Electronic CodeBook  (ECB) method exclusively for key generation. For every database there should be at least one AES master key, from which all subsequent keys may be derived. More than one AES master key may exist in more complex scenarios where different areas of the database must have different master keys.

The service requester must also possess a password or passphrase, this will be mandatory for key generation.

Since the master key will be used to derive all database keys, as a security precaution nothing else will be directly encrypted by it. In order to encrypt the name of the database, a key has to be generated for that purpose. This key is generated by hashing the result of encrypting the user password with the master key as such:

<p align="center">(1)</p>
<p align="center"><img src="https://github.com/blockbasenetwork/documentation/blob/master/images/eq1.svg"></p>

In order to encrypt the database name, the CBC method is used. The CBC method requires an Initialization Vector. Since we want to avoid having to store various Initialization Vectors, we use a master Initialization Vector that is derived from the password as such:

<p align="center">(2)</p>
<p align="center"><img src="https://github.com/blockbasenetwork/documentation/blob/master/images/eq2.svg"></p>

This *IV*<sub>*m*</sub> will be composed of the 128 least significant bits of the hash of the secret password of the user. With the database key *K*<sub>*db*</sub> and the *IV*<sub>*m*</sub> the database name is encrypted as such:

<p align="center">(3)</p>
<p align="center"><img src="https://github.com/blockbasenetwork/documentation/blob/master/images/eq3.svg"></p>

Hence, from the master key *K*<sub>*m*</sub> and the password the database name may be encrypted and decrypted. In order to encrypt the names of the tables a new key is generated. This key is generated from the database name and the master key as such:

<p align="center">(4)</p>
<p align="center"><img src="https://github.com/blockbasenetwork/documentation/blob/master/images/eq4.svg"></p>

With the tables’ key *K*<sub>*tb*</sub> all table names may be encrypted as such:

<p align="center">(5)</p>
<p align="center"><img src="https://github.com/blockbasenetwork/documentation/blob/master/images/eq5.svg"></p>

As such, all table names may be encrypted and decrypted with the tables’ key. In order to encrypt the columns of a table, a new key for that table is generated. This key is generated from the concatenation of the database name and table name, and encrypted with the master key as such:

<p align="center">(6)</p>
<p align="center"><img src="https://github.com/blockbasenetwork/documentation/blob/master/images/eq6.svg"></p>

With the columns’ key of an ith table, all column names may be encrypted as such:

<p align="center">(7)</p>
<p align="center"><img src="https://github.com/blockbasenetwork/documentation/blob/master/images/eq7.svg"></p>

Thus, we have a key to encrypt and decrypt the database name, a key to encrypt and decrypt all table names, and a key per table to encrypt and decrypt all columns for each table. In order to encrypt the values of a specific column, a new key is needed. It is generated from the concatenation of the table name and the column name, and encrypted with the master key as such:

<p align="center">(8)</p>
<p align="center"><img src="https://github.com/blockbasenetwork/documentation/blob/master/images/eq8.svg"></p>

In order to encrypt the values themselves, a random Initialization Value has to be generated for each record. This *IV* can be known to the service provider, and therefore it is also stored in the database. This means that for each database column, a *IV* column is also created. The only exceptions are primary key columns, foreign key columns, and unique key columns. Therefore, the value of a column of a record is encrypted as such:

<p align="center">(9)</p>
<p align="center"><img src="https://github.com/blockbasenetwork/documentation/blob/master/images/eq9.svg"></p>

Primary key columns and unique key columns don’t have repetitions, and since they have a unique encryption key, a *IV* column isn’t required, and instead the master *IV* is used on the encryption method presented above.

With this encryption strategy, many keys are required to encrypt and decrypt the database data. But all keys may be derived from the master key and from the password, which improves usability. Also, a mix of encrypted names and encryption keys may be shared, to facilitate query creation and data decryption, without fully giving access all database data and structure.

These proposed encryption methods enable a hierarchical encryption of the database. But with only these we are left without any way for retrieving specific records with filtering queries. Since the encryption methods presented above completely remove any structure from the unencrypted version of the data, there is no way for filtering or ordering the data.

Unfortunately, there is no known way for filtering or ordering encrypted data without revealing some information about the underlying data. In fact, the more precise the filtering and ordering of the data, the more information must be revealed about the data.

With this in mind, we propose an approach that relies on extra filtering and ordering columns that group records in buckets. These buckets may be made small enough to hold only one record, or large enough to hold all records. The larger the bucket the less information it reveals about the data, but also the less it aids in helping to filter or order the data.

Any table column may receive an extra adjacent column, to allow for filtering or ordering. For example, given a column that holds the encrypted data of the first name of users, we may add an extra adjacent column, that also holds an encrypted version of the first name of users, but that permits filtering or ordering. That column exists solely to enable filtering or ordering of records according to users’ first names. The data stored in this table uses a data bucketing strategy that we will explain ahead, which reveals information about the underlying data in inverse proportion to the bucket sizes. Similarly to the above, we should create a new key for this purpose. We use method (6) to encrypt the new column name, and method (7) to generate a key to encrypt the column data.

For each record that has such column, the number of the bucket is calculated with the corresponding value of the referenced column:

<p align="center">(10)</p>
<p align="center"><img src="https://github.com/blockbasenetwork/documentation/blob/master/images/eq10.svg"></p>

This method gives us a bucket number *n* between *0* and *N* that can be used in equality filtering queries. The larger *N* is, the less records will each bucket have, improving data recall, but also lessening data security to statistical analysis.

This type of bucketing strategy works when equality queries are used. In the case where range queries are required, the process is different. In this case, besides the bucket size, the upper and lower bounds of the domain values must be predetermined. As an example, if we wanted to store the day of the year and event took place, we would define the lower and upper bounds as 1 and 367.

<p align="center"><img src="https://github.com/blockbasenetwork/documentation/blob/master/images/bucket.png"></p>

Choosing a bucket size of 10, each bucket would have also a lower and upper bound, such that every value would fall inside the bounds of one of those buckets. Each bucket’s lower bound is inclusive and upper bound is exclusive. In order to calculate the bucket number first the bucket where the value falls is chosen, and its upper bound is used as input in the following method:

<p align="center">(11)</p>
<p align="center"><img src="https://github.com/blockbasenetwork/documentation/blob/master/images/eq11.svg"></p>

The resulting hash number is stored as the value for range queries. This approach doesn’t directly reveal order in the data. But with this method range queries won’t work either. Range queries must be transformed to equality queries, that use the hashed values of the upper bounds of all the buckets contained inside the range query. This way, the only thing that may reveal order is the inclusion of various buckets in one query. But this also doesn’t reveal order, only proximity.

## Conclusion
In this paper we proposed a blockchain system capable of storing user's data without compromising their privacy, using sidechains for horizontal scaling and a dynamic market to incentivize potential block producers to provide their services in return for token rewards. This solution is built on the [EOSIO](https://eos.io) platform and is planned to be launched in the EOS mainnet.

## Disclaimer
This white paper is provided as is, all the information presented represents the current plans of the BlockBase team and is subject to change at any moment, and shouldn’t be taken as a promise of implementation.









