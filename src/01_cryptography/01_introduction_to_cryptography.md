# Introduction to Cryptography

Cryptography is a tool that forms the core of Web3 technology. Before understanding and developing Web3 systems, an understanding of cryptography and the assumptions we make with cryptography is neccessary.

## Goals of this Chapter

* Understand the goals desired when using cryptography
* Understand the assumptions we make about cryptography
* Learn about cryptographic primitives

## The Problem

The internet is an open and public space. However, some issues emerge when using it.

### Security

We assume the internet is considered an open and public place. We use the internet to communicate messages to each other while assuming some sense of identity. Given this assumption, individuals will exists that may try to impersonate others, tamper with messages, or read messages that were not intended for them.

This provides the problem of ensuring identity and message authenticity.

### Resources

For the internet to exists, we need both storage and computation - both of which are physically limited.

This means that we must strive to be efficient with our usage of the internet.

### Privacy

We can assume that all channels of communication on the internet are, in some way, monitored.

This makes ensuring privacy through the means of a system pratically impossible.


## The Solution (With Cryptography)

**Kerckhoffs's Principle**: A cryptographic system should be secure even if everything about the system, except the key, is public knowledge.

In other words, instead of depending on the system (the internet) to provide security, we should instead depend on the content of our messages to solve our problems.

### What Cryptography Provides

As hinted by Kerckhoffs, cryptography provides us the means to acomplish this. Cyrptography provides tools that allow us to communicate in public spaces while ensuring security and privacy. This security comes from controlled data assessiblility, message authenticity, and data integrity.

* **Data Accessiblity**
  
  To obtain access to cryptographically secure (encrypted) information, one must know a secret (normally called a key).
  
  It must be possible to communicate the knowlege of a cryptographic key without sharing the key itself.
  
* **Message Authenticity**

  Often when communicating phisical information, we use a written signature to "prove" that we were the origin of said information. Similarly, a cryptographic signature may be used provide authenticity.
  
  A cryptographic signature should verify that the signer knows a secret without sharing the secret itself and should be, practically, impossible to forge.

* **Data Integrity**

  Where as the content of a message signed with a physical signature can be manipulated without the signature itself becoming invalid, the same is not true in the context of cryptographic signatures. If the content of a message is changed after signing, the existing signature is no longer valid for that message.

## Cryptographic Primatives

### One-Way Functions & Hash Functions

### Symmetric Encryption

### Asymmtric Cryptography

### Cryptographic Signatures
