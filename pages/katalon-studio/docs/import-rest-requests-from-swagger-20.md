---
title: "Import RESTful requests with OpenAPI Specification 2.0 (Swagger)" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/import-rest-requests-from-swagger-20.html 
redirect_from:
    - "/display/KD/Import+REST+requests+from+Swagger+2.0/"
    - "/display/KD/Import%20REST%20requests%20from%20Swagger%202.0/"
    - "/x/8hXR/"
    - "/katalon-studio/docs/import-rest-requests-from-swagger-20/"
description: 
---
> [Read more about Swagger 2.0...](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md).

This topic shows you how to import web service objects from a **Swagger 2.0** file or URL, depending on the type of your Katalon Studio project.

To import a RESTful request from Swagger 2.0 to Katalon Studio, perform the following steps:

1. Create or open an API/Web Service project. 

2. To import a RESTful request from **Swagger 2.0**, click on **OpenAPI** > **Import OpenAPI 2 (Swagger)**.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-rest-requests-from-swagger-20/import.png" alt="api or web service project type" width=40%>

   Alternately, you can import a RESTful request via the **Tests Explorer** panel. Right-click on **Object Repository** > **Import** > **From OpenAPI 2 (Swagger)**.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-rest-requests-from-swagger-20/K.S.E-8.2.5-import-swagger-object_repository_open_api2.png" alt="object repository" width=70%>

3. In the dialog that displays, browse to your **Swagger** local file or enter an OpenAPI 2 (Swagger) URL and click **OK**.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-rest-requests-from-swagger-20/browse.png" alt="browse to local file" width=70%>

    Katalon Studio loads the file and generates RESTful test requests accordingly.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-rest-requests-from-swagger-20/result.png" alt="generated test requests" width=70%>

> **Known Issues**:
> 
> *   No Raw text content in HTTP Body parsed from Swagger.
> *   No Authorization parsed from Swagger.
> *   Variables and Parameters must be adjusted manually.

**See also:**

* [Use test requests in a test case](https://docs.katalon.com/katalon-studio/docs/using-web-services-in-a-test-case.html).
* [Parameterize a Web Service Object](/display/KD/Parameterize+a+Web+Service+Object).
* [Verification Snippets](/display/KD/Verification+Snippets).
* [Import REST API with OpenAPI Specification 3.0](https://docs.katalon.com/katalon-studio/docs/import-openapi30.html).