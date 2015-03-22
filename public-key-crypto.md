# End to End cryptography
End to End cryptography is the ability for 2 people to communicate
securely over insecure connections. To do this two users who want to
communicate must first generate crypto key

# Public key cryptography

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
their messages.


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
