---
title: "Elliptic curve in PARI/GP using python"
excerpt: "In this work, we represent how to use PARI/GP for elliptic curves with python and apply it to the use of ECDH and ECDSA.<br/><img src='/images/ECC.png'>"
collection: portfolio
---

In terms of security, cryptography is just a cover between the attacker and the network users. The right choice of cryptosystem is therefore a difficult mission and one of the good cryptosystems used is the elliptic curve.<br/><img src='/images/Sec_level.png'><br>
Thus, as we can see, we get the same level of security for small key lengths, since for level 80 we only need 160 bits while 1024 bits are needed for the RSA encryption system. For elliptic curves, there is not only one algorithm, but we use each algorithm for a given task, like for key exchange we have to use ECDH and for digital signature we use ECDSA or EdDSA.