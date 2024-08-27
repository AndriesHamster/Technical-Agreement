# IHE Actors and Transactions

This TA applies on the boundary interfaces of home communities. Only transaction between the boundary actors (XCA(-i) gateways) will be addressed. In all cases the standards as described by IHE are leading. 

When there is room for interpretation of these standards in the context of applying them in the Netherlands, this TA will address resolutions vendors supporting this TA will commit to. 

## IHE mandatory transactions

The TA mandates the use of the IHE XCA, XCA-I and XUA profiles for the interfaces through which the HIE systems interact. Hence, HIE system vendors have the obligation to implement the IHE Initiating Gateway, Responding Gateway, X-Service User and X-Service Provider actors. For security purposes the IHE XUA and ATNA profiles and their actors are used.

In order to fulfill the (XUA) X-Service User actor an HIE system must be able to provide a trusted user identity. How this IdP responsibility is achieved by the HIE system is out of scope for this TA. This TA will only dictate the minimal set of “user attributes” (or claims) the identity provider must be able provide. The IHE profiles this TA references can be found in:

- IT Infrastructure Technical Framework volume 1 t/m 3.
- Radiology Technical Framework volume 1 & 2.

Unless otherwise specified the latest version of the above listed frameworks are referenced.

![](https://lh7-eu.googleusercontent.com/docsz/AD_4nXeBwQk7eQ8RNsLofMWFJW4lwYPVw2gk-126Sja903VqfBc9mULYTPLqQx9FuBFrJ9pEB2uYn9OcIoALaFDJVKTjX-EpuoEbmsuVhb9hS4QsW1inzhgA0uU7NwW_ikO_--Zllsg9plOHh6i-JbYqnMVBPXYH?key=tvhHE0qAQDmv6Dp7rQX5vw)

An HIE Vendor shall implement, and successfully validate at an IHE Connectathon, the following actors & transactions within their HIE system:

| **Profile** | **Actors**                                             | **Transactions**                                                  |
| ----------- | ------------------------------------------------------ | ----------------------------------------------------------------- |
| ATNA        | Secure Application, Secure Node                        | ITI-19 (Node Authentication)                                      |
| XCA         | Initiating Gateway, Responding Gateway                 | ITI-38 (Cross-community Query), ITI-39 (Cross-community Retrieve) |
| XCA-I       | Initiating Imaging Gateway, Responding Imaging Gateway | RAD-75 (cross-community Retrieve Imaging Document Set)            |
| XUA         | X-Service User, X-Service Provider                     | ITI-40 (Provide X-User Assertion)                                 |

## Other optional transactions

Since the above transactions only allow for the exchange of documents and full DICOM studies the optional transaction “WADO-WS” has been implemented. WADO-WS is not an official IHE profile, but due to the need of exchanging lossy compressed images via XCA-I the vendors Enovation and Founda Health B.V. (Forcare at the time) decided to support this standard during the Dutch IHE steering group consultation of November 27th.

Referenced documentation for the WADO-WS transaction can be found on:

- <https://wiki.ihe.net/index.php/WADO-WS_Extensions_for_XDS-I.b_and_XCA-I> 
- <http://dicom.nema.org/dicom/2013/output/chtml/part18/sect_6.4.html> 

| **Standard**   | **Actors**                                             | **Transactions**                                |
| -------------- | ------------------------------------------------------ | ----------------------------------------------- |
| DICOM, WADO-WS | Initiating Imaging Gateway, Responding Imaging Gateway | WADO-WS, Retrieve Rendered Imaging Document Set |

Implementation of the WADO-WS transaction shall be agreed upon on a case by case bases since this transaction strongly relies on the capabilities of both the Imaging Source and the XDS(-i) consumer. Since the WADO-WS transaction is not tested on an IHE Connectathon it shall therefore be tested on an acceptance environment with at least two other vendors that are part of the Dutch National HIE Network. To allow for integration of this transaction by HIE Vendors the transaction specifications are part of this TA agreement. The (reference to the) WSDL can be found in the appendix.
