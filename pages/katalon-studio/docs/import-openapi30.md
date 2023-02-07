---
title: "Import REST API with OpenAPI Specification 3.0" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/import-openapi30.html
---

This manual shows you how to import RESTful APIs with [OpenAPI Specification version 3.0](https://swagger.io/specification/) to Katalon Studio. For more information on how to import RESTful APIs with OpenAPI 2.0 (Swagger), see: [Import RESTful requests from OpenAPI Specification Swagger (2.0)](https://docs.katalon.com/katalon-studio/docs/import-rest-requests-from-swagger-20.html).

> **Requirements**
>
> * Katalon Studio version 7.7.0 
> * An active Katalon Studio Enterprise license.

To import a service definition with OpenAPI 3.0, perform the following steps:

1. Create or open an API/Web Service project. 
   
2. To import test requests with OpenAPI 3.0, click on **OpenAPI** > **Import OpenAPI 3**.

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-openapi30/icon.png" alt="api or web service project type" width=65%>

   Alternately, you can import test requests via the **Tests Explorer** panel. Right-click on **Object Repository** > **Import** > **From OpenAPI 3**.

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-openapi30/K.S.E-8.2.5-import-postman-object_repository_open_api3.png" alt="object repository" width=70%>

3. In the dialog that displays, browse to your **OpenAPI 3.0** local file and click **OK**.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-openapi30/browse-openapi30.png" alt="dialog box" width=70%>

   Katalon Studio loads the file and generates RESTful test requests accordingly.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-openapi30/imported.png" alt="generated request" width=70%>

**See also:**

* [Use test requests in a test case](https://docs.katalon.com/katalon-studio/docs/using-web-services-in-a-test-case.html).
* [Parameterize a Web Service Object](/display/KD/Parameterize+a+Web+Service+Object).
* [Verification Snippets](/display/KD/Verification+Snippets).
* [Import RESTful requests with OpenAPI Specification 2.0 (Swagger)](https://docs.katalon.com/katalon-studio/docs/import-rest-requests-from-swagger-20.html).