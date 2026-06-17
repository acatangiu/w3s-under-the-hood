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
- data you store here - content addressed
- accessible natively through the light client using IPFS Bitswap
- No gateways. Decentralized.
- One important caveat:
- stored data is ephemeral
- function of capacity over time
- 2 weeks lifetime by default
- can be manually renewed

S8:
- this is not slideware
- Levity is used by real dApps you'll see and interact with in W3S
- host entire web-apps on .dot domains
- used for file & media transfers in chat apps
- used for app assets like Event data, or collectible art
- and it is fully integrated with the SCs platform to manage it all
- these are real usecases you can explore implementations for in the W3S open stack

S9:
- the last main superpower is called Humanity
- prev known as PoP
- provides: one person, one account
- social games prove you are a unique human, without relying on gov IDs or invasive biometrics
- once you prove humanity through social game(s)
- get added to a RingVRF, that can ZK proof membership without disclosing identity
- derive per-domain aliases
- effectively get cross-app SSO with no cross-app tracking
- give examples


S10:
- gives dApps superpowers like:
- social media without bots
- genuine communities of people
- best part:
- get sybil resistance without relinquishing privacy

S11:
- bring it all together
- one of many possible examples:
- Marketplace dApp
- sellers & buyers verified humans
- reviews and ratings verified humans
- s & b get private chat
- listings hosted in censorship-res. storage
- SCs provide trustless escrow
- All reached through one API
- All verifiably and trustlessly accessible through light client
- these properties cryptographically guaranteed by the infrastructure

S12:
- so I leave you with this
- GO BUILD
- IT'S OPEN SOURCE
- the web3 stack has arrived
- gives web2 ease with web3 guarantees
- now it's up to you to bring forth the new private and human-centric internet
- have fun!