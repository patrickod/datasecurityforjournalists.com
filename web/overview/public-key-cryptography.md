---
layout: page
title: Public Key Cryptography
permalink: /overview/public-key-cryptography.html
---

## The traditional method and problem
Traditionally when people (Alice and Bob for example) wanted to
communicate securely Alice would encrypt the message with a secret (e.g.
"mysecretpassword"), resulting in an unintelligible blob of information
(the cyphertext).

For Bob to be able to retrieve the original message from the cyphertext
he'd need to know the original secret.

The problem in this scenario is that both Alice and Bob must share the
same secret "mysecretpassword". This is particularly tricky if they are
communicating only by means which they don't think are secure
(unencrypted email, SMS etc...). If someone was listening to their
messages they'd be able to intercept the secret key and read all of
their encrypted communications.


## The solution: Public and Private keys
Public key cryptography is a neat solution for this problem. It works by
introducing the concept of a pair of two separate types of keys, one
used to encrypt messages, the other to decrypt those same messages.
These two keys are commonly referred to as the public and private key
respectively.

A pair of public and private keys share the property that messages
encrypted with a given public key can **only** be decrypted by the
corresponding private key. This means that public keys can be shared
openly with anyone without risk. You only need to keep your private key
secret from everyone.

## Alice and Bob try again
In this new scenario Alice and Bob would generate their own public and
private keys and share their public keys with each other.

When Alice wants to send a message to Bob, she encrypts it with Bob's
public key. The remaining cyhpertext can only be decrypted by Bob's
private key.

Now Alice can send Bob messages securely, safe in the knowledge that
only Bob can decrypt them.


## The problem: Which public keys can I trust?

While public key cryptography removes the problem of shared secrets, one
major problem that remains is this: how do you trust that a given public
key really belongs to someone.

For example. Malory could create a new public key with Bob's and share
it publicly. When Alice wants to communicate with Bob she could find the
fake key Malory created and use it to encrypt her messages. Alice thinks
that only Bob can read them, but in reality only Malory can.

This is a problem of key distribution and verification. There are
methods you can use to ensure that the key you have is really that of
the person with whom you want to communicate.

## Verifying public keys.

To communicate with someone securely using public key cryptography you
must first validate the public key you have for someone.


## Fingerprints

Your key can be many thousands of characters long. To make it easier to validate keys it's possible to generate a much shorter unique identifier called a fingerprint for that key. This fingerprint (around 40 characters) can be used to uniquely refer to the particular key that generated it.

Thus if when Alice is trying to validate Bob's key both Alice and Bob generate and compare the fingerprints they'll only have to check 40 characters instead of the many thousand in the key.

**NB** When comparing fingerprints it's extremely important to check that every character and letter match. A single non-matching character could indicate that someone has maliciously generated a fake key in a bid to impersonate the key owner.

## Verifying keys out-of-band

There are many ways to validate a person's key. If possible the best
solution is to physically meet the other party and compare the public
key that you have for them, and their own public key.

You can verify the fingerprint by reading it aloud over a phone call and verifying that you both have the same fingerprint for the same key, or by writing it down and exchanging fingerprints in person.
