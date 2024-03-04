# Sleepy Protocol 0.1alpha

## Base protocol
The sleepy protocol is based on HTTP. This allows it to be implemented in any language and on any platform. Even in a web browser. It is not a protocol for high performance, but for compatibility.

A sleepy peer must support almost all the HTTP 1.1 specification. The Keep-Alive functionality is greatly recommended for performance reasons.

Additionally, the sleepy protocol uses JSON as the main metadata exchange format.

The most basic sleepy peer is a simple HTTP server that serves the files of the [introduction](introduction/MODULE.md) and
has public files matching the [upload](upload/MODULE.md) module filename schema. This type of peer is called _passive_ peer.
The objective of this type of peer is to be able to share files inside sleepy network in the easiest way possible, integrating with existent web servers and applications.

An advanced sleepy peer has the ability to handle HTTP requests and initiate them already. In other words, is a http client and server at the same time. 
This type of peer is called _active_ peer and must handle most advanced behaviors.

The description of the protocol is available as OpenAPI 3.0 definition in the [openapi.yml](https://editor.swagger.io?url=https://raw.githubusercontent.com/sleepy-p2p/protocol/main/openapi.yml) file.
Each request and response describe different behaviors and functionalities of the protocol that must be implemented by _passive_ or _active_ peers.

## Limitations
The use of HTTP has a base protocol has some limitations:
- The peers must have a public IP address or be behind a NAT with port forwarding. If an _active_ peer connect to another _active_ peer, and the other client can't connect back, the second
peer will consider the first peer as _masked_ and some functionalities will be disabled or limited with priority to the _active_ peers that can connect to the other peer.
   - The sleepy clients can have UPnP support to automatically open the ports in the router.

## Modularity
The sleepy protocol is modular. Clients must comply with the implementation of the _introduction_ module as a minimum. All other modules are optional.

### Introduction
The [_introduction_ module](introduction/MODULE.md) performs the initial connection between two sleepy clients and performs the presentations: It exchanges information about the implemented protocol version, about the client capabilities, about the modules it implements....

### Download
The [_download_ module](download/MODULE.md) allows you to download files from other clients using magnet links.

### Upload
The [_upload_ module](upload/MODULE.md) allows you to upload files to other clients.

### Router
The [_router_ module](router/MODULE.md) allows you to search for clients that have the files you are looking for. 

The download module can work without it if the link includes the address of the sources, but it is not a proper P2P client without it.

### Search
The [_search_ module](search/MODULE.md) allows you to search for files within the P2P network.

### Board
The [_board_ module](board/MODULE.md) allows you to create boards where you can publish new topics.

A topic is a post of a message with one or more associated files.

Other customers can subscribe to your boards or topics to keep up to date with your publications.

## Statement of Intent

I have always wanted to build a P2P file sharing client as a hobby. 

I started trying to create my own Ed2k client more than a decade ago, but after a long time fighting with an obsolete protocol with many variants, I only managed to have a very basic and buggy client.

For this reason I started to think about creating my own protocol, open and well documented... but I thought: another protocol? realistically, what can I contribute that emule or torrent doesn't already do?

I thought carefully and came to the conclusion that if I wanted to have some adoption, I had to lay the foundations of my protocol on certain pillars:

- Reuse of a generic protocol already created and widely adopted.
- Focus on creating a protocol that is extremely easy to implement.
- Create a protocol as compatible as possible with all platforms, architectures... and things possible.

The sleepy protocol is my answer to this challenge.

I will try to develop the protocol little by little and once I have it completely defined, I will create a functional client for it as portable as possible.

My priority is my work and my family. This project is just a hobby, but I hope it can be a hobby for many more people, if they wish.
