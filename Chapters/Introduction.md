---
title: Introduction
slug: egAR-introduction
createdAt: 2024-07-21T15:06:55.414Z
updatedAt: 2024-07-21T15:56:27.203Z
---

In an information exchange use-case patient (medical) information can be considered to have a “medical home”. This medical home is often represented by a clinical information or HIE system that allows for exchange of the information it is responsible for. One or more “medical homes” can form a “home community”. A home community is often managed by an HIE organization (Dutch: RSO) or by a healthcare organization itself. When one or more “home communities” need to share information, they need to do so according to an agreed upon “cross-community governance” (Dutch: afsprakenstelsel) that defines the “rules of engagement”.

![](https://lh7-eu.googleusercontent.com/docsz/AD_4nXci6swdAYDFdQ5YGwwg0nNUlv62x8yd0_64x8Xa9wxgN5H5OEh0ryQ3axNaJbAFhfSR9fABshWLP7o-zqMB0SVx5Ud-5cxKf3zQlJdHlCXTU0oYk0GXfwOeR-RWtyA4scxQk7wx58C26vG4LC9ZnCdzlx4?key=tvhHE0qAQDmv6Dp7rQX5vw)

This document is about the technical agreements that are part of this governance for home communities that participate in the Dutch National HIE Network.

## Definition of terms

| **Term**                          | **Definition**                                                                                                                                                                                                                                       |
| --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| TA                                | Technical Agreement                                                                                                                                                                                                                                  |
| Affinity Domain (Aff. Domain)     | An XDS(-i) Affinity Domain is a (group of) healthcare enterprise(s) that has/have agreed to work (together) using a common set of policies and share a common infrastructure.                                                                        |
| Medical Record Custodian          | The (legal) entity responsible for the creation and maintenance of medical records contain clinical and medical information of a patient.                                                                                                            |
| Cooperation Agreement             | The (legally binding) sharing agreement used by all Medical Record Custodians within an Affinity Domain                                                                                                                                              |
| Health Information Exchange (HIE) | The act of exchanging patient health related information between two or more parties.                                                                                                                                                                |
| HIE System                        | The system of infrastructure used to share health information.                                                                                                                                                                                       |
| HIE Vendor                        | Vendor of an system capable of participating in an HIE.                                                                                                                                                                                              |
| HIE Administrator                 | The entity responsible for maintaining the HIE infrastructure                                                                                                                                                                                        |
| Community                         | A health information exchange with one or more Medical Record Customdians that are using a common set of policies for the purpose of sharing clinical information via an established mechanism with Medical Record Custodians external to their HIE. |
| IHE                               | Integrating the Healthcare Enterprise .                                                                                                                                                                                                              |
| IHE Connectathon                  | Testing event organized by IHE.                                                                                                                                                                                                                      |
| IHE Integration Profile           | Implementation guideline how to use a specific communication protocol in the context of a sharing clinical information use-case.                                                                                                                     |
| Actor                             | Role or responsibility a system has in relation to a use-case a defines in an IHE Integration Profile.                                                                                                                                               |
| Transaction                       | Technical definition how information is exchanged between two or more actors using a agreed upon (standards-based) communication protocol.                                                                                                           |
| SAML                              | Security Assertion Mark-up Language.                                                                                                                                                                                                                 |
| IdP                               | Identity Provider.                                                                                                                                                                                                                                   |

## Scope and assumptions

This TA takes the Nictiz Interoperability [Model](https://nictiz.nl/app/uploads/2022/02/Electronic-information-for-health-and-care-services-Nictiz-2021.pdf) as guidance and references the lower two layers (IT Infrastructure and Application) of this model. It touches the information layer but will not go into detail as to “what” medical information will be exchanged.

This TA entitles vendors to make their own choices with respect to how they design or implement their HIE system. This TA only addresses the (boundary) interfaces such systems need to implement when interacting with other HIE systems in order to exchange (patient) information.

![](https://lh7-eu.googleusercontent.com/docsz/AD_4nXf1FvdPXQb-13ABuWz9hExe9nQ62Cx1I1Mp8DONS2y0yCHnNiGOvtUlr9CIyEgtwW5ojYCcVFFcqTjQ0rHGf94wEovcumKU7EHzGppeBdQNEM9wdpQwZjMC7xHRvE9NfFrxSMMev-8BtDWNsfmuZB6qZfZ7?key=tvhHE0qAQDmv6Dp7rQX5vw "Position of TA in Ducht Interoperability Model")

The following principles are used while creating this document:

1. This TA extends existing (decentralized) health information exchange systems and infrastructures.
2. This TA acknowledges that existing systems are build using different technology stacks.
3. This TA does not prevent vendors of HIE systems from competing in the marketplace based on functionality, quality, service and/or price.
4. This TA assumes the exchange of medical documents (e.g. Patient Summaries, (scanned) Letters, (Radiology) reports in CDA document format, medical documents in a binary object format, and medical images (in the DICOM format).
5. This TA assumes that a vendor that represents an HIE is responsible for implementing this TA. If a vendor within the HIE is not compliant with this TA, they can cooperate with another vendor to comply with this TA.

## Relation to other documents

This Technical Agreement covers some aspects discussed in other documents published on the NICTIZ website such as the “handreiking interoperabiliteit tussen zorginstellingen 2019”. Since the technical agreement will only address the boundary interfaces of a home community, it will

only describe the responsibilities of these boundary interfaces. The goal of the technical agreement is not to standardize content but to define what boundary interfaces can be expected when integrating in the Dutch National HIE Network and outline the responsibilities of these interfaces on a more technical level.

## Format of this technical agreement

This Technical Agreement starts by outlining the IHE Integration Profiles and transactions that are applicable within the Dutch National HIE Network. The IHE profiles are the foundation of the network and therefore this technical agreement will refer to them wherever possible.

The document will then outline any technical and non-technical responsibilities of HIE vendors or HIE administrators of an HIE infrastructure. It also addresses the responsibilities the HIE vendor should be aware of for successful integration, but to which the vendor itself can’t take responsibility.

Finally, the TA addresses specific technical agreements to which HIE vendors will commit in relation to the transactions of the boundary interfaces (XCA(-i) gateways).
