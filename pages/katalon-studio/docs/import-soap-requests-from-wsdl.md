---
title: "Import SOAP requests from WSDLs" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/import-soap-requests-from-wsdl.html 
redirect_from:
    - "/display/KD/Import+SOAP+requests+from+WSDL/"
    - "/display/KD/Import%20SOAP%20requests%20from%20WSDL/"
    - "/x/BhbR/"
    - "/katalon-studio/docs/import-soap-requests-from-wsdl/"
description: 
---

[WSDL](https://www.w3.org/TR/wsdl/) is used for specifying a SOAP web service's functionality. It is critical to SOAP web service testing when you can create web service requests based on a WSDL file. This section shows you how to import a WSDL file into a Katalon project and explore it as well.

Starting **version 7.5.0+**, Katalon Studio has improved the *WSDL import feature* with a more intuitive UI and added utility, for support. You can, in particular, add the desired endpoint to your SOAP request, which takes precedence over the imported endpoint.

## Importing WSDLs into Katalon Studio

To import a WSDL file to your project, perform the following steps:

1. Create or open an API/Web Service project.
   
2. In the **Tests Explorer** panel, right-click on **Object Repository** > **Import** > **From WSDL**.
   
   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-soap-requests-from-wsdl/K.S.E-8.3.0-import-soap_requests_from_wsdl.png" alt="object repository" width=70% >

3. In the **URL** field of the **Import WSDL** dialog, specify either a remote WSDL url or the path of a local WSDL file (E.g. `http://www.dneonline.com/calculator.asmx?WSDL`).
   
4. Click **OK**. Katalon Studio loads the file and generates SOAP request objects.
   
   > Notes:
   > 
   > If you have created an **API/Web Service** project, click the **Import WSDL** icon on the main toolbar to display the **Import WSDL** dialog in step 3.
   >
   > <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-soap-requests-from-wsdl/import-wsdl-icon.png" alt="api or web service project type" width=70% >
  
## Working with imported WSDLs

A WSDL may contain multiple services. For each service, Katalon Studio:

 - Creates a SOAP request with a specific service function.
  
 - Parses its content from the specified WSDL, into their corresponding fields in the request object, such as Service Endpoint, SOAPAction, and Request message. 
  
For example, Katalon Studio creates multiple request objects with `http://www.dneonline.com/calculator.asmx?WSDL`.  

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-soap-requests-from-wsdl/parsed-objects.png" alt="parsed objects" width=100%>

Starting version 7.5.0, you can manually change the content of these fields. When you override any fields of the imported request object with new values, you need to *save* your modification(s) for it to take effect.

* **Service Endpoint**: This tab stores the service endpoint parsed from the WSDL file. You can specify another endpoint for the interface if you prefer. The request object receives any value given in this field.
  
* **SOAPAction**: The SOAPAction is parsed in the HTTP Header of the request if the request method is SOAP.

## Troubleshooting

After sending the SOAP request, you may encounter a *System.Web.Services.Protocols.SoapException: Server did not recognize the value of HTTP Header SOAPAction..* exception (1), in the response.

This can happen if you check the **Use the endpoint and SOAPAction header parsed from WSDL** (2) check box, and at the same time, specify the SOAPAction in the request header (3).

*(1),(2),(3): please see the image below for more information.*

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-soap-requests-from-wsdl/exception.png" alt="exception message" width=100%>

**Proposed solution**

Remove *SOAPAction* from the *HTTP Header*, if you decide to use the endpoint and SOAPAction header parsed from WSDL.

See also:

  * [SOAP Request](https://docs.katalon.com/katalon-studio/docs/soap.html)