# Diffie-Hellman Key Exchange

The Diffie-Hellman Key Exchange (DH) is a method of securely exchanging
cryptographic keys over a public channel.

![DH Illustration](https://upload.wikimedia.org/wikipedia/commons/4/46/Diffie-Hellman_Key_Exchange.svg)

## Algorithm
1. Alice and Bob publicly agree to use `p = 23` and `g = 5`.
2. Alice secretly chooses `a = 4`, then sends Bob `A = g^a mod p`, i.e. `A = 5^4 mod 23 = 4`
3. Bob secretly chooses `b = 3`, then sends Alice `B = g^b mod p`, i.e. `B = 5^3 mod 23 = 10`
4. Alice computes `s = B^a mod p = 18` and Bob computes `s = A^b mod p = 18`.

`p`, `g`, `A`, `B` is sent in the clear and `a`, `b` is kept secret. Both parties
arrive at the same secret, `s`.

Note that this can work with anything that has multiplication in it, e.g.
elliptic curves.

## Breaking
The difficulty of breaking this lies in the difficulty of computing the disrete
logarithm.

## Vulnerabilities
- If the channel can be MITM'd, the malicious party may choose to send `A = p`
  and `B = p` instead, hence having `a = b = 1`. https://cryptopals.com/sets/5/challenges/34
- If `g` can be set, one can break it by setting `g = 1, 0, -1`. https://cryptopals.com/sets/5/challenges/35
