# Specification

v0.0.1, March 01 2021

This is a rough sketch of an actual spec for the Project Photon protocol (PTTP). It is far from complete, so changes to this document may be drastic. You can write code to this pseudo-specification and be confident that it probably won't become totally non-functional due to massive changes next week, but you are still urged to keep an eye on ongoing development of the protocol and make changes as required.

This is just here so that I am able to pen down my thoughts for this document as fast as possible, while letting people know what to expect of the specification.

Any feedback on this is very welcome, please email [raphpb1912@gmail.com](mailto:raphpb1912@gmail.com).

### Status of this Memo

This memo provides information for the Internet community.  It does not specify an Internet standard.  Distribution of this memo is unlimited.

### Introduction

photon.  n.  1. A particle representing a quantum of light or other electromagnetic radiation. A photon carries energy proportional to the radiation frequency but has zero rest mass.  2. (computer tech.) software protocol specifying a simple standard to allow devices to transmit and recieve data.

## 1 Overview

Photon Transfer Protocol (PTTP) is a client-server protocol featuring request-response transactions and the network protocol specification that is used for communicating between clients and servers. Photon servers and clients can transmit data to and from each other via Bluetooth (Internet Protocol), which is prioritized over LAN/WLAN. Clients communicate to each other via Bluetooth to fetch main page content and Network protocols that stream larger chunks of optional data from the server to the client. The optional loading is only done after the initial page load and is loaded asynchronously while the user can view the content of the document. This specification also covers every aspect of how the client and the server should receive and transmit data to and from each other, like how the Bluetooth should be implemented and how beacons should be set up on clients that receive widespread data from Wireless/Wired Networks before mirroring them to other nearby devices. Connections are closed at the end of a single transaction and cannot be reused. When Photon is served over TCP/IP, servers should listen on port 88. This is an unprivileged port, so it's very easy to run a server as a "nobody" user, even if e.g. the server is written in Go and so can't drop privileges in the traditional fashion.

### 1.1 Photon Transactions

