---
title: 'Networking Architecture for Multiplayer Games: Part 1'
date: 2023-02-22 5:38:00 +0300
categories: [Programming]
---

Game networking is one of the components that distinguishes a multiplayer game from a single player game. When working on multiplayer games the developers need to take care of how the players are going to interact with each other. This requires a direct/indirect channel of communication between the players(clients) and also establishing a common protocol. This part of the logic is called networking.


This post is an introduction to some of the important components of game networking to help decide the right options for your game architecture.

## Network Topology
Is the game designed to be played on same computer (offline multiplayer), same network (local multiplayer) or over the internet? The answer to that determines the network topology you'd want to choose.

### Offline Multiplayer
Here obviously you don't need a network, however this makes easier to cheat as the data is stored on client side and could potentially be tampered. But if validation is needed dedicated server should be considered.

### Peer to Peer
Best suited for local multiplayer games. There are two types, client hosted and mesh based. If the game is client hosted, one player (the host) acts as a server and a client while the rest of the players connect to it. The host has a lower latency and could potentially cheat as a server, giving an unfair advantage. Alternatively, in mesh based each player acts as a server and client establishing a direct connection with other players as they validate the players' actions to prevent cheating. However mesh based is difficult to setup and requires more bandwidth.

### Dedicated Server
This is by far the most common choice. A dedicated server is setup and all the players connect to it. This is an authoritative server that validates players' actions and confirms legitimate input. It is usually setup in the cloud which costs money.

As you may have noticed, network topology is mainly a trade-off between lower cost and cheating prevention.

In the next section I'll talk about choosing the network protocol and serialization techniques.

Cya.