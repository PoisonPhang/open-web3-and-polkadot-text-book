# The Problem

## Context

Due to the internet being a public space, bad actors will exist who will:

* Read messages not intended for them
* Impersonate others
* Tamper with messages

We still exist in a world where resources such as bandwidth, storage, and 
computation are all limited.

Closed channels are, by definition, heavily constrained and unlikely to exist in 
a useful capacity.

## Open v.s. Closed Channels

Kerckhoff's Principle: Security should not rely on secret methods, but rather on 
secret information.

Meaning, we should not strive to create secure/closed methods/channels but 
instead data that is secured independently of a system.

# The Solution

## Message Authenticity

Like physical signatures, cryptography may be used to reasonably prove the origin 
of a message and infer that the message is authentic.

However, unlike cryptography, physical signatures are very easy to 
forge/reproduce.

## One-Way Functions

The basis of cryptographic hashing and asymmetric cryptography.

* (Generally) fast to compute
* Hard to invert
* May have a secret that makes them easy to invert

## Hash Functions 

Hash functions are a critical example of one-way functions. Hash functions 
provide some means of proving the content of some data is the same as another.

### Applications

* Representation of larger data
* Keys in a database
* Digital signatures
* Key derivation
* Psudo-random functions

### Properties

* Accept unbounded size input
* Map to a bounded output
* Fast to compute
* One-Way Function
* Resist pre-image attacks
* Resist collisions

#### Pre-Image attacks

The attacker controls one input

#### Collisions

Two different data elements that produce the same output when hashed

### Other Notes

* Input Sensitivity - Changes to the hash do not scale directly to the change of 
the input (i.e. "hello." and "hello" should produce very different hashes)
* Non-Cryptographic hash functions may not be one-way and may not resist 
pre-image attacks & collisions

### Examples

* xxHash (non-cryptographic)
* MD5
* SHA1
* RIPEMD-160
* SHA2-256
* SHA3
* Keccak
* Blake2

### Benchmarks

![Benchmarks](./crypto-bench.png)

## Symmetric Encryption

Some functions that, given some data and a key, produces a hash that is 
reversible given the original key.

```
x = [some data]
k = [some key]
se = [some symmetric encryption function]

o = se(x, k)

x == se(o, k)
```

### Examples

* ChaCha20
* Twofish
* Serpent
* Blowfish
* AES
* DES,
* XOR

### XOR Example

```
Plain: 1010   --> Cipher: 0110
Key:   1100   |           1100
       ----   |           ----
       0110 --^           1010
```

## Considerations

Care must be taken when working with symmetric encryption. Unsalted passwords 
and [Exploring an Encrypted Penguin with AES-ECB](https://tonybox.net/posts/ecb-penguin/) 
are great examples of this.

## Asymmetric Cryptography

* Transforms one value (secret key) into a corresponding counterpart(public key) 
* Believed to be a one way function
* The public key does not reveal what the original secret key is
* Using only the public key, information can be transformed (encrypted) such that those with 
knowledge of the secret key are able to regain the original information
* Using the secret key, information can be transformed (signed) such that anyone 
with knowledge of the information and the public key is able to confirm the 
validity of the information

### Asymmetric Protocols

* Slowest to fastest: RSA, Elgamal, Elliptic Curve
* Elliptic Curve Cryptography (ECC)
  * ECDSA (SECP256k1, SECP256r1)
  * Schnorr
  * EdDSA (Ed25519, Ed448)
  * Schnorr/Ristretto 25519
  * BLS
* ECC requires double the bits to the symmetric AES for the same level of security (e.g. 128 bit security requires a 256 bit ECC key)

## Considerations

* Symmetric cryptography is much faster but requires more setup and trust
* Asymmetric cryptography is slow but maintains relationships such that less trust is required
* Both can be used in different parts of a system in hybrid cryptography
  * Symmetric encryption can provide speed and confidentiality
  * Asymmetric can dictate relations among the participants
  
## Digital Signatures

Digital Signatures guarantee the authenticity and integrity of a message.

* **Signing Function:** A pure function which takes some message and a secret to output a signature
* **Signature:** Proves the signer knew the secret without revealing the secret itself
* A signature cannot be used to create more signatures
* Can affirm authorship and integrity if the message is public information

### Considerations

Signing large amounts of data is not efficient. Hashing large amounts of data is efficient.

Assuming the verifier of a signature is able to produce a hash of the message, a signature on the hash (relatively small) implies a signature on the message itself.

## Certifications

Certifications are used to make attestations about public key relationships.

Typically, by signing:

* One or more identifiers (e.g. public key, hashes)
* Information about ownership, witnessing, and/or attesting
* Metadata about the information which could ensure conditional validity

# Summary

Cryptography allows us to:

* Safely communicate on public networks
* Access information 
* Have expectations about a message's authenticity and integrity
* Prove knowledge of a secret without sharing the secret
* Represent large amounts of data