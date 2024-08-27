## Synchronous vs Asynchronous messaging

As described by IHE, when two actors, referred to as Requester and Provider, need to exchange web services based messages using a request-response exchange pattern, they can do so synchronously or asynchronously. This technical agreement allows for vendors to integrate using either a synchronously as well as asynchronous exchange of messages in conformance with IHE specifications and the Asynchronous Web Services Exchange Supplement. 

However, in practice, the Dutch National HIE Network relies on synchronous message exchange since it expected that the processing of the request and formulation of the response takes very little time and lies well within the boundaries of the HTTP timeout values as described in the paragraph “Infrastructure and security agreements”. Therefore, an HIE vendor shall support synchronous messaging.

## Infrastructure and security agreements

### (Mutual) TLS timeout settings

For node authentication TLS inactivity timeout settings should be set as low as possible but in accordance with the HTTP timeout values set in the HIE infrastructure. Note that in case of a DICOM exchange use case a minimum HTTP timeout value of 10 minutes is defined as “normal” (chapter 4.2). The TLS inactivity timeout settings shall be aligned with the XCA-I HTTP timeout values when (large) DICOM studies are retrieved.

### Mutual TLS requirements

- The HIE vendor shall use a TLS version qualified as good (in Dutch: goed) or sufficient (in Dutch: voldoende) in conformance with the guidelines (ICT-beveiligingsrichtlijnen voor Transport Layer Security (TLS)) of the National Cyber Security Center (NCSC).
- The HIE vendor shall apply hashing standards qualified as good (in Dutch: goed) or sufficient (in Dutch: voldoende) in conformance with the above-mentioned guidelines
- The HIE vendor shall use cypher suites qualified as good (in Dutch: goed) or enough (in Dutch: voldoende) in conformance with the above-mentioned guidelines

### Certificate requirements

- The certificate authority of a server certificate should be a known trusted root (or intermediate) authority for the clients
- The certificate shall not be a self-signed certificate
- The certificate used for authentication can be used for both server side and client-side authentication.
- The SubjectDN/CN of a system certificate shall match the system's public host name.
- The HIE vendor shall provide the full certificate chain including all CA’s between the root CA and the certificate

## IHE XUA related agreements

The XUA profile carries a readable and verifiable claim of the user identity, authentication method, and as needed their roles, purpose of use, and consent. This chapter outlines any specific agreements regarding this profile and dealing with multiple identity providers.

### Dealing with multiple Identity providers

Within a home community there can be multiple ways a user is authenticated, therefor there can be a variety of identity providers that are responsible for the claim of the user’s identity. The technical agreement identifies two ways of dealing with this situation.

### Resigning of the XUA token (preferred)

HIE vendors of the systems that act as the initiating gateway actor may modify a SAML token, and shall resign this token if modified.

Resigning a XUA token may be done to achieve operational efficiencies and network scalability. In case this is done, the Initiating Gateway actor is responsible for resigning the XUA token that was created by any of the trusted identity providers within the home community. The consequence of resigning the XUA token is that the Responding Gateways trusts all identities of the initiating community based on the resigning authority.

In this case:

- HIE vendors of the systems that acts as the initiating gateway actor shall provide one identity provider certificate and URI and provide the required details in their connection document
- HIE vendors of the system that acts as the responding gateway actor shall configure the responding gateway to trust this identity provider

### Forwarding the claim of the original identity provider

An HIE vendor can choose to forward a claim from the initiating gateway without modifications or resigning of the claim. This however creates the need for the responding gateway to trust all identity providers that reside within the home communities the initiating gateway represents. In this case it is agreed that:

- HIE vendors of the system that acts as the initiating gateway actor shall provide all identity provider certificates and URI details in their connection document
- HIE vendors of the initiating gateway shall not change any of the claims made by the original identity provider
- HIE vendors of the system that acts as the responding gateway actor shall configure the responding gateway to trust all provided identity providers

### SAML Token attributes (claims)

The following table is derived from ITI TF Vol. 2b section 3.40.4.1.2 (Message Semantics) and lists the SAML token attributes allowed to be included.

| **Attribute**                      | **R/O/C** | **Name space**                                                | **Description**                                                                                                                                                                                                                                                                                                                              |
| ---------------------------------- | --------- | ------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Subject ID                         | O         | urn\:oasis\:names\:tc\:xspa:1.0\:subject\:subject-id          | The value on the Subject ID attribute shall be a plain text description of the user's name (not user ID). This SubjectID may be used for audit logging by the responding gateway.                                                                                                                                                            |
| SubjectOrganizationName            | C         | urn\:oasis\:names\:tc\:xspa:1.0\:subject\:organization        | The value on Subject Organization attribute shall be a plain text description of the organization. This Subject Organization Name may be used for audit logging by the responding gateway.If no Subject Organization name is available, a Subject Organization ID shall be provided.                                                         |
| SubjectOrganization ID             | C         | urn\:oasis\:names\:tc\:xspa:1.0\:subject\:organization-id     | A unique identifier for the organization that the user is representing in performing thisTransaction. If no Subject Organization ID is available, aSubject Organization Name shall be provided.                                                                                                                                              |
| Home CommunityID                   | O         | urn\:ihe\:iti\:xca:2010\:homeCommunityId                      | The value shall be the Home Community ID (an Object Identifier) assigned to the Community that is initiating the request.                                                                                                                                                                                                                    |
| National ProviderIdentifier        | O         | urn\:oasis\:names\:tc\:xspa:1.0\:subject\:npi                 | A National Provider Identifier (NPI) is a unique identifier issued to health care providers by their national authority.                                                                                                                                                                                                                     |
| Other ProviderIdentifier Attribute | O         | urn\:ihe\:iti\:xua:2017\:subject\:provider-identifier         | A unique identifier issued to health care providers by a named authority. This attribute may be repeated.                                                                                                                                                                                                                                    |
| Subject-Role                       | R         | urn\:oasis\:names\:tc\:xacml:2.0\:subject\:role               | The role attribute shall contain one or more role codes from the identified Value-Set that represents the role that the XUA user is playingwhen making the request.                                                                                                                                                                          |
| Authz-Consent                      | O         | urn\:ihe\:iti\:bppc:2007\:docidorurn\:ihe\:iti\:xua:2012\:acp | Conveys either the BPPC document relevant for this transaction context or it references the related Privacy Policy ID agreed upon between communities.                                                                                                                                                                                       |
| Patient Identifier                 | O         | urn\:oasis\:names\:tc\:xacml:2.0\:resource\:resource-id       | Shall be the patient’s BSN for which the transaction is executed.                                                                                                                                                                                                                                                                            |
| Purpose of Use                     | O         | urn\:oasis\:names\:tc\:xspa:1.0\:subject\:purposeofuse        | The PurposeOfUse element shall contain the coded representation of the Purpose for Use that is in effect for the request. The X-ServiceProvider may use the PurposeOfUse value in Access Control decisions. In case no PurposeOfUse element is present inthe transactions; the custodian of the medical record can apply its local policies. |

**Subject Organization ID attribute**

The Subject Organization ID attribute shall be the OID as listed in the HL7 Nederland OID register (<https://www.hl7.nl/component/phocadownload/category/13-oid.html>). Otherwise a Subject Organization ID shall be used that is traceable and verifiable in a publicly available register such as the AGB register.

**HomeCommunityID attribute**

The Home Community ID attribute shall be the OID of the home community as provided in the connection statement.

**Subject-Role attribute**

For a user one or more roles can be provided in the subject role attribute. As described in *Vol. 2b - Section 3.40.4.2 - Additional section to add to all ATNA audit messages when the transaction includes XUA Assertion*. The iDP is responsible for Subject-Role claim.

The HIE system shall be able to interpret or translate the roles coming from the Initiating Gateway. If no national standards are defined or implemented regarding the Subject-Role claim, a variation of roles can be expected.

To support the use case of exchanging medical information between one or more home communities, we define that the initiating HIE system shall be able to translate the Subject-Role claim to at least one of the roles as described in the table below.

| **Code** | **System**                    | **Description**                                                        |
| -------- | ----------------------------- | ---------------------------------------------------------------------- |
| 01.000   | RoleCodeNLUZIRoleCodePersonen | NL: Arts, US: Medical Doctor                                           |
| 56542007 | Snomed CT                     | NL: Beheerder van medische dossiers,  US: Medical record administrator |

If a use case requires additional Subject-Role claims, the use and interpretation of these claims lie outside of the scope of this technical agreement.

**Patient Identifier Attribute**

In cases where a BSN is provided it shall be provided as a HL7 CX Data Type (as defined in Vol. 2b - Section 3.40.4.1.2.2.1 Patient Identifier Attribute) with at a minimum the follow components specified:

- ID Number
- Assigning Authority

Example: 123456789^^^\&amp;2.16.840.1.113883.2.4.6.3\&amp;ISO

**Purpose of Use**

The purpose of use claim is option but if used it shall indicate the intended purposed of the entity that initiated a request, using one of the following codes.

| **Code** | **System** | **Description**                                           |
| -------- | ---------- | --------------------------------------------------------- |
| 1        | ISO 14265  | Clinical care provision to an individual subject of care  |
| 2        | ISO 14265  | Emergency care provision to an individual subject of care |

It is the responsibility of the initiating and responding XCA gateways to map these purpose of use codes to purpose of use codes used within their community and apply, if required, the necessary access control policies.

If a use case requires additional purpose of use codes, the use and interpretation of these codes lie outside of the scope of this technical agreement.

## ITI-38 transaction agreements

The ITI-38 transaction shall contain an IHE-XUA token.

## ITI-39 transactions agreements

The ITI-39 transaction shall contain an IHE-XUA token.

## RAD-75 transactions agreements

The RAD-75 transaction shall contain an IHE-XUA token.

## WADO-WS transactions agreements

The *optional* WADO-WS transaction shall contain an IHE-XUA token.
