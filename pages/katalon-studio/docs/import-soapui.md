---
title: "Import web service requests from SoapUI"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/import-soapui.html
description: 
---

Starting version 7.8.0, you can import SOAP requests from a [SoapUI](https://www.soapui.org/getting-started/) to Katalon Studio. It is already possible to import RESTful requests from a SoapUI since version 7.6.0

To import a REST/SOAP test request from a SoapUI to Katalon Studio, perform the following steps:

1. Create or open an API/Web Service project.
   
2. Click the **Import Services from SoapUI** icon.
      
   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-soapui/icon.png" alt="api or web service project type" width=70%>

   Alternately, you can import REST/SOAP test requests via the **Tests Explorer** panel. Right-click on **Object Repository** > **Import** > **From SoapUI**.
      
   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-soapui/K.S.E-8.2.5-import-soap_api.png" alt="object repository" width=70%>

3. In the dialog that displays, browse to your **SoapUI** project and click **OK**.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-soapui/soapui.png" alt="local soap api project" width=70%>

   Katalon Studio loads the file and generates the RESTful/SOAP request objects accordingly.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-soapui/imported.png" alt="generated request objects" width=100%>
