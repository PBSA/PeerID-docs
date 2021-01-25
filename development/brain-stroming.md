# Brain Storming

## Brain Stroming

## Identity Provider - Brainstroming

Created by \[Bobinson Bobby\]

| **Facilitator** | @Bobinson Bobby |
| :--- | :--- |
| **Participants** | @Prabhjot Singh @Satyanarayana Koneru |
| **Brainstorm date** | Jun 11, 2020 |
| **Video conference link** |  |
| **On this page** | [ Brainstorm planning](https://peerplays.atlassian.net/wiki/spaces/PROJECTS/pages/829718557/Identity+Provider+-+Brainstroming#⏳-Brainstorm-planning)[ Brainstorm pre-work & ideas](https://peerplays.atlassian.net/wiki/spaces/PROJECTS/pages/829718557/Identity+Provider+-+Brainstroming#🌱-Brainstorm-pre-work-&-ideas)[In the context of SSO few items we are trying to do is:](https://peerplays.atlassian.net/wiki/spaces/PROJECTS/pages/829718557/Identity+Provider+-+Brainstroming#In-the-context-of-SSO-few-items-we-are-trying-to-do-is:)[The wallet](https://peerplays.atlassian.net/wiki/spaces/PROJECTS/pages/829718557/Identity+Provider+-+Brainstroming#The-wallet[hardBreak])[ Brainstorm outcomes](https://peerplays.atlassian.net/wiki/spaces/PROJECTS/pages/829718557/Identity+Provider+-+Brainstroming#🎯-Brainstorm-outcomes) |

### Brainstorm planning

| **Goals of the brainstorm** | Finalize the requirements for the Identify provider |
| :--- | :--- |
| **Participant instructions** | Compare existing Identity / SSO providers |

### Brainstorm pre-work & ideas

SSO document prepared by @Prabhjot Singh in 2019

HiveSigner

Scatter

Study Reference Architectures for dApps

Problem Statement

One of the challenges everyone in the blockchain is agreeing and facing is the lack of standards for signin, interaction with between wallets, an SSO mechanism similar to OpenID \(Janrain version\) which later got extended to Oauth. Needless to say, the blockchain space doesn't even have something similar to a simple gravtar system.

#### In the context of SSO few items we are trying to do is:

1. For a user with Twitch/Facebook account, it should be easy to signup for a Peerplays account
2. Once a user owns say, EOS or Bitcoins, she should be able to easily signup or use Peerplays without going through the entire cycle of account creation etc.
3. Our target market uses additional apps like STEAM, Discord & Youtube Gaming \(& there could be betting related apps\).

The objective of the SSO is to provide a simpler mass on boarding mechanism for people with or without blockchain accounts to start participating in various public blockchains. Such an SSO service like Bitpass can have massive impact on the blockchains. Graphene based chains \(Bitshares, SCORUM, STEEM & EOS\), Bitcoin & Etherium should be considered as our target blockchains. While storing private keys and "Brain Keys" should not be allowed, we can store Tokens like JWT with an expiry against private keys and store them in a secure database. The database will be encrypted at store and in transit using TLS to ensure safety. In a nutshell we can store mapping between a private key derived Time & URL bound unique tokens & various services.

Further use cases : KYC similar to[ Passport from Telegram](https://core.telegram.org/passport/), create discord bots, Telegram bots, Access Twitch widgets

#### The wallet

Similar to the chains and services there is also a challenge with numerous wallet implementations and no clear, unified mechanism for the dApps to interact with wallets. In the case of lesser known blockchain projects its important to get noticed by Software Wallets like Exodus and hardware wallets like Ledger. We would essentially expose a mechanism for the wallets and dApps to integrate with us and also act as signature providers.

The transit API is such an example.

[https://medium.com/eos-new-york/the-transit-api-connecting-dapps-signature-providers-5d816c056f7f](https://medium.com/eos-new-york/the-transit-api-connecting-dapps-signature-providers-5d816c056f7f)

Along with the wallet, if we can also consider an extention of Transit API for Peerplays, that will be a great achievement.

The combination of SSO and wallet implementation with Transit API like interface will help us to on board "masses" & safely interact with Peerplays via various dApps.

Thoughts and ideas welcome!

### Brainstorm outcomes

1. In a large dApp like [peaked.com](http://peaked.com) or [StreamersEdge.com](http://StreamersEdge.com) an identity provider which can help end users sign transactions is helpful to isolate the authentication and authorization functionalities from the application business logic
2. We will have to provide easy account creation using existing social accounts like Facebook, Twitter etc as opposed to be expecting users to be blockchain savvy. This would mean that the identity provider component should store the MASTER\_PASSWORD or the generated keys and lease to the dApps as when needed.

