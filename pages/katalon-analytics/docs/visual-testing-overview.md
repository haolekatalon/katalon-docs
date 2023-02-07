---
title: "Visual Testing Overview" 
sidebar: katalon_studio_docs_sidebar
permalink: /katalon-analytics/docs/visual-testing-overview.html 
redirect_from:
description: 
---

## What is visual testing?

Visual testing is an automated process that enables user interface (UI) testing of a web/mobile application to ensure that the software/application is represented to the end-users in the exact visual way it is intended to.

With incorporated artificial intelligence (AI), visual testing also refers to the AI image comparison, in which you could compare the visible output (of your tests) against the baseline image using an AI engine.

Since comparing images manually (using human eyes only) could still result in human errors, visual testing allows automated image comparison using AI-powered functions such as pixel-by-pixel detection, text-change detection, and layout-change detection.

Visual testing helps reduce human errors to a minimum because it captures even minor differences between two images, which human eyes might accidentally miss.

> Notes:
>
> A baseline image is a reference image initially configured to compare with other image output from visual testing.

## Insights

If the software has visual issues, functional testing cannot help since it focuses on the software behaviors only.

For example, automated functional tests cannot detect any change regarding the layout, colors, fonts, or misplacement of elements on a website. In such a case, one would need to check for any visual regressions instead, and the apparent solution is to run visual testing.

Furthermore, there is an increasing demand for opening/using software on different platforms. Considering the combination of different operating systems and browsers when developing a website, it is also wise to be aware that the website might display adequately on one browser but improperly on another browser. Hence, testing a website across various platforms is crucial to check for any visual defects. Manually doing so would cost tremendous time and effort, not to mention that the human eyes might still miss one or two minor visual bugs if checking complex layouts.

Running visual tests spots visual bugs faster and more effectively, and it makes sure those bugs cannot slip into production. Consequently, visual testing helps boost productivity, increase product confidence, and optimize user experiences.

## TestOps Visual Testing

Katalon TestOps offers visual testing with three image comparison methods: pixel-based, layout-based, and content-based comparison. Since AI powers the layout-based and content-based methods, TestOps Visual Testing could become an integral part of your visual testing infrastructure.

### Pixel-based comparison

This method compares the pixel resolution of two images to figure out the pixel-by-pixel differences between them.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-visual-testing/kt-visual-testing-pixel-ui-may2022.png" width=100% alt="pixel comparison">

The advantage of this method is that it is a popular function and easy to understand and implement. This method identifies pixel differences and picks up minor changes that could be trivial or ignorable to the human eyes.

### Layout-based comparison

This method identifies and maps the similar zones between the baseline and checkpoint images, highlighting the layout differences between the two images.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-visual-testing/kt-visual-testing-layout-ui-may2022.png" width=100% alt="layout comparison">

> Notes:
>
> The AI engine will identify the zones on the images.

In Katalon TestOps, the zones are categorized into 3 types:

* Identical (green border): shows UI zones identically rendered in both images.
* Distinguishable (red border): shows UI zones that look identical for the most parts but have some recognizable distinctions.
* Missing/New (pink border): shows UI zones that exist in one image but not in the other.

This method is helpful to review changes identified by the pixel-based comparison, and it spots the changes in layout, color, font, and element location.

### Content-based comparison

This method identifies the text content differences between two images.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-visual-testing/kt-visual-testing-text-content-ui-may2022.png" width=100% alt="content comparison">

> Notes:
>
> The AI engine will identify the zones on the images.

In Katalon TestOps, the zones are categorized into 3 types:

* Identical (green border): shows text-look-like zones identically rendered in both images.
* Shifted (blue border): shows text-look-like zones with identical but shifted positions.
* Missing/New (pink border): shows text-look-like zones in one image but not in the other.

This method is useful when there is a lot of text content on the pages. It helps users review and prioritize which text changes are critical and need immediate attention.

For step-by-step instructions to use visual testing in Katalon TestOps, see [Use TestOps Visual Testing](https://docs.katalon.com/katalon-analytics/docs/ks-visual-testing.html#set-up-visual-testing).
