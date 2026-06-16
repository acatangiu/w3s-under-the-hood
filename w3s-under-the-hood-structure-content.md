# W3S Presentation Proposal "Polkadot Developer Platform: Under the Hood"

**Presenters:** Torsten & Adrian **Slot:** 45 min shared. Torsten \~20 (the boundary: TrUAPI, triangle container, host). Adrian \~20 (the decentralized infrastructure behind TrUAPI). 5 min buffer / Q\&A. **Audience:** technical, but the session is a **capability showcase**, not a how-it-works deep-dive. Goal: make builders think *"wait.. I can build THAT without running any servers?"*

---

## Where this fits in the W3S program

| Presenter | Layer |
| :---- | :---- |
| Anton | The Polkadot Triangle \- Mobile, Desktop, Web apps |
| Karim | dApps that run *inside* the triangle |
| **Torsten** | **The boundary**: TrUAPI, the triangle container, the host |
| **Adrian** | **What's behind the boundary**: the decentralized infrastructure dApps reach through TrUAPI |

---

## Through-line (the one sentence)

1. **(Provocative) What if your backend were private, unstoppable, and Sybil-proof..  and you never had to build or run any of it?**  
2. **(Explicit) Web2 ease, web3 guarantees: call one API, run no servers, and your users get privacy, censorship-resistance, and verified humanity for free.When you build on this platform, you inherit decentralized superpowers: private interactions, verified humanity, censorship-resistence; with no servers to run and no intermediaries to trust. All through one API.**

The slides serve that sentence. Won't explain how the primitives work, rather show what becomes *buildable*.

---

## Tone guardrails (technical-but-marketing)

- **Lead every primitive with the capability, not the architecture.** "Here's what you can build" before "here's how it works."  
- **Concrete impossible-becomes-possible beats superlatives.** Technical audiences gag on hype words; they light up at "P2P calls with no signaling server." Show the specific surprising thing.  
- **One mental-model slide per primitive, max.** Resist the urge to go deep, time is very limited and a deep-dive kills the energy.  
- **Credibility anchor:** these aren't slideware, they're reference implementations in the W3S open-source stack. Say it. It separates this from vaporware decks.  
- **The recurring drumbeat (for Adrian):** *"…and you run no servers to do this."* Repeat it across SSS, PoP, BC. It's the through-line that makes the whole platform click.

---

# Torsten's part

## Narrative arc

TODO

## Slide-by-slide (≈20 min)

TODO

# Adrian's part

## Narrative arc

1. **Handoff hook** \- "you've seen the apps, the dApps, the API; here's what's actually underneath"  
2. **The foundation** \- light-client-first; Smoldot is the trustless connection, now with native SSS \+ BC support  
3. **Three superpowers** \- SSS (private interactions), PoP (verified humanity), BC (censorship-resistant storage)  
4. **Put them together** \- one dApp, all three, zero servers  
5. **Go build** \- it's open source

(PoP part is flex, can drop or compress if needed, but makes sense in the narrative)

---

## Slide-by-slide (≈25 min)

### 1\. Handoff / Framing  *(\~1.5 min)*

- Pick up from Torsten: "Torsten showed you the door \- TrUAPI. Let me show you the rooms behind it."  
- The promise on one slide: **decentralized primitives · no servers · no trusted intermediaries · one API.**  
- Set expectation: "I'm not going to explain blockchains or smart contracts \- you know those. I'm showing you the *new* primitives this platform puts in your hands."

### 2\. Light-client-first: the trust backbone  *(\~2.5 min)*

- The platform doesn't phone home to a server. **Smoldot \- a light client running inside the app/browser \- IS the connection to Polkadot.**  
- New: **Smoldot now has native support for SSS and BC.** Your dApp reaches these primitives directly, trustlessly.  
- Why a builder should care: free from RPC providers to trust, rate-limit, or censor, or otherwise compromise your users’ experience. Decentralization built in, not an afterthought.  
- One-liner: *"Most 'web3' apps still trust one server to tell them the truth. Ours don't."*

### 3\. Three superpowers  *(\~0.5 min, agenda slide)*

- **Private interactions** → SSS  
- **Verified humanity** → Proof of Personhood  
- **Censorship-resistant storage** → Bulletin Chain  
- All exposed through TrUAPI. All trustless and verifiable via the light client.

### 4\. SSS, the promise  *(\~2 min)*

- **A decentralized private messaging & signaling protocol.**  
- The promise on one slide: **E2E encrypted, no metadata leakage, `(source, destination)` pair kept confidential, no centralized or trusted servers.**  
- Framing: *"It's your TCP for confidential, serverless app-to-app and user-to-user communication."*

### 5\. SSS, the mental model  *(\~1.5 min)*

- Keep it light: a generic **store-and-forward pub/sub** data store.  
- Topics are keys, statements are values. Subscriptions are topic-based. One statement → many topics.  
- Does not give *strong delivery guarantee* → but does provide *eventual delivery guarantee*.  
- (Not going into Kademlia/DHT internals. One visual, moving on.)  
- *"For a builder: you publish to a topic, interested parties subscribe. That's it."*  
- Chat is the obvious example \- **but the primitive powers *any* private interaction between users**, not just messaging.

### 6\. SSS, what you can build (the punch)  *(\~2 min)*

- Private chat (the obvious one) \- e2e encrypted, endpoints private, no central server(s)  
- *"But what about audio or video calls?"*  
- **WebRTC P2P calls with no signaling server** \- SSS carries the SDP offer/answer exchange; the centralized signaling server simply disappears.  
  - *(This is the killer visual: two browsers, SDP through the SSS cloud, then a direct WebRTC line, signaling server crossed out.)*  
- Private notifications, confidential coordination, presence \- any product surface that today needs a trusted backend.  
- Land it: *"Every one of these normally needs a server you operate and your users trust. Here, neither exists."*

### 7\. Proof of Personhood, the promise  *(\~1.5 min · FLEX)*

- **One person, one account \- cryptographically enforced. No invasive biometrics.**  
- Privacy-preserving verification → **per-domain aliases**: cross-app SSO with *no* cross-app tracking.  
- How it couples to SSS: personhood (via RingVRF ring membership proofs) is what *gates write access* \- you prove you're a unique human in the ring without revealing which one.  
- (talk about apps getting zk-proof/untraceable aliases that also guarantee they represent the account of unique human)

### 8\. PoP, what you can build  *(\~1.5 min · FLEX)*

- "Verified Human Only" features:  
  - Feeds immune to bot spam  
  - Marketplaces with real sellers  
  - Communities with genuine engagement  
- Land it: *"Sybil resistance and privacy usually pull in opposite directions. Here you get both."*

### 9\. Bulletin Chain, the promise  *(\~1.5 min)*

- **Decentralized storage for Polkadot.** Content-addressed (CIDs), censorship-resistant, retrievable via IPFS Bitswap \- no gateways, no centralized servers.  
- **Ephemeral by default, with renewal** \- intentional, managed storage, not "store everything forever." (Honest, and a differentiator vs. permanent-storage chains.)

### 10\. BC, what you can build  *(\~2.5 min)*

Real reference implementations (from W3S open-source stack), which makes it credible:

- **Static site / web-app hosting** → entire apps deployed to `.dot` domains via dot.li  
- **Identity evidence storage** → Proof-of-Ink media from People Chain via XCM  
- **Encrypted P2P file transfer** → chat attachments as AES-256-GCM encrypted HOP chunks  
- **App metadata \+ artwork** → Festival events, contract ABIs, collectible images  
- **Smart-contract-gated storage** → EVM contracts on Asset Hub authorizing users via XCM  
- **Governance records** \- proposal discussions, signaling votes, treasury reports as immutable, CID-referenced, censorship-resistant records \- *replacing today's reliance on Polkassembly or Google Docs.*

### 11\. Putting it together  *(\~1.5 min)*

- One dApp, all the primitives, zero servers. Example: a **decentralized marketplace**:  
  - Sellers are **verified humans** (PoP)  
  - Buyer↔seller **private chat** (SSS)  
  - Listing images \+ docs in **censorship-resistant storage** (BC)  
  - All reached **trustlessly via the light client** (Smoldot)  
  - All through **one API** (TrUAPI)  
- *"No backend. No infra team. No server bill. And more private and more censorship-resistant than the centralized version."*

### 12\. Go build  *(\~1 min)*

- This is under the hood. It's **open source**.  
- Where to start / repos / docs. One clear call to action.

