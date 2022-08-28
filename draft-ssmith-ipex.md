---
title: "Issuance and Presentation Exchange Protocol"
abbrev: "IPEX"
category: info

docname: draft-ssmith-ipex-latest
v: 3
area: AREA
workgroup: WG Working Group
keyword: Internet-Draft
venue:
  group: WG
  type: Working Group
  mail: WG@example.com
  arch: https://example.com/WG
  github: USER/REPO
  latest: https://example.com/LATEST

author:
 -
    fullname: Samuel M. Smith
    organization: ProSapien LLC
    email: "sam@prosapien.com"
 -
    name: Phil Feairheller
    organization: GLEIF
    email: Philip.Feairheller@gleif.org


normative:

  IPEX-ID:
    target: https://github.com/WebOfTrust/ietf-oobi
    title: IETF IPEX (Issuance and Presentation EXchange) Prototocol Internet Draft
    author:
      -
        ins: S. Smith
        name: Samuel M. Smith
        org: ProSapien LLC
      -
        name: Phil Feairheller
        organization: GLEIF
        email: Philip.Feairheller@gleif.org
    date: 2022

  ACDC-ID:
    target: https://github.com/trustoverip/tswg-acdc-specification
    title: IETF ACDC (Authentic Chained Data Containers) Internet Draft
    author:
      ins: S. Smith
      name: Samuel M. Smith
      org: ProSapien LLC
    date: 2022

  OOBI-ID:
    target: https://github.com/WebOfTrust/ietf-oobi
    title: IETF OOBI (Out-Of-Band-Introduction) Internet Draft
    author:
      ins: S. Smith
      name: Samuel M. Smith
      org: ProSapien LLC
    date: 2022

  KERI-ID:
    target: https://github.com/WebOfTrust/ietf-keri
    title: IETF KERI (Key Event Receipt Infrastructure) Internet Draft
    author:
      ins: S. Smith
      name: Samuel M. Smith
      org: ProSapien LLC
    date: 2022

 SAID-ID:
    target: https://github.com/WebOfTrust/ietf-said
    title: IETF SAID (Self-Addressing IDentifier) Internet Draft
    author:
      ins: S. Smith
      name: Samuel M. Smith
      org: ProSapien LLC
    date: 2022

  CESR-ID:
    target: https://github.com/WebOfTrust/ietf-cesr
    title: IETF CESR (Composable Event Streaming Representation) Internet Draft
    author:
      ins: S. Smith
      name: Samuel M. Smith
      org: ProSapien LLC
    date: 2022

  PTEL-ID:
    target: https://github.com/WebOfTrust/ietf-ptel
    title: IETF PTEL (Public Transaction Event Log) Internet Draft
    author:
      ins: P. Feairheller
      name: Phil Feairheller
      org: GLEIF
    date: 2022

  Proof-ID:
    target: https://github.com/WebOfTrust/ietf-cesr-proof
    title: IETF CESR-Proof Internet Draft
    author:
      ins: P. Feairheller
      name: Phil Feairheller
      org: GLEIF
    date: 2022

  DIDK-ID:
    target: https://github.com/WebOfTrust/ietf-did-keri
    title: IETF DID-KERI Internet Draft
    author:
      ins: P. Feairheller
      name: Phil Feairheller
      org: GLEIF
    date: 2022

  JSON:
    target: https://www.json.org/json-en.html
    title: JavaScript Object Notation Delimeters

  RFC8259:
    target: https://datatracker.ietf.org/doc/html/rfc8259
    title: JSON (JavaScript Object Notation)

  RFC4627:
    target: https://datatracker.ietf.org/doc/rfc4627/
    title: The application/json Media Type for JavaScript Object Notation (JSON)

  CBOR:
    target: https://en.wikipedia.org/wiki/CBOR
    title: CBOR Mapping Object Codes

  RFC8949:
    target: https://datatracker.ietf.org/doc/rfc8949/
    title: Concise Binary Object Representation (CBOR)
    author:
      -
        ins: C. Bormann
        name: Carsten Bormann
      -
        ins: P. Hoffman
        name: Paul Hoffman
    date: 2020-12-04

  MGPK:
    target: https://github.com/msgpack/msgpack/blob/master/spec.md
    title: Msgpack Mapping Object Codes

  JSch:
    target: https://json-schema.org
    title: JSON Schema

  JSch_202012:
    target: https://json-schema.org/draft/2020-12/release-notes.html
    title: "JSON Schema 2020-12"


informative:

  KERI:
    target: https://arxiv.org/abs/1907.02143
    title: Key Event Receipt Infrastructure (KERI)
    author:
      ins: S. Smith
      name: Samuel M. Smith
      org: ProSapien LLC
    date: 2021

  IDSys:
    target: https://github.com/SmithSamuelM/Papers/blob/master/whitepapers/Identity-System-Essentials.pdf
    title: Identity System Essentials


  RC:
    target: https://en.wikipedia.org/wiki/Ricardian_contract
    title: Ricardian Contract

  CLC:
    target: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2045818
    title: "Chain-Link Confidentiality"


--- abstract

The Issuance and Presentation Exchange (IPEX) Protocol provides a uniform mechanism
for the issuance and presentation of ACDCs {{ACDC-ID}} in a securely attributable manner.
A single protocol is able to work for both types of exchanges by recognizing
that all exchanges (both issuance and presentation) may be modeled as the
disclosure of information by a Discloser to a Disclosee. The difference between
exchange types is the information disclosed not the mechanism for disclosure.
Furthermore, the chaining mechanism of ACDCs and support for both targeted and
untargeted ACDCs provide sufficient variability to accommodate the differences
in applications or use cases without requiring a difference in the exchange
protocol itself. This greatly simplifies the exchange protocol. This simplification
has two primary advantages. The first is enhanced security. A well-delimited
protocol can be designed and analyzed to minimize and mitigate attack mechanisms.
The second is convenience. A standard simple protocol is easier to implement,
support, update, understand, and adopt. The tooling is more consistent.

This IPEX {{IPEX-ID}} protocol leverages important features of ACDCs and ancillary protocols such as CESR {{CESR-ID}}, SAIDs {{SAID_ID}}, and CESR-Proofs {{Proof-ID}} as well as Ricardian contracts {{RC}} and graduated disclosure (partial, selective, full) to enable contractually protected disclosure. Contractually protected disclosure includes both chain-link confidential {{CLC}} and contingent disclosure {{ACDC-ID}}.



--- middle

# Introduction

TODO Introduction

# Terminology

*Presentation Exchange*
: a disclosure of one or more ***issuances**** between a ***Discloser**** and a ***Disclosee****.

*Discloser*
: Disclosure is *disclosed by* the *Discloser*.

*Disclosee*
: Disclosure is *disclosed to* the *Disclosee*.


*Issuance*
: Concretely defined by an ACDC {ACDC-ID}.

*Issuer*
: Issuance is *issued by* the *Issuer*. The *Issuer* identifier (AID) appears in the top level of the ACDC.

*Issuee*
: Issuance is *issued to* the *Issuee*. The *Issuee* identifier (AID) when present appears at the top level of the attribute section or in the attribute list at the top level of the attribute aggregate section of the AID.

Each *issuance* Must have an *Issuer* and May have an *Issuee*.

The set of *issuances* (ACDCs) so disclosed in a *presentation exchange* MUST be chained. This set of chained *issuances* define a directed acyclic graph (DAG) that MUST have at least one vertex and MAY have zero or more edges pointing to other vertices.

Each *issuance* (ACDC) itself defines a graph fragment consisting of one vertex and zero or more directed edges. Each directed edge contained in an *issuance* points to a vertex contained in another *issuance*. The *issuance* that contains the origin vertex of the DAG is called the *origin* or *primary* *issuance* (ACDC) of the *presentation exchange*.

The disclosure performed by a presentation exchange MAY be *graduated* and MAY be *contractually protected*.

*Issuance Exchange*
: A special case of a *presentation exchange* where the *Discloser* is the *Issuer* of the *origin* (Primary) *issuance* (ACDC) of the DAG formed by the set of chained *issuances* so disclosed.

In an *issuance exchange*, when the *origin issuance* has an *Issuee*, the *Disclosee* MAY also be the *origin issuance's* *Issuee*.


## Chain-Link Confidentiality

Disclosures via Presentations Exchanges may be contractually protected by Chain-Link Confidentiality (i.e a Chain-Link Confidential disclosure). The chaining in this case is different from the chaining described above between Issuances in a DAG of chained Issuances. Chain-link confidentiality, in contrast, chains together a sequence of Disclosees. Each Disclosee in the sequence in turn is the Discloser to the next Disclosee. The terms-of-use of the original disclosure as applied to the original Disclosee MUST be applied by each subsequent Discloser to each subsequent Disclosee via each of the subsequent disclosures (presentation exchanges). These terms-of-use typically constrain disclosure to only approved parties, i.e. imbue the chain of disclosures with some degree of confidentiality. These terms-of-use are meant to contractually protect the data rights of the original Issuer or Issuee of the data being disclosed.



# Exchange Protocol

| Discloser | Disclosee | Initiate | Contents |  Description |
|:-:|:-:|:-:|:--|:--|
| | `apply`| Y | schema or its SAID, attribute field label list, signature on `apply` or its SAID | schema SAID is type of ACDC, optional label list for selective disclosure, CESR-Proof signature|
|`spurn`|  | N | |rejects `apply` |
|`offer`|  | Y | metadata ACDC or its SAID, signature on `offer` or its SAID  | includes schema or its SAID, other partial disclosures, selective disclosure label list, CESR-Proof signature |
| | `spurn` | N | |rejects `offer` |
| | `agree`| N | signature on `offer` or its SAID | CESR-Proof signature |
|`spurn`|  | N | |rejects `agree` |
|`grant`|  | Y | full or selective disclosure ACDC, signature on `grant` or its SAID  | includes attribute values, CESR-Proof signature |
|| `admit` | N | signature on `grant` or its SAID  | CESR-Proof signature |



## Discussion

All the variants of an ACDC are various degrees of expansion of the compact variant. Therefore, an Issuer commitment via a signature to any variant of ACDC (compact, full, etc)  makes a cryptographic commitment to the top-level section fields shared by all variants of that ACDC because the value of a top level section field is either the SAD or the SAID of the SAD of the associated section. Both a SAD and its SAID, when signed, each provide a verifiable commitment to the SAD. In the former the signature verification is directly agains the SAD itself. In the latter, the SAID as digest must first be verified against its SAD and then the signature on the SAID may be verified. This indirect verifiablity assumes that the cryptographic strength of the SAID digest is equivalent to the cryptographic strength of the signature used to sign it. To clarify, because all variants share the same top level structure as the compact variant, then a signature on any variant  may be used to verify the Issuer's committment to any other variant either directly or indirectly, in whole or in part on a top-level section by top-level section basis. This cross-variant Issuer commitment verifiability is an essential property that supports graduated disclosure by the Disclosee of any or all variants wether it be full, compact, metadata, partial, selective, bulk issued, or contractually protected.

To elaborate, the SAID of a given variant is useful even when it is not the SAID of the variant the Issuer signed because during graduated disclosure the Discloser MAY choose to sign that given variant to fullfill a given step in an IPEX graduated disclosure transaction. The Discloser thereby can make a verifiable disclosure in a given step of the SAD of a given variant that fulfills a commitment made in a prior step via its signature on merely the SAID of the SAD of the variant so disclosed.

For example, the Metadata variant of an ACDC will have a different SAID than the Compact variant because some of the top-level field values may be empty in the Metadata variant. One can think of the The metadata variant as a partial manifest that only includes those top level sections that the Discloser is committing to disclose in order to induce the Disclosee to agree to the contractual terms of use when disclosed. The IPEX transaction is between the Discloser and Disclosee, who both may make non-repudiable commitments via signing to each other. Typically this means that the Discloser will eventually need to fulfull its commitment with a proof of disclosure to the Disclosee. This proof may be satisfied with either directly against the Discloser's signature on the the actual disclosed SAD or indirectly agaisnt the Discloser's signature on the SAID of the actual disclosed SAD. In addition, the Disclosee will typically require a proof of issuance via a non-repudiable signature by the Issuer on a variant of the disclosed SAD that is verifiable (directly or indirectly) against the variant that is the disclosed SAD.

To summarize, when the Issuer commits to the composed schema of an ACDC it is committing to all the variants so composed. As described above, the top level field values in the compact variant enable verification against a disclosure of any of the other Issuer committed variants because they all share the same top level structure. This applies even to the metadata variant in spite of it only providing values for some top level sections and not others. The verifiablity of a top level section is separable.

Consequently, the IPEX protocol must specify how a validator does validation of any variant in a graduated disclosure. To restate there are two proofs that a Discloser must provide. The first is proof of issuance and the second is proof of disclosure. In the former, the Discloser provide the variant via its SAD that was actually signed (as SAD or SAID of SAD) by the Issuer in order for the Disclosee to verify authentic issuance via the signature on that variant.  In the latter, the Discloser must disclose any other Issuer enabled (via schema composition) variants that the Discloser offered to disclose as part of the graduated disclosure process.

## IPEX Validation

The goal is to define a validation process (set of rules) that works for all variants of an ACDC and for all types of graduated disclosure of that ACDC.

For example, in the bulk issuance of an ACDC, the Issuer only signs the blinded SAID of the SAD that is the Compact variant of the ACDC not the SAD itself. This enable a Discloser to make a proof of inclusion of the ACDC in a bulk issuance set by unblinding the signature on the blinded SAID without leaking correlation to anything but the blinded SAID itself. To clarify, the Disclosee can verify the signature on the SAID without to prove set inclusion with needing the disclosure of any other information about the ACDC. Issuer signing of the SAID not the SAD also has the side benefit of minimizing the computation of large numbers of bulk issued signatures.

### Issuer Signing Rules

The Issuer MUST provide a signature on the SAID of the most compact form defined by the schema of the ACDC . To restate, when only one variant of the ACDC is defined by the schema, that variant is therefore by defintion the most compact variant.

When more than one variant is defined by the schema via the oneOf composition operator, the most compact variant MUST appear as the first entry in the oneOf list.

An iIssuer MAY provide signatures of the SAIDS of other variants, as well as signatures of the SADs of other variants.

Proof of issuance is provided by disclosing the SAID of the most compact variant and the signature by the Issuer on that SAID.

Proof of disclosure is provided by disclosing the SAD of the most compact variant and then recursively disclosing the nested SADs of each of the top level sections of the most compact variant as needed for the promised disclosure.

Thus for any disclosed variant of an ACDC, the Disclosee need only verify only one proof of issuance as defined above and may need to verify a different proof of disclosure for each disclosed variant as defined above.




# Conventions and Definitions

{::boilerplate bcp14-tagged}


# Security Considerations

TODO Security


# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
