---
title: "Import from Postman"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/import-postman.html
description: Guides on how to import from Postman.
---
To import test requests from Postman, perform the following steps:

1. Export your Postman collection to JSON. See the instruction [here](https://learning.getpostman.com/docs/postman/collections/data_formats/#exporting-and-importing-postman-data). 

2. In Katalon Studio, with an API/Web Service project, click on the **Postman** icon.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-postman/postman.png" alt="api or web service project type" width=70%>

   Alternately, from Katalon Studio 8.3.0 onwards, you can import test requests via:

   * The **Action** button in the top menu bar:
  
     * In the top menu bar, click **Action** > **API/Web Service** > **Import Postman**.

         <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-postman/K.S.E-8.2.5-import-postman-api_option.png" alt="action button" width=40%>

   * The **Tests Explorer** panel:
   
     * In **Tests Explorer**, right-click on **Object Repository** > **Import** > **From Postman**.

         <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-postman/K.S.E-8.2.5-import-postman-object_repository_option.png" alt="action button" width=70%>
         

3. In the dialog that displays, browse to your exported **Postman** local file and click **OK**.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/import-postman/browser.png" alt="browse to local file" width=100%>

   The corresponding test requests will be imported to Katalon Studio.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/new/version-615/img2.png" alt="imported test requests" width=100%>
