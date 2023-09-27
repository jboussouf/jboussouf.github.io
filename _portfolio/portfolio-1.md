---
title: "Confidential, secure and optimal communication: Secure P2P chat application using java"
excerpt: "In this work, we will propose a secure P2P chat application in java programming language, and this system consists of a robust, fully decentralized (P2P) and end-to-end encrypted network architecture.<br/><img src='/images/communication_P2P.png'>"
collection: portfolio
---

The need to transmit messages between us human beings requires a strong need for security due to the existence of sensitive data; this always leads us to find more confidential means of communication when messages are transmitted from a sender to a receiver. In other words, it is a matter of avoiding the survival of messages by bailout attacks.

Today we find enough applications that perform this task, but as far as the idea of peer to peer is concerned, we don't find enough, because its network architecture presents complications to ensure real security since there is no controlled organization that manages the transmission of messages. At this stage, we have worked in this project to develop a secure chat application that includes more powerful encryption and coding methods, we are talking about RSA, AES... .<br/><img src='/images/communication_P2P.png'>

<h2>Network architecture</h2>

The general architecture of the proposed system is in the form of a complete and fully connected graph: there are nodes that are connected to each other by a virtual communication channel. The nodes on the one hand are defined by a logical address (IP), a key pair (public/private) and an identifier (ID) so that they are recognized by the rest of the network.

Network architect:
<br/><img src='/images/net_arch.png'>

<h2>Data exchange</h2>

When communicating between nodes in the network, nodes send secure packet types based on the state of the communication, i.e., each node enters a three-state process before it can communicate securely. These states are reached as soon as the receiver accepts each of the three packet types. The first is for discovering the nodes in the network, the second is for exchanging key packets (AES) to manage them. The first is for discovering the nodes in the network, the second is for exchanging key packets (AES) to manage them securely, as we will see later, and the last packet is used for sending the message and for general communication. These packets usually circulate in an internal network where the architecture is defined.


<br/><img src='/images/msg_exchange.png'>

<h2>Security</h2>

<h3>Representation of the network</h3>
we have configured our network as a darkroom, this room is divided into sub-areas, each area is represented by its address (1-1, 1-2, ..., n-n). For this room users can't see other areas without sending a scan packet and if this area is full of a user, the user sends another acceptance scan packet with his information.

<br/><img src='/images/new_user.png'>
<br />
Currently, if a new user wants to be added to the network, it sends a message to each zone, the message contains its name, and if a user exists in a zone, it adds the new user to its user list (infoNode list as a new node). Then the receiver sends the person who scanned an accepted scan packet with the receiver's ID.
<h3>Scanning</h3>
As we have seen, the user sends a packet to each network zone. If a user exists in one of the zones zone, the receiver creates a new infoNode containing the new node's information and adds it to a list of nodes, then to a list of nodes, then generates a packet with its ID and sends it to the sender to do the same job of adding a new node. add a user to its list of nodes.

<br/><img src='/images/scan_net.png'>

<h3>Exchange of keys</h3>

At the moment, the user has a list of other users but he can't establish a secure communication with the other users, so we have to use AES to generate a secure communication channel and to exchange this and to exchange this key we have to use another algorithm called RSA algorithm, and the users exchange the AES keys by sending a packet of type setAES and also include the public key of the RSA key pair ; then the receiver of the packet generates an AES key and adds it to the information of the sender's node, then encrypts it with the RSA public key, then generates a getAES packet, and for the time being the new receiver (which was a sender) decrypts the AES key using the RSA private key and adds it to the sender's information.

<br/><img src='/images/key_exchange.png'>

<h3>Communication</h3>
Finally, for the moment, we are able to communicate in a secure way and without going through a server (decentralized) and to use a secure channel to exchange messages.

<br/><img src='/images/comm.png'>

Project URL on github: <a href="https://github.com/jboussouf/Confidential-secure-and-optimal-communication-P2P">jboussouf/Confidential-secure-and-optimal-communication-P2P</a>