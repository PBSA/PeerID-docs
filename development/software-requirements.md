# Software Requirements

#### 1. Introduction

The rationale behind the dApps is to develop applications using the rock solid transaction capabilities, tamper proof immutability and the impenetrable security offered by the Peerplays blockchain platform.

While these are compelling reasons for developers to use blockchain technology, the need for end to end application development knowledge, traditional enterprise backed software development methods etc create entry barriers for developers.

A Blockchain Middleware System \(BMS\) platform with various components will be build by PBSA to address these unique challenges. Our goal is to expose general purpose APIs which can be accessed in a language and platform agnostic way and thus making it possible for developers of varying skill sets to create applications on the blockchain.

**\(Figure 1: High-level design topology of a dApp\)**

#### 2. Identity management

User management and identity management is a major part in any application development and the blockchain with unique security constraints brings challenges to the same. While the public key cryptography based account access provided by the Peerplays blockchain is secure compared to a username password based authentication, the same makes it challenges and next to impossible for laymen to create and use dApps. A common alternative proposed is using cryptocurrency wallets. This doesn't really solve the on-boarding challenge as a tiny set of internet browsing population and cryptocurrency wallets.

To ensure faster and smoother on-boarding of users, Peerplays is thus creating an identity management and SSO platform which helps anyone with an email address, Facebook or Google account to easily create an account on the Peerplays blockchain. For tech-savvy users the traditional blockchain mechanism will be used to create the accounts.

In addition to the account creation, Peerplays will also provide simpler mechanisms for dApp developers to create and provision dApps and configure various dApp level permissions.

#### 3. Requirements

**3.1 High level Requirements**

This section will define each of the high level components of the the identify manager product - PeerID.

The components:

* account creation
* retrieving Peerplays keys
* dApp provisioning
* dApp Permissions
* unlinking third party services
* Multi Factor Authentication
* Anti Phishing features

**3.1.1 Account creation3.1.2 Retrieving Peerplays keys3.1.3 dApp Provisioning3.1.4 dApp Permissions3.1.4.1 External conditions3.1.5 Miscellaneous Features3.2 Functional RequirementsAccount creation1.5.dApp provisioning**

