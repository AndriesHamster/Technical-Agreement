## HIE Administrator responisbilities

The following responsibilities can impact the transactions between affinity domains. These responsibilities are not necessarily that of the HIE vendor but need to be aligned on clearly within the affinity domain that the HIE vendor represents. HIE vendors integrating within the Dutch National HIE Network can assume that these responsibilities are taken care of by the HIE Administrator that manages the affinity domain it is connecting to.

### Cooperation agreements

The topics below are typically part of a cooperation agreement (Dutch: samenwerkingsovereenkomst). This agreement is relevant when integrating with the Dutch National HIE Network as these can impact the integration between the home communities.

### Users and user roles

Within the scope of the technical agreement it is relevant that the cooperation agreement states:

- That users are individually traceable and authenticated based on a personal (user)account
- Which user roles are allocated on user authentications and which user roles can query and retrieve information from other home communities?

### Patient identification and BSN verification

Within the scope of the technical agreement it is relevant that both the initiating gateway and the responding gateway can assume that it is the medical record custodians' responsibility that the patient was identified, and the BSN was verified by legal standards. Where applicable this verified BSN is used as the patient ID in the transactions described in this document.

### Patient consent registration and consent scope

Within the scope of the technical agreement it is relevant that the cooperation agreement states that it is the responsibility of the medical record custodian to capture a patient’s consent and only share medical information in accordance with the patient’s consent. How this responsibility is (technically) fulfilled is up to the medical record custodian and the HIE administrator, within the possibilities offered by the HIE vendor.

## Legal compliance

This technical agreement does not address legal compliance that may be applicable to the context in which patient information is exchanged between two (or more) medical record custodians. It is assumed that all parties involved in the exchange obey the applicable legislation(s).

## IHE integration statements

Organizations and/or vendors providing a gateway service to other HIEs shall be able to exchange an IHE conformance statement of their gateway service.

## IHE Connectathon participation and scope

Organizations and/or vendors providing a gateway service shall use a system that successfully validated the transactions mentioned in chapter 2.1 Mandatory IHE transactions at an IHE. Such Connectathon results shall be publicly available at the IHE Connectathon Results Website.

## Metadata quality

The responsibility of the information quality and the meta-data lies outside the scope of these boundary interfaces.

## Providing a connection document

Organizations and/or vendors providing a gateway service shall be responsible to provide a “connection document” through which the technical (connectivity) details for other HIEs are made available. A template connection document is added as an appendix￼.
