# Technical Responsibilities

## Network security

Connecting HIE vendors must assure the following regarding network security.

### **Connectivity on infrastructure level**

The administrator of an HIE infrastructure is responsible for allowing other parties to connect to the endpoints as provided in the “Connection Document”. If there any special requirements for achieving connectivity (e.g. IP whitelisting, IP-sec tunneling etc.) the administrator of an HIE infrastructure shall mention these requirements in the connection document.

### **Domain Name System addressing endpoints**

The administrator of an HIE infrastructure shall provide a Domain Name System (DNS) Address for endpoint of the XCA(-i) actor(s), and shall maintain the DNS entries that allow connecting to these endpoints.

### **Bandwidth**

The administrator of an HIE infrastructure is responsible for sufficient bandwidth from and to the HIE system in order to support the exchange of medical information. In case of XCA-I transactions (which allows for the exchange of DICOM studies) the HIE system is preferred to have a 1 Gigabit network connection (1,000 megabits) to the HIE system(s) involved with these transactions.

### Server certificates

- In conformance with the ATNA profile all XCA(-i) gateways must implement the secure node actor providing secure network connections through mutual TLS. Endpoints of the secure nodes shall therefore always use the Hypertext Transfer Protocol Secure (https) protocol.
- On production environments the server certificate is provided specifically for that server.
- Server certificates used for mutual TLS shall be signed by a publicly trusted certificate authority.
- HIE infrastructures can use a loadbalancer set-up. How load balancing is implemented or set up technically is outside the scope of this document and remains the HIE vendors choice. The loadbalancer and/or the load balancing setup however shall support establishing mutual TLS.
- All certificates required to establish mutual TLS, for the transactions specified in this
- document, will be part of the connection document and will comply with the points above.

## Performance

By default, the Dutch National HIE Network relies on a synchronous message exchange. This requires that the processing of the request and formulation of the response needs to take place within the boundaries of the HTTP timeout value. Therefor vendors of HIE systems have a best-efforts obligation towards maintaining the performance of the IHE infrastructure.

Vendors agree that typically processing a request and start formulating an initial response should take no longer than 10 minutes, which can then be considered as the “default timeout boundary” especially considering the exchange of DICOM images (specifically the WADO-WS and RAD-75 transactions). If the usecase allows for a lower HTTP time-out boundary, this can be applied by vendors. For example, an usecase where only documents are exchanged via ITI-38 and ITI-39. Note that the HTTP timeout should be in line with the Mutual TLS timeout setting (5.2.1.1 (Mutual) TLS timeout settings). 

If an affinity domain repeatedly fails to respond within this 10 minute “default timeframe”, an HIE vendor must be able to allow an HIE administrator to configure a higher time-out value. In case timeout exceeds the agreed upon threshold the initiating gateway can close the connection.

HIE vendors will investigate the performance of the affinity domain and to their best efforts identify any

HIE system that might be the cause of the delay. If the performance is impacted by systems

controlled by the HIE vendor, the HIE vendor shall, to their best effort try to mitigate the performance issues in order to maintain the timeout window that is acceptable for involved parties.

How this best effort translates directly to potential solutions, such as load balancing or allocating additional virtual or physical system resources to an HIE system, is out of scope for this TA allowing vendors to make their own choices.

It is possible that the performance is impacted by systems beyond the boundary interfaces that are not controlled by the HIE vendor. In that case the HIE vendor shall inform the involved parties about the set timeout boundaries and inquire if there is a way that these boundaries can be met. If not, parties can agree on setting new boundaries that are acceptable for all involved parties.

## Availability of services

Availability agreements are out of scope for this technical agreement. These agreements are customer facing only and do not apply on the boundary interfaces discussed in this TA.

However, HIE vendors shall to their best-effort maintain the highest possible availability for both acceptance as production environments allowing for the best possible 24/7 nationwide availability of medical information for affinity domains connected to the Dutch National HIE Network.

## Auditing

HIE vendors shall provide a means for Accountability, meaning each transaction as mentioned in chapter “IHE standards and transactions” shall be logged, allowing for a full audit of the integration. This can be achieved in several ways and is not limited to implementation of the IHE ATNA profile.

Systems that are responsible for processing auditing messages from the HIE systems can expect that audit messages contain the information as was exchanged between these boundary interfaces. This is in conformance with the ATNA specifications as defined in chapter “3.40.4.2 ATNA Audit encoding”.

When an initiating gateway is requested to resign a SAML token the responding gateway shall use information from the resigned token for its ATNA audit logging.

## Consistent Time

HIE systems shall implement the consistent time profile.

## Respecting cooperation agreements

An initiating gateway shall respect cooperation agreements and only query home communities that contain information for which a cooperation agreement is available.

An XCA(-i) responding gateway can act as an entry point to multiple home communities / organizations. It is the responsibility of the queried home community to respect the “cooperation agreements”.

How this is achieved and implemented is the choice of an HIE vendor. The information in the XUA (SAML) token as described in chapter 8.2 XUA related agreements contains the required information to enforce these cooperation agreements.

## Applying patient consent

Dutch legislation mandates that a medical record custodian is responsible to enforce a patient's consent when exchanging health information. This technical agreement does not dictate how, or where within the affinity domain an HIE vendor should implement rules that apply patient consent to incoming queries.
