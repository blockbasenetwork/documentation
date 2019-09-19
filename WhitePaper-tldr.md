# BlockBase White Paper tl;dr Version
## Motivation
Information security is paramount. Here we present BlockBase, a distributed system that applies many of blockchain related paradigms to provide secure and distributed database storage services. Traditional blockchain systems aren’t easily scalable by design and as such storing all database related operations on it is impracticable. For these reasons, a new blockchain architecture is proposed here, that relies on smart contracts for the management and operation of sidechains to a main blockchain, which in turn will serve to store those database and data operations. Each sidechain exists for the sole purpose of storing database related operations. It stores all database management operations and all data management operations.
Each sidechain is born from the agreement on a sidechain service request that specifies its servicing and financial accounting rules, which must be agreed upon by the service requester and service providers through staking of BlockBase tokens that will be lost if the rules aren’t met. 
All database related data is encrypted and decrypted by the service requester, without revealing any information to the service providers. BlockBase uses the EOSIO blockchain as its main blockchain. BlockBase is currently in pre alpha phase.


<p align="center"><img src="https://github.com/blockbasenetwork/documentation/blob/master/images/img1.jpg"></p>

## Security Features
BlockBase is a distributed system that applies blockchain related paradigms to provide secure and distributed database storage services. It’s a system that promotes the CIA triad of computer security and has the following fundamental security features:

### Confidentiality
* All data registered in the system is, by default, pre-encrypted.
* All data is stored in an encrypted format.
* Encrypted data is searchable, without disclosing any relevant information about what it contains.

### Integrity
* The system uses a blockchain structure to assure a historical record of all data changes.
* All changes to the data are digitally signed assuring authenticity and non-repudiation.

### Availability
* The system is resilient to faults, shortages, attacks, human error or deceit.
* The system is horizontally scalable and allows for an unlimited number of users.

## Main Blockchain Structure
A new blockchain architecture is proposed here, that relies on smart contracts for the management and operation of sidechains to a main blockchain, which will serve to store those database and data operations. Here, a sidechain consists of a normal blockchain structure, that “runs parallel to” the main blockchain. It’s a chain of blocks that is spawned from the main blockchain, but that exists outside of the main chain.

Sidechains are an interesting approach to scaling a blockchain because instead of storing all data on the main blockchain, it may be distributed through many sidechains.

Here, each sidechain exists for the sole purpose of storing data related databases. It stores all database management operations, such as database creation, update and deletion, table creation, update and deletion, column creation, update and deletion, and all data management operations, such as data insertion, update and deletion. Since a sidechain stores all these operations, executing all stored operations in order, from the sidechain’s genesis block to the latest block, on a traditional database server, leads to reaching the current up-to-date state of the databases.

## Sidechain-as-a-Service Economic Model
Each sidechain is born from the agreement on a sidechain service request that specifies its servicing and financial accounting rules, such as: 
* the service level requirements
* the financial commitment of the service requester and service provider
* the financial incentives for participating as a service provider
* the financial penalties of not complying with the requirements 

Both service requester and service providers must stake tokens in order to participate. The service requester stakes tokens in the service request, which ensures its distribution to the service providers according to block production, and service providers must stake tokens to participate in the service provision, which they will lose if service requirements aren’t met.

## EOS for the Main Blockchain
This system requires a main blockchain that has smart contracts capabilities and that has a high throughput of blocks. We chose to use the EOS blockchain for this project. This system requires two smart contracts, one for managing the sidechains, called *operations contract*, and one for managing the sidechains financial accounting, called *accounting contract*. For more information on EOS, please check [EOSIO](https://eos.io/).

## BlockBase Token
BlockBase will use its own token, the BlockBase Token. This is the token that will be used by the *accounting contract*, such as adding stakes and receiving payments for the services provided to sidechain owners.

## Smart Contracts
### Operations Contract Role in the Consensus
The operations contract is responsible for keeping track of the latest block headers that have been accepted as valid by the network. Every time a new block is produced, the other producers in the chain will need to validate it for it to be accepted as valid and to become irreversible in the contract.

Producers who fail to produce blocks during their turn will get flagged in the contract, and added to the blacklist of the sidechain they were producing. If a producer is expelled from the sidechain network, he won’t be able to get its stake back.

### Accounting Contract Role in the Consensus
The accounting contract is based on the EOS token contract, retaining all of its functions, as well as security measures. This means that users can expect the token to have the same behavior as the EOS token.

<p align="center"><img src="https://github.com/blockbasenetwork/documentation/blob/master/images/img2.jpg"></p>

### Requesting a Sidechain Service
Requesting a new sidechain requires a requester to allocate stake, which will be the source of tokens used to pay the providers working on the sidechain. The requester will be responsible for making sure the stake is enough to pay every producer until the next settlement phase (explained further ahead).

When configuring a sidechain, the requester will be able to configure the desired time between blocks, the block size, the payment per block, the minimum stake from service providers, and the number of blocks that should be produced between each settlement phase. This information allows potential providers to decide if they want to place a stake in the sidechain to become a candidate to produce blocks.

## Sidechains Lifecycle Management
All sidechains are managed through the use of the two smart contracts. It requires various phases as follows:
* Request Phase
* Application Phase
* Applicants Selection Phase
* Sidechain Production Phase

<p align="center"><img src="https://github.com/blockbasenetwork/documentation/blob/master/images/img3.jpg"></p>

## Receiving Payments
The number of tokens each producer gets is based on the number of blocks produced between settlements.

## Data Storage and Security

The security of BlockBase is based on CryptBD. This implementation isn’t in any way mandatory for BlockBase to work. Different variants from the client application may be implemented, that could provide different encryption strategies for the data. The service providers have no say on how the data is encrypted.

With our implementation, the service requester only needs to possess a master key and a password or passphrase. All remaining keys are derived from these two, and enable a hierarchical encryption of the database.

In order to query data, a bucketing approach is used. The larger the bucket the less information it reveals about the data, but also the less it aids in helping to filter or order the data. Two different techniques are used to allow for equality queries and range queries.

<p align="center"><img src="https://github.com/blockbasenetwork/documentation/blob/master/images/img4.jpg"></p>


## Conclusion
In this paper we proposed a blockchain system capable of storing user's data without compromising their privacy, using sidechains for horizontal scaling and a dynamic market to incentivize potential block producers to provide their services in return for token rewards. This solution is built on the [EOSIO](https://eos.io) platform and is planned to be launched in the EOS mainnet.

## Disclaimer
This white paper is provided as is, all the information presented represents the current plans of the BlockBase team and is subject to change at any moment, and shouldn’t be taken as a promise of implementation.

