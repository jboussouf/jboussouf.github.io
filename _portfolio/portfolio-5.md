---
title: "Elliptic curve in PARI/GP using python"
excerpt: "In this work, we represent how to use PARI/GP for elliptic curves with python and apply it to the use of ECDH and ECDSA.<br/><img src='/images/ECC.png'>"
collection: portfolio
---

In terms of security, cryptography is just a cover between the attacker and the network users. The right choice of cryptosystem is therefore a difficult mission and one of the good cryptosystems used is the elliptic curve.<br/><img src='/images/Sec_level.png'><br>
Thus, as we can see, we get the same level of security for small key lengths, since for level 80 we only need 160 bits while 1024 bits are needed for the RSA encryption system. For elliptic curves, there is not only one algorithm, but we use each algorithm for a given task, like for key exchange we have to use ECDH and for digital signature we use ECDSA or EdDSA.

<h2>Setup</h2>
To use <a href="https://pari.math.u-bordeaux.fr/doc.html">PARI/GP</a> in python, we need to use a python library named <a href="https://github.com/sagemath/cypari2">cypari2</a>, this library supports both Python 2 and Python 3. To install it, we use:

```
pip install cypari2 [--user]
```
(the --user option allows to install cypari2 for a single user and avoids using pip with administrator rights). Depending on your operating system, the pip command can also be called pip2 or pip3.

Or we can also use:

```
  pip install git+https://github.com/sagemath/cypari2.git [--user]
```
for the moment, we are able to use PARI/GP with python.

<h2>ECDH in python</h2>

Elliptic-curve Diffie–Hellman (ECDH) is one of the most used cryptosystems for key exchange and used by "IMessage, Whatsapp, SSL, HTTPS", and in this section you can check the file ECDH.ipynb to see the full code of this algorithm.

The first thing we have to do is to check if cypari2 is already installed in the system, if not we have to install it.

<h3>System part</h3>
In this part we use an object of the ECDHSys class and then we output the system parameters.
```
  ecdhSyd = ECDHSys(a, b, p)
```
if we enter a=0, b=7 and p=43, the output will be :
```
{'a': 0, 'b': 7, 'p': 43, 'ordre': 31, 'generator': '[32, 3]'}
```
<br/><img src='/images/ell_elem.png'>
<h3>User part</h3>
In this part we will use an object of the ECDHUser class, then we will use it to generate a random private key; then we will double the chosen generator by the system class.
```
ecdhUser = ECDHUser(sysKey)
```
Thus, between each user, we generate an encrypted key between them (in this example, the encrypted key is [2, 12]). We can now use this key for key exchange.

<br/><img src='/images/key_ex.png'>
<h2>ECDSA in python</h2>
ECDSA is a digital signature bayser by the elluptic curve cryptographic system and one of the most popular digital signatures used by many blockchains like bitcoin, ethirum, dodgecoin, etc. And for our project ECDSA is represented in the file ECDSA.ipynb.

First of all, for our project, we will use ECDSASys to create an object named ecdsaSys. This object will create the important parameters to use it to generate keys for the digital signature.
```
  ecdsaSys = ECDSASys(0, 13)
```
(There is a section in the code where we loop over part of the code and generate a random prime number until the order of the curve is a prime number because we are looking to do PGCD(prime, order, outher number) = 1, and the only way to get that is to do PGCD(prime, order) = 1.)

<br/><img src='/images/ECDSA.png'>

Thus, for the time being, any user of the system is able to generate a key pair to sign and verify the signature of the other. To generate a key pair, the user uses an ECDSAUser object and takes as argument the parameters of the system, to generate a private key "d" and a public key "A" formed as a point, then the user signs a piece of information (hash of the transaction in the case of a transaction), then sends the information to the other users with the clear information to verify the signature.

```
  ecdsaUser = ECDSAUser(parameters)
```

<br/><img src='/images/Sign.png'>

<h2>Conclusion</h2>
Elliptic curves are one of the most used encryption systems in the world of digital signature and key exchange, by many algorithms such as ECDH and ECDSA, but for digital signature, there is a problem to find a curve with a modulo number in the modulo section has a prime order, and it makes a big problem for us to use a recommended curve like secp256k1 that we use in the bitcoin digital signature, or use on a curve, but we have to try until we find a great curve with a prime order. Like the work of a foundryman, we are trying to find a method to know if a curve is a light to use for the digital signature.

Project URL on github: <a href="https://github.com/jboussouf/Elliptic-Curve-Cryptography">jboussouf/Elliptic-Curve-Cryptography</a>