---
title: Appendix: WADO WS specification (WSDL)
slug: 1yy4-appendix
createdAt: 2024-07-21T16:00:34.439Z
updatedAt: 2024-07-21T16:04:52.889Z
---

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!-- This wsdl file is for an XDS-I.b Imaging Document Source Actor
It can be used 'as is' to support Retrieve Imaging Document Set Transaction [RAD-69]
using Synchronous Web Services.-->
<definitions name="ImagingDocumentSource" targetNamespace="urn:ihe:rad:xdsi-b:2009"
   xmlns="http://schemas.xmlsoap.org/wsdl/"
   xmlns:wsdl="http://schemas.xmlsoap.org/wsdl/"
   xmlns:soap12="http://schemas.xmlsoap.org/wsdl/soap12/"
   xmlns:wsaw="http://www.w3.org/2006/05/addressing/wsdl"
   xmlns:xsd="http://www.w3.org/2001/XMLSchema"
   xmlns:tns="urn:ihe:rad:xdsi-b:2009"
   xmlns:wadows="urn:dicom:wado:ws:2011"
   xmlns:deprecatedwadows="urn:dicom:ws:wado:2011"
   xmlns:ihe="urn:ihe:iti:xds-b:2007"
   xmlns:rs="urn:oasis:names:tc:ebxml-regrep:xsd:rs:3.0"
   xmlns:lcm="urn:oasis:names:tc:ebxml-regrep:xsd:rim:3.0">
   <documentation>IHE XDS-I.b Imaging Document Source</documentation>
   <types>
       <xsd:schema elementFormDefault="qualified">
           <xsd:import namespace="urn:oasis:names:tc:ebxml-regrep:xsd:rs:3.0" />
           <xsd:import namespace="urn:ihe:iti:xds-b:2007" />
           <xsd:import namespace="urn:ihe:rad:xdsi-b:2009" />
       </xsd:schema>
   </types>
   <message name="RetrieveImagingDocumentSetRequest_Message">
       <documentation>Retrieve Imaging Document Set</documentation>
       <part name="body" element="tns:RetrieveImagingDocumentSetRequest" />
   </message>
   <message name="RetrieveRenderedImagingDocumentSetRequest_Message">
       <documentation>Retrieve Rendered Imaging Document Set</documentation>
       <part name="body" element="wadows:RetrieveRenderedImagingDocumentSetRequest" />
   </message>
   <message name="DeprecatedRetrieveRenderedImagingDocumentSetRequest_Message">
       <documentation>Deprecated Retrieve Rendered Imaging Document Set</documentation>
       <part name="body" element="deprecatedwadows:RetrieveRenderedImagingDocumentSetRequest" />
   </message>
   <message name="RetrieveRenderedImagingDocumentSetResponse_Message">
       <documentation>Retrieve Rendered Imaging Document Set Response</documentation>
       <part name="body" element="wadows:RetrieveRenderedImagingDocumentSetResponse" />
   </message>
   <message name="RetrieveDocumentSetResponse_Message">
       <documentation>Retrieve Document Set Response</documentation>
       <part name="body" element="ihe:RetrieveDocumentSetResponse" />
   </message>
   <portType name="ImagingDocumentSource_PortType">
       <operation name="ImagingDocumentSource_RetrieveImagingDocumentSet">
           <input message="tns:RetrieveImagingDocumentSetRequest_Message" wsaw:Action="urn:ihe:rad:2009:RetrieveImagingDocumentSet" />
           <output message="tns:RetrieveDocumentSetResponse_Message" wsaw:Action="urn:ihe:iti:2007:RetrieveDocumentSetResponse" />
       </operation>
       <operation name="ImagingDocumentSource_RetrieveRenderedImagingDocumentSet">
           <input message="tns:RetrieveRenderedImagingDocumentSetRequest_Message" wsaw:Action="urn:dicom:wado:ws:2011:RetrieveRenderedImagingDocumentSet" />
           <output message="tns:RetrieveRenderedImagingDocumentSetResponse_Message" wsaw:Action="urn:dicom:wado:ws:2011:RetrieveRenderedImagingDocumentSetResponse" />
       </operation>
       <operation name="ImagingDocumentSource_DeprecatedRetrieveRenderedImagingDocumentSet">
           <input message="tns:DeprecatedRetrieveRenderedImagingDocumentSetRequest_Message" wsaw:Action="urn:dicom:ws:wado:2011:RetrieveRenderedImagingDocumentSet" />
           <output message="tns:RetrieveDocumentSetResponse_Message" wsaw:Action="urn:ihe:iti:2007:RetrieveDocumentSetResponse" />
       </operation>
   </portType>
   <binding name="ImagingDocumentSource_Binding" type="tns:ImagingDocumentSource_PortType">
       <soap12:binding style="document" transport="http://schemas.xmlsoap.org/soap/http" />
       <wsaw:UsingAddressing wsdl:required="true" />
       <operation name="ImagingDocumentSource_RetrieveImagingDocumentSet">
           <soap12:operation soapActionRequired="false" />
           <input>
               <soap12:body use="literal" />
           </input>
           <output>
               <soap12:body use="literal" />
           </output>
       </operation>
       <operation name="ImagingDocumentSource_RetrieveRenderedImagingDocumentSet">
           <soap12:operation soapActionRequired="false" />
           <input>
               <soap12:body use="literal" />
           </input>
           <output>
               <soap12:body use="literal" />
           </output>
       </operation>
       <operation name="ImagingDocumentSource_DeprecatedRetrieveRenderedImagingDocumentSet">
           <soap12:operation soapActionRequired="false" />
           <input>
               <soap12:body use="literal" />
           </input>
           <output>
               <soap12:body use="literal" />
           </output>
       </operation>
   </binding>
   <service name="ImagingDocumentSource_Service">
       <port name="ImagingDocumentSource_Port_Soap12" binding="tns:ImagingDocumentSource_Binding">
           <soap12:address location="http://servicelocation/ImagingDocumentSource_Service" />
       </port>
   </service>
</definitions>
```
