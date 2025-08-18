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

title: Secure Asset Exchange Protocol
abbrev: SAT Asset Exchange
docname: draft-ietf-satp-asset-exchange-latest
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
  github: "ietf-satp/draft-ietf-satp-asset-exchange"
  latest: "https://ietf-satp.github.io/draft-ietf-satp-asset-exchange/draft-ietf-satp-asset-exchange.html"

author:
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
    ins: K. Marstein
    name: Kjell-Erik Marstein
    organization: INATBA
    email: kjellerik.marstein@gmail.com
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
  SAEP25:
    author:
    - ins: Kjell-Erik Marstein
    - ins: Paulina Davita
    - ins: Luke Riley
    date: June 2025
    target: https://www.techrxiv.org/users/689823/articles/1240676-adapting-the-secure-asset-transfer-protocol-for-secure-cross-network-asset-exchange
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

This document describes the Secure Asset Exchange Protocol (SAEP). SAEP is a protocol operating between two gateways that coordinate the atomic exchange of digital assets in two different asset networks.

--- middle

# Introduction

{: #introduction-doc}

TBD: Introduce the asset exchange protocol as a core requirement for interoperability between asset networks, primarily blockchains and DLTs, and as a natural extension to the SATP. Cite the earlier SATP drafts for reference {{SATA}} {{SATP}} {{SATU}}.

# Terminology

{: #terminology-doc}

The following are some terminology used in the current document. We borrow terminology from {{NIST}} and {{ISO}} as much as possible, introducing new terms only when needed:

- Asset network (system): The network or system where a digital asset is utilized.

- Secure Asset Transfer Protocol (SATP): The protocol used to transfer (move) a digital asset from one network to another using gateways.

- Origin network: The current network where the digital asset is located.

- Destination network: The network to which a digital asset is to be transferred.

- Data sharing: The process, using the Asset Transfer Protocol, by which one or more units of verifiably authentic data are communicated from an Origin network to a Destination network, either voluntarily or upon request.

- Asset Transfer: A fail-safe process of moving an asset from one network to another, with the destruction of the asset in the Origin network and its recreation in the Destination network occurring as a single atomic action.

- Asset Exchange: A fail-safe process of exchanging (or swapping) assets held by a pair of owners, each asset being maintained in a different network, with the two in-network transfers occurring as a single atomic action.

# Security Considerations

{: #saep-security-considerations}

TBD: List security considerations, if any.

# IANA Considerations

{: #saep-iana-considerations}

TBD: Does this document require any IANA actions?


--- back
