---

stand_alone: yes
pi:
  rfcedstyle: yes
  toc: yes
  tocindent: yes
  tocdepth: 4
  sortrefs: yes
  symrefs: yes
  strict: yes
  comments: yes
  inline: yes
  text-list-symbols: o-*+
  compact: yes
  subcompact: no

title: Secure Asset Transfer Protocol (SATP) Asset Exchange
abbrev: SATP Asset Exchange
docname: draft-marstein-satp-asset-exchange-latest
category: info

ipr: trust200902
area: "Applications and Real-Time"
workgroup: "Secure Asset Transfer Protocol"

stream: IETF
keyword: Internet-Draft
consensus: true

venue:
  group: "Secure Asset Transfer Protocol"
  type: "Working Group"
  mail: "sat@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/sat/"
  github: "ietf-satp/draft-marstein-satp-asset-exchange"
  latest: "https://ietf-satp.github.io/draft-marstein-satp-asset-exchange/draft-marstein-satp-asset-exchange.html"

author:
  -
    ins: K. Marstein
    name: Kjell-Erik Marstein
    organization: Cathmere
    email: kjell-erik@cathmere.com
  -
    ins: A. Chiriac
    name: Alex Chiriac
    organization: Quant Network
    email: alexandru.chiriac@quant.network
  -
    ins: L. Riley
    name: Luke Riley
    organization: Quant Network
    email: luke.riley@quant.network
  -
    ins: V. Ramakrishna
    name: Venkatraman Ramakrishna
    organization: IBM Research
    email: vramakr2@in.ibm.com

informative:
  Abebe19:
    author:
    - ins: E. Abebe
    - ins: D. Behl
    - ins: C. Govindarajan
    - ins: Y. Hu
    - ins: D. Karunamoorthy
    - ins: P. Novotny
    - ins: V. Pandit
    - ins: V. Ramakrishna
    - ins: C. Vecchiola
    date: December 2019
    target: https://arxiv.org/abs/1911.01064
    title: Enabling Enterprise Blockchain Interoperability with Trusted Data Transfer (Middleware 2019 - Industry Track)
  BVGC20:
    author:
    - ins: R. Belchior
    - ins: A. Vasconcelos
    - ins: S. Guerreiro
    - ins: M. Correia
    date: May 2020
    target: https://arxiv.org/abs/2005.14282v2
    title: 'A Survey on Blockchain Interoperability: Past, Present, and Future Trends'
  Clar88:
    author:
    - ins: D. Clark
    date: August 1988
    title: The Design Philosophy of the DARPA Internet Protocols, ACM Computer Communication Review, Proc SIGCOMM 88, vol. 18, no. 4, pp. 106-114
  HLP19:
    author:
    - ins: T. Hardjono
    - ins: A. Lipton
    - ins: A. Pentland
    date: June 2019
    target: https://doi:10.1109/TEM.2019.2920154
    title: Towards an Interoperability Architecture for Blockchain Autonomous Systems, IEEE Transactions on Engineering Management
  HS2019:
    author:
    - ins: T. Hardjono
    - ins: N. Smith
    date: December 2019
    target: https://doi.org/10.3389/fbloc.2019.00024
    title: Decentralized Trusted Computing Base for Blockchain Infrastructure Security, Frontiers Journal, Special Issue on Blockchain Technology, Vol. 2, No. 24
  HTLC21:
    author:
    date:
    target: https://en.bitcoin.it/wiki/Hash_Time_Locked_Contracts
    title: Hash Time Locked Contracts, Bitcoin Wiki
  SRC84:
    author:
    - ins: J. Saltzer
    - ins: D. Reed
    - ins: D. Clark
    date: November 1984
    title: End-to-End Arguments in System Design, ACM Transactions on Computer Systems, vol. 2, no. 4, pp. 277-288

normative:
  SAEP:
    author:
    - ins: K. Marstein
    - ins: P. Davita
    - ins: L. Riley
    date: June 2025
    target: https://doi.org/10.1109/ICBC64466.2025.11185062
    title: Adapting the Secure Asset Transfer Protocol for Secure Cross-Network Asset Exchange, IEEE ICBC Cross-Chain Workshop (ICBC-CCW)
  ISO:
    author:
    - ins: ISO
    date: July 2020
    target: https://www.iso.org/standard/82208.html
    title: Blockchain and distributed ledger technologies-Vocabulary (ISO:22739:2020)
  NIST:
    author:
    - ins: D. Yaga
    - ins: P. Mell
    - ins: N. Roby
    - ins: K. Scarfone
    date: October 2018
    target: https://doi.org/10.6028/NIST.IR.8202
    title: NIST Blockchain Technology Overview (NISTR-8202)
  MICA:
    author:
    - ins: European Commission
    date: June 2023
    target: https://www.esma.europa.eu/esmas-activities/digital-finance-and-innovation/markets-crypto-assets-regulation-mica
    title: EU Directive on Markets in Crypto-Assets Regulation (MiCA)
  SATA:
    author:
    - ins: T. Hardjono
    - ins: M. Hargreaves
    - ins: N. Smith
    - ins: V. Ramakrishna
    date: July 2025
    target: https://datatracker.ietf.org/doc/draft-ietf-satp-architecture/
    title: Secure Asset Transfer (SAT) Interoperability Architecture, IETF, draft-ietf-satp-architecture-08
  SATP:
    author:
    - ins: M. Hargreaves
    - ins: T. Hardjono
    - ins: R. Belchior
    - ins: V. Ramakrishna
    - ins: A. Chiriac
    date: August 2025
    target: https://datatracker.ietf.org/doc/draft-ietf-satp-core/
    title: Secure Asset Transfer Protocol (SATP) Core, IETF, draft-ietf-satp-core-11
  SATU:
    author:
    - ins: V. Ramakrishna
    - ins: T. Hardjono
    - ins: C. Liu
    date: July 2025
    target: https://datatracker.ietf.org/doc/draft-ietf-satp-usecases/
    title: Secure Asset Transfer (SAT) Use Cases, IETF, draft-ietf-satp-usecases-06

--- abstract

This document describes an extension of the Secure Asset Transfer Protocol (SATP) that enables the asset exchange interoperability mode.
It specifies the required modifications necessary to the SATP message flows to facilitate asset exchange between asset networks.
Gateways that support SATP can be extended to also support the asset exchange mode, enabling support for both asset transfer and asset exchange in a single set of gateways.

--- middle

# Introduction

{: #introduction-doc}

This document presents an extension of the Secure Asset Transfer (SAT) Protocol {{SATP}} that facilitates asset exchange between asset networks.
The asset exchange protocol is a mediated cross-authentication protocol for cross-network digital asset exchange.
SATP gateways can be extended to support the asset exchange mode, enabling support for both the asset transfer and asset exchange interoperability modes through a single set of gateways.
The reader is directed to {{SATA}} for further discussion of the interoperability modes recognized in SATP.

The protocol uses a lock-and-assign pattern to facilitate the asset exchange, where all assets included in the exchange are locked or otherwise disabled within their respective networks before being assigned to the designated beneficiaries.
This process is coordinated by peer gateways, where each gateway is connected to one of the digital asset networks involved in the exchange.
The lock-and-assign pattern is used to facilitate atomicity, consistency, isolation, and durability (ACID) in the cross-network exchange process.

The goal of this draft is to define an asset exchange protocol that builds upon the architectural and procedural foundations established in earlier SATP drafts ({{SATA}}, {{SATP}}).
Asset exchange as a core interoperability requirement is recognized in the SATP architecture {{SATA}}, and is, thus, a natural progression of the protocol.
The reader is directed to {{SATU}} for further discussion of the use cases enabled by the asset exchange version of SATP.

# Terminology

{: #terminology-doc}

The following are some terminology used in the current document. We borrow terminology from {{NIST}} and {{ISO}} where possible, introducing new terms only when needed:

- Digital asset: A digital representation of a value or of a right that can be transferred and stored electronically using distributed ledger technology or similar technology {{MICA}}.

- Asset network (system): The network or system where a digital asset is utilized.

- Secure Asset Transfer Protocol (SATP): The protocol used to transfer (move) a digital asset from one network to another using gateways.

- Asset transfer: A fail-safe process of moving an asset from one network to another, with the destruction of the asset in the origin network and its recreation in the destination network occurring as a single atomic action.

- Asset exchange: A fail-safe process of exchanging (or swapping) assets held by a pair of owners, each asset being maintained in a different network, with the two in-network transfers occurring as a single atomic action.

# Asset Exchange Extension

{: #asset-exchange-protocol}

## Overview

{: #asset-exchange-overview}

The SAT asset exchange extension protocol is a gateway-to-gateway protocol enabling cross-network digital asset exchange, first introduced in {{SAEP}}.
The protocol intends to have a low barrier of adoption in systems that already implement SATP by potentially being enabled through the same set of gateways.

This document presents the modifications necessary to the SATP message flows and to the asset network actions to support the asset exchange mode.
The asset exchange protocol inherits the SATP model and behavior where not otherwise stated.
The reader is directed to {{SATP}} for further discussion of SATP and non-modified behavior.

While several variations of the message flows can be used to support a gateway-to-gateway asset exchange protcol, a conscious design choice is to diverge as little as possible from the asset transfer version of SATP by reusing established definitions, semantics, and security guarantees where possible.
This allows the protocol to leverage the progress of SATP and simplifies integration with existing SATP compliant systems.

The gateway referred to as the "sender gateway" in SATP takes on the role as "initiating" gateway of the asset exchange, and the gateway referred to as the "recipient gateway" takes on the role as "receiving" gateway, referring to each gateway's role in initiating the exchange.
The protocol defines API endpoints, resources and identifier definitions, and message flows used in orchestrating the asset exchange between the two gateways.

## Stages of the Protocol

{: #asset-exchange-stages}

The asset exchange protocol follows the same three message stages as SATP:

- Transfer Initiation stage (Stage-1): The gateways come to an agreement of the set of parameters describing the proposed exchange. The gateway initiating the exchange delivers the initial proposal containing the set of parameters.

- Lock Assertion stage (Stage-2): The initiating gateway conveys a signed assertion to the receiving gateway, asserting the locked status of the asset in the network connected to the initiating gateway.

- Commitment Preparation and Finalization stage (Stage-3): The receiving gateway conveys a signed assertion to the initiating gateway, asserting the locked status in the network connected to the receiving gateway. The gateways finalize the exchange by assigning the assets to their beneficiaries, and convey signed assertions pertaining to the status of the assets in their respective networks to the counterparty gateway.

The interactions between the peer gateways prior to the initiation stage is referred to as the setup stage (Stage-0), which is outside the scope of the current specification of SATP.

## Message Types

{: #asset-exchange-message-types}

This refers to the type of request or response to be conveyed in the message.
The values are defined in {{SATP}}.

The possible values for an asset exchange session are:

- transfer-proposal-msg: The exchange proposal message sent by the gateway initiating the exchange. The message contains the set of parameters proposed for the exchange.

- proposal-receipt-msg: The signed receipt message indicating acceptance of the exchange proposal by the receiving gateway.

- reject-msg: The reject message sent from a gateway to another. The message contains an indication of the reason for the rejection.

- transfer-commence-msg: The exchange commence message sent by the gateway initiating the exchange, requesting to begin the commencement of the asset exchange.

- ack-commence-msg: Response to accept the commencement of the asset exchange.

- lock-assert-msg: The gateway has performed the locking of the asset in its network.

- assertion-receipt-msg: The receiving gateway acknowledges receiving the signed lock-assert-msg.

- commit-prepare-msg: The initiating gateway requests the start of the commitment stage.

- ack-prepare-msg: The receiving gateway acknowledges receiving the previous commit-prepare-msg and agrees to start the commitment stage.

- ack-commit-final-msg: The gateway has performed the asset assignment in its network.

- commit-transfer-complete-msg: The initiating gateway indicates closure of the current transfer session.

- error-msg: This message is used to indicate that an error has occured at the SATP layer. It can be transmitted by either gateway.

- session-abort-msg: This message is used by a gateway to abort the current session.

The reader is directed to {{SATP}} for further discussion of the message types.

# Modified Message Flows

{: #asset-exchange-flows}

The asset exchange protocol follows the same Stage-1 and Stage-2 message flows as {{SATP}}.

Stage-1 flows pertain to the initialization of the transfer session between the two gateways.

Stage-2 flows cover the conveyance of the signed assertion pertaining to the asset's locked status in network N1 connected to the initiating gateway G1.

If the signed assertion conveyed by gateway G1 in Stage-2 is accepted by gateway G2, it must in return initiate Stage-3 and transmit a signed receipt to gateway G1 that it has correctly locked the asset in network NW2 connected to gateway G2.

The remaining Stage-3 flows commit gateways G1 and G2 to assigning the locked assets to their respective benficiaries.
The initiating gateway G1 must assign (unlock) the asset in network NW1 to the correct benficiary in network NW1 and gateway G2 must assign (unlock) the asset in network NW2 to the correct beneficiary in network NW2.

```
       App1  NW1          G1                     G2          NW2    App2
      ..|.....|............|......................|............|.....|..
        |     |            |       Stage 1        |            |     |
        |     |            |                      |            |     |
        |     |       (1.1)|--Transf. Proposal -->|            |     |
        |     |            |                      |            |     |
        |     |            |<--Proposal Receipt---|(1.2)       |     |
        |     |            |                      |            |     |
        |     |       (1.3)|---Transf. Commence-->|            |     |
        |     |            |                      |            |     |
        |     |            |<----ACK Commence-----|(1.4)       |     |
        |     |            |                      |            |     |
      ..|.....|............|......................|............|.....|..
        |     |            |       Stage 2        |            |     |
        |     |            |                      |            |     |
        |     |<---Lock----|(2.1)                 |            |     |
        |     |            |                      |            |     |
        |     |       (2.2)|----Lock-Assertion--->|            |     |
        |     |            |                      |            |     |
        |     |            |                 (2.3)|--Record--->|     |
        |     |            |                      |            |     |
        |     |            |<--Assertion Receipt--|(2.4)       |     |
        |     |            |                      |            |     |
      ..|.....|............|......................|............|.....|..
        |     |            |       Stage 3        |            |     |
        |     |            |                      |            |     |
        |     |       (3.1)|----Commit Prepare--->|            |     |
        |     |            |                      |            |     |
        |     |            |                 (3.2)|----Lock--->|     |
        |     |            |                      |            |     |
        |     |            |<----Commit Ready-----|(3.3)       |     |
        |     |            |                      |            |     |
        |     |<--Assign---|(3.4)                 |            |     |
        |     |            |                      |            |     |
        |     |       (3.5)|-----Commit Final---->|            |     |
        |     |            |                      |            |     |
        |     |            |                 (3.6)|---Assign-->|     |
        |     |            |                      |            |     |
        |     |            |<-----ACK Final-------|(3.7)       |     |
        |     |            |                      |            |     |
        |     |            |                      |            |     |
        |     |<--Record---|(3.8)                 |            |     |
        |     |            |                      |            |     |
        |     |       (3.9)|--Transfer Complete-->|            |     |
      ..|.....|............|......................|............|.....|..
                                Figure 2
```

## Transfer Initiation Stage (Stage 1)

{: #asset-exchange-stage1}

This section describes the transfer initiation stage, where the initiating gateway and the receiving gateway prepare for the start of the asset exchange.

The initiating gateway proposes the set of transfer parameters and asset-related artifacts for the exchange to the receiving gateway.
The parameters are contained in the Transfer Initiation Claim.

The asset exchange protocol requires two Transfer Initiation Claims, one for each asset involved in the exchange.
The inclusion of two Transfer Initiation Claims in the proposal signals to the receiving gateway that the session should be conducted using the asset exchange version of SATP.

The reader is directed to {{SATP}} for further discussion of Stage-1.

## Lock Assertion Stage (Stage 2)

{: #asset-exchange-stage2}

The messages in this stage pertain to the initiating gateway providing the receiving gateway with a signed assertion that the asset in network NW1 has been locked or disabled, and under the control of the initiating gateway.

The reader is directed to {{SATP}} for further discussion of Stage-2.

## Commitment Preparation and Finalization (Stage 3)

{: #asset-exchange-stage3}
This section describes the exchange commitment agreement between the client (initiating gateway) and the server (receiving gateway).

This stage must be completed within the time specified in the lockAssertionExpiration value in the lock-assertion or commit ready message, whichever is shortest.

The reader is directed to {{SATP}} for further discussion of required HTTP endpoints, methods, request parameter serialization, and digital signatures for this message.

### Commit Preparation Message (Commit-Prepare)

{: #asset-exchange-commit-preparation-message}
The purpose of this message is for the client to indicate its readiness to begin the commitment of the exchange.
In response to this message, the receiving gateway must lock or otherwise disable the asset in network NW2.

The reader is directed to {{SATP}} for further discussion of the Commit Preparation Message.

### Commit Ready Message (Commit-Ready)

{: #asset-exchange-commit-ready}
The purpose of this message is for the server to indicate to the client that the server has locked or otherwise disabled the asset in network NW2 and that the server is ready to proceed to the next step.
In response to this message, the initiating gateway can perform the assignment of the asset in network NW1 to its designated benficiary.

This message is sent from the server to the Commit Ready Endpoint at the client.

The message must be signed by the server.

The asset exchange extension requires the message transmitted in this step to be formatted as a lock-assert-msg instead of following the commit-ready-msg format specified for this step in the asset transfer version of SATP.

The parameters of this message consist of the following:

- messageType REQUIRED. It MUST be the value urn:ietf:satp:msgtype:lock-assert-msg.

- sessionId REQUIRED: A unique identifier chosen earlier by client in the Initialization Request Message.

- transferContextId REQUIRED: A unique identifier used to identify the current exchange session at the application layer.

- hashPrevMessage REQUIRED. The hash of the previous message.

- lockAssertionClaim REQUIRED. The lock assertion claim or statement by the server.

- lockAssertionClaimFormat REQUIRED. The format of the claim.

- lockAssertionExpiration REQUIRED. The duration of time of the lock or escrow upon the asset.

Example:

{\
  "messageType": "urn:ietf:satp:msgtype:lock-assert-msg",\
  "sessionId": "d66a567c-11f2-4729-a0e9-17ce1faf47c1",\
  "transferContextId": "89e04e71-bba2-4363-933c-262f42ec07a0",\
  "hashPrevMessage": "8dcc8dc4e6c2c979474b42d24d3747ce4607a92637d1a7b294857ff7288b8e46",\
  "lockAssertionClaim": {},\
  "lockAssertionClaimFormat": "LOCK_ASSERTION_CLAIM_FORMAT_1",\
  "lockAssertionExpiration": "2024-12-23T23:59:59.999Z",\
}\

### Commit Final Assertion Message (Commit-Final)

{: #asset-exchange-commit-final-message}

The purpose of this message is for the client to indicate to the server that the client (initiating gateway) has completed the assignment of the asset in network NW1.

The message must contain a standalone claim related to the assignment of the asset by the client.
The standalone claim must be signed by the client.

This message is sent from the client to the Commit Final Assertion Endpoint at the server.

The message must be signed by the client.

The asset exchange extension requires the message transmitted in this step to be formatted as an ack-commit-final-msg instead of following the commit-final-msg format specified for this step in the asset transfer version of SATP.

The parameters of this message consist of the following:

- messageType REQUIRED. It MUST be the value urn:ietf:satp:msgtype:ack-commit-final-msg.

- sessionId REQUIRED: A unique identifier chosen earlier by the client in the Initialization Request Message.

- transferContextId REQUIRED: A unique identifier used to identify the current exchange session at the application layer.

- hashPrevMessage REQUIRED. The hash of the previous message.

- assignmentAssertionClaim REQUIRED. The claim or statement by the client that the asset has been assigned by the client to the intended beneficiary.

- assignmentAssertionClaimFormat REQUIRED. The format of the claim.

Example:

{\
  "messageType": "urn:ietf:satp:msgtype:ack-commit-final-msg",\
  "sessionId": "d66a567c-11f2-4729-a0e9-17ce1faf47c1",\
  "transferContextId": "89e04e71-bba2-4363-933c-262f42ec07a0",\
  "hashPrevMessage": "b92f13007216c58f2b51a8621599c3aef6527b02c8284e90c6a54a181d898e02",\
  "assignmentAssertionClaim": {},\
  "assignmentAssertionClaimFormat": "ASSIGNMENT_ASSERTION_CLAIM_FORMAT_1",\
}\

### Commit-Final Acknowledgement Receipt Message (ACK-Final-Receipt)

{: #asset-exchange-final-ack}

The purpose of this message is to indicate to the client that the server has completed the assignment of the asset to the intended beneficiary in network NW2.

The reader is directed to {{SATP}} for further discussion of the Commit-Final Acknowledgement Receipt Message.

### Transfer Complete Message

{: #asset-exchange-transfer-complete-message}

The purpose of this message is for the client to indicate to the server that the asset exchange session (identified by sessionId) has been completed and no further messages are to be expected from the client in regards to this transfer instance.

The reader is directed to {{SATP}} for further discussion of the Transfer Complete Message.

## Error Messages

The reader is directed to {{SATP}} for further discussion of error messages.

# Security Considerations

{: #asset-exchange-security-considerations}

The reader is directed to {{SATP}} for further discussion of security considerations.

# IANA Considerations

{: #asset-exchange-iana-considerations}

This document has no IANA actions.

--- back
