S1:
- Hi, I'm Adrian
- Now that Torsten showed the host container and unified API
- I will show you some of the infrastructure behind it
- Not gonna explain blockchains and SCs - you already know those
- focus on new powerful decentralized infrastructure pieces
- ones that allow building human-centered Web3 dapps with no central servers and no trusted intermediaries
- all available through the Trinity API

S2:
- Busy building a full developer platform on top of Polkadot stack
- you'll enjoy building on this platform,
- made up of too many pieces
- focus on 3 superpowers
- Celerity - Private interactions
- Levity - Censorship-res. storage
- Humanity - verified humans
- all exposed thru one api
- all trustless and verifiable via the light client

S3 (1 min):
- I mention the LC, bc
- most w3 apps still trust one server to tell them the truth.
- ours don't
- Smoldot is a light client running inside the host container
- dapp gets out of the box
- no RPC provider to trust, can rate-limit or censor users
- the light client IS the connection
- built-in native support to the superpowers I am about to showcase

S4:
- 1st superpower - Celerity - private, serverless messaging
- it is your dApp's TCP for confidential, serveless comms
- what we want
1. relies on no trusted servers - powered by decentralized celerity swarm
2. there is no metadata leakage - external observers can make minimal inference about what or who
3. (src, dest) pair confidential
4. msgs e2e encrypted - only src and dst holding decryption key

S5 (3m):
- the way - relatively simple st-and-fwd pub/sub architecture
- Topics are keys · statements are values
- I likened it to TCP earlier - not exactly
- No strong delivery guarantee — but eventual delivery.
- Good enough.
- You publish to a topic, interested parties subscribe.
- That's it.
(now go to previous slide and explain on prev diagram)
- let's see how our requirements are satisfied
- A & B run Diffie-Hellman key exchange - secret private key - secret session topic
- A publishes encrypted messages to this seemingly random topic
- Swarm gossips all messages including A's message
- (each peer actually gossips a pseudo-random-distribution subset of all topics)
- B is part of that swarm and acts similar to other peers
- any observer outside cannot infer that (A, B) as (src, dst)
- obv example of dapps feature:
- e2e encrypted chat, where nobody can infer
- who talks to who, how much or how often, etc
- fully resilient, with no centralized server to hack, or otherwise backdoor into
- pretty cool!

S6 (1:30):
- we've seen private chat
- what about audio or video calls?
- you can do that too!
- decentralized & completely private
- Celerity as control-plane
- WebRTC as data-plane
- Celerity carries the WebRTC SDP offer / answer exchange
- Call happens p2p, e2e encrypted over direct WebRTC
- same model can be used for:
- detecting presence
- confidential coordination
- private notifications
- any general signaling for negotiating some other protocol
- these normally need a server you run + trust
- here neither is required!

S7:
- another critical thing apps need is storage
- the 2nd superpower - is censorship-res. and dec. storage
- 