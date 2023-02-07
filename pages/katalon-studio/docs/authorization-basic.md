---
title: "[Authorization] Basic" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/authorization-basic.html 
redirect_from:
    - "/display/KD/authorization-basic/"
    - "/display/KD/Authorization-basic/"
    - "/katalon-studio/docs/authorization-basic/"
description: 
---

## Basic

This is the simplest authorization for a request. With basic authentication, you need to input your credentials to authenticate the request. These credentials will be encoded into the Authorization request headers. Do as follows:

1. In the **Authorization** tab of a web service request, set the **Type** as **Basic**.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/authorization-basic/basic-authorization.png" alt="authorization basic" width="100%">

2. Pass in your username and password to authenticate the request, then click on **Update to HTTP Header**. The username and password are encoded to the **Authorization** request of the **HTTP Header** tab, as you can see below. 

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/authorization-basic/basic-http-header.png" alt="http header" width="100%">
