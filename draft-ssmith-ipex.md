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

  IPEX_ID:
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

  ACDC_ID:
    target: https://github.com/trustoverip/tswg-acdc-specification
    title: IETF ACDC (Authentic Chained Data Containers) Internet Draft
    author:
      ins: S. Smith
      name: Samuel M. Smith
      org: ProSapien LLC
    date: 2022

  OOBI_ID:
    target: https://github.com/WebOfTrust/ietf-oobi
    title: IETF OOBI (Out-Of-Band-Introduction) Internet Draft
    author:
      ins: S. Smith
      name: Samuel M. Smith
      org: ProSapien LLC
    date: 2022

  KERI_ID:
    target: https://github.com/WebOfTrust/ietf-keri
    title: IETF KERI (Key Event Receipt Infrastructure) Internet Draft
    author:
      ins: S. Smith
      name: Samuel M. Smith
      org: ProSapien LLC
    date: 2022
    
  SAID_ID:
    target: https://github.com/WebOfTrust/ietf-said
    title: IETF SAID (Self-Addressing IDentifier) Internet Draft
    author:
      ins: S. Smith
      name: Samuel M. Smith
      org: ProSapien LLC
    date: 2022
    
  CESR_ID:
    target: https://github.com/WebOfTrust/ietf-cesr
    title: IETF CESR (Composable Event Streaming Representation) Internet Draft
    author:
      ins: S. Smith
      name: Samuel M. Smith
      org: ProSapien LLC
    date: 2022
    
  PTEL_ID:
    target: https://github.com/WebOfTrust/ietf-ptel
    title: IETF PTEL (Public Transaction Event Log) Internet Draft
    author:
      ins: P. Feairheller
      name: Phil Feairheller
      org: GLEIF
    date: 2022
    
  Proof_ID:
    target: https://github.com/WebOfTrust/ietf-cesr-proof
    title: IETF CESR-Proof Internet Draft
    author:
      ins: P. Feairheller
      name: Phil Feairheller
      org: GLEIF
    date: 2022

  DIDK_ID:
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

The Issuance and Presentation Exchange (IPEX) Protocol provides a uniform mechanism for the issuance and presentation of ACDCs {{ACDC_ID}} in a securely attributable manner. A single protocol is able to work for both types of exchanges by recognizing that all exchanges (both issuance and presentation) may be modeled as the disclosure of information by a Discloser to a Disclosee. The difference between exchange types is the information disclosed not the mechanism for disclosure. Furthermore, the chaining mechanism of ACDCs and support for both targeted and untargeted ACDCs provide sufficient variability to accommodate the differences in applications or use cases without requiring a difference in the exchange protocol itself. This greatly simplifies the exchange protocol. This simplification has two primary advantages. The first is enhanced security. A well-delimited protocol can be designed and analyzed to minimize and mitigate attack mechanisms. The second is convenience. A standard simple protocol is easier to implement, support, update, understand, and adopt. The tooling is more consistent. 

This IPEX {{IPEX_ID}} protocol leverages important features of ACDCs and ancillary protocols such as CESR {{CESR_ID}}, SAIDs {{SAID_ID}}, and CESR-Proofs {{Proof_ID}} as well as Ricardian contracts {{RC}} and graduated disclosure (partial, selective, full) to enable contractually protected disclosure. Contractually protected disclosure includes both chain-link confidential {{CLC}} and contingent disclosure {{ACDC_ID}}.



--- middle

# Introduction

TODO Introduction



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
