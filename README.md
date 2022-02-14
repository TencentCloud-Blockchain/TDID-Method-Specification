# TDID-Method-Specification

## Abstract

[TencentCloud Decentralized Identity (TDID)](https://cloud.tencent.com/product/tdid)  provides infrastructure for cross-system and cross-organization trusted digital identity and data exchange services. TDID is based on the blockchain and provides a distributed mechanism for generating, holding and verifying identity identifiers DIDs (Decentralized Identifiers) and VCs (Verifiable Credentials) that carry identity data, enabling you to encrypt security, protect Data privacy and machine-verifiable third-party representation of various types of real-world identities and credentials on the Internet.

## Status of this document

This is a draft document and will be updated based on W3C.

## Introduction

[Tencent Cloud Blockchain](https://cloud.tencent.com/product/blockchain-catalog), as China's leading blockchain service platform and technology provider, is committed to building a blockchain infrastructure for technology, data, value, and industrial interconnection, leading blockchain underlying technology and industry application innovation, assisting the transformation and upgrading of traditional industries, and promoting the deep integration of the real economy and the digital economy.

Tencent Cloud Decentralized Identity (TDID) is a set of digital identity basic services built on the [Tencent Cloud blockchain TBaaS](https://cloud.tencent.com/product/tbaas) platform, which is full-featured and easy to use. TDID provides a mechanism for the distributed generation and verification of globally unique identifiers (Decentralized Identifiers, DIDs) to identify various entities (people, institutions, objects, etc.). At the same time, various types of credentials (Verifiable Credentials, VCs) in the real society are expressed on the network by means of encryption security, privacy protection, and machine verification by a third party, so as to provide cross-organization and cross-regional trust between entities. Provides infrastructure for digital identities, digital credentials and data exchange.

<br />

### Features
#### - Distributed ID Registration

The distributed and multi-centralized ID registration mechanism based on blockchain gets rid of the dependence on the single-center ID registration in the traditional mode. It gives entities (people, institutions, things, etc.) the ability to independently control identity control, and provides basic functions such as entity identity creation, update, and verification.

#### - Distributed issuance/validation

Issuers of various identities/credentials issue data-bearing certificates to entities, and verifiers can verify the entity's identity control right on the blockchain, and further verify the authenticity, integrity, and authority of its identity/credential data.

#### - Trusted flow of data

Distributed interconnection between independent business systems is achieved through blockchain technology, and a trusted data flow channel is easily built to support the cross-system, cross-organization, and cross-region trusted flow of entity identity ID, entity credentials/identity data.

#### - Data Privacy Protection

The real identity and digital credentials of the entity are stored under the blockchain, and the entity can choose the storage location and manage or host it independently. Enabling entities to minimize or selectively disclose information to other entities.

#### - Portability and Interoperability

TDID data can be ported to other platforms that follow the same specifications, and currently supports mainstream blockchain platforms such as Chainmaker, FISCO-BCOS, and Fabric. At the same time, TDID provides standardized interfaces to support cross-chain and cross-platform interoperability.

<br />

### Current Application scenario
#### - Unified online government service 
TDID provides the credible electronic ability of the license requirements to improve of the governmental affair efficiency.


#### - Educational training certificate / Reference Check
TDID provides cross-institutional collaboration tools to make Educational collaboration easier.


#### - Medical data interconnection
TDID provides data privacy and trusted transfer capabilities to ensure Medical information interconnection


#### - Supply chain finance
Through TDID, enterprises with financing needs can be used as the center to apply to credit endorsers such as core enterprises or upstream and downstream enterprises for accounts receivable/payable, trade bills and other documents, and then submit them to the bank for verification through TDID, enable to Confirm the source and completeness of the data to increase the credit for financing.

<br /><br />

## Tencent Cloud Distributed Identity DID Method

The DID identifier of Tencent Cloud Distributed Identity is defined as:  `tdid`. 
The DID method format of the `did:tdid` identification system is composed as the following format.

```bash
# tdid
"did:tdid:" + tdid-router-id + ":" + tdid-identifier

# tdid-router-id
less than 10 characters composed of lowercase letters and numbers

# tdid-identifier
the prefix of tdid-identifier is 0x, followed by 40 characters composed of lowercase letters and numbers.
```
Example did of TDID is 
`did:tdid:cb534-15:0x1e7115081c178459be8d3844dd129b2234edc6be`

<br/>

## DID Document
Example did document of `did:tdid:cb534-15:0x1e7115081c178459be8d3844dd129b2234edc6be` is

```json
{
  "@context": "https://w3id.org/did/v1",
  "id": "did:tdid:cb534-15:0x1e7115081c178459be8d3844dd129b2234edc6be",
  "created": 1642992401,
  "updated": null,
  "publicKey": [
    {
      "id": "did:tdid:cb534-15:0x1e7115081c178459be8d3844dd129b2234edc6be#keys-0",
      "type": "Secp256k1",
      "owner": "did:tdid:cb534-15:0x1e7115081c178459be8d3844dd129b2234edc6be",
      "publicKey": "9140759724994454628181963565667341739731028461151630822625149865018431527829307192022895075113804689383949423804960687290646469426121233393934795192655714",
      "revoked": false
    }
  ],
  "authentication": [
    {
      "type": "Secp256k1",
      "publicKey": "did:tdid:cb534-15:0x1e7115081c178459be8d3844dd129b2234edc6be#keys-0",
      "revoked": false
    }
  ],
}
```

<br/> 

## CRUD Operations

did:tdid method(CRUD) are implemented by the Tencent Cloud Distributed Identity (TDID) service that generate the identifier and create DID documents to save in blockchain. 

To operate DID Documents, you should first execute prerequest which is creating an account of the [Tencent Cloud](https://cloud.tencent.com/) service and TDID service.

To improve interoperability, The identifier is calculated from the public key, then is published in decentralized blockchain.

### Prerequest

Create an account from cloud.tencent.com at first, then operate following below:
1. create your owner DID service in the TDID service
2. create a DID identifier on your owner DID service that created by the first step
3. DID CRUD can be operating on the console of the TDID or called by Tencent Cloud api

### Create

```bash
# endpoint
the tencent cloud api url

# Input
{
    AK/SK, PUBICKEY, BLOCKCHAIN_ID
}

# Output
{transaction Id}
```

### Read

```bash
# endpoint
the tencent cloud api url

# Input
{
    AK/SK, TDID
}

# Output
{TDID Document}
```

### Update

DID Document does not support update.

### Delete

```bash
# endpoint
the tencent cloud api url
# Input
{
    AK/SK, TDID
}
# Output
{transaction Id}
```

<br/> 

## Safety considerations

The CURD operation of TDID on DID is exposed through Tencent Cloud public cloud API. Users need to pass AK/SK authentication to call the operation method of DID. AK/SK authentication helps to further improve the security of TDID service.

<br/> 

## Privacy considerations

1. The DID identifier of the TDID service is generated by the operation of the public key, so it supports the user's own private key and private key escrow modes to register DID:
- The user automatically creates a public-private key pair through the system or imports the private key to register the DID, and the private key is hosted in the TDID service.
- The user enters the public key to create (agent mode) registration DID, and the private key needs to be held by the individual.

2. The user's private information is stored in a verifiable credential, and the VC is stored under the user's Tencent Cloud account, which can only be obtained through AK/SK authentication.
