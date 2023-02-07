---
title: "Import RESTful requests from WADLs" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/import-wadl.html 
---

Starting **version 7.7.0**, Katalon Studio supports the import of [WADL](https://www.w3.org/Submission/2009/03/) files to create RESTful requests. This section shows you how to import a WADL file into a Katalon project. Refer to the sample WADL description given [here](https://www.w3.org/Submission/wadl/#x3-40001.3).

To import a RESTful request from a WADL to Katalon Studio, perform the following steps:

1. Create or open an API/Web Service project.

2. Click the **Import WADL** icon.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-wadl/icon.png" alt="api or web service project type" width=50%>

   Alternately, you can import a RESTful request from a WADL, via the **Tests Explorer** panel. Right-click on **Object Repository** > **Import** > **From WADL**.

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-wadl/K.S.E-8.2.5-import-wadl_api.png" alt="object repository" width=70%>
   
3. In the displayed dialog, browse to your **WADL** local file and click **OK**.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-wadl/browse.png" alt="browse to local wadl file" width=70%>

   Katalon Studio loads the file and generates RESTful request objects accordingly.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-wadl/imported.png" alt="generated request objects" width=70%>

**See also:**

* [Use test requests in a test case](https://docs.katalon.com/katalon-studio/docs/using-web-services-in-a-test-case.html).
* [Parameterize a Web Service Object](/display/KD/Parameterize+a+Web+Service+Object).
* [Verification Snippets](/display/KD/Verification+Snippets).
