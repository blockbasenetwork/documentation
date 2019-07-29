# BlockBase Whitepaper
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






