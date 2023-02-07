---
title: "How to extract and verify textual patterns in a test case"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-recorder/docs/how-to-extract-and-verify-textual-patterns-in-a-test-case.html
description: "In this tutorial, we use Katalon Recorder to extract and verify texts through pattern matching (regex)."
---

In a test project, you might want to verify that the application under test (AUT) displays information in the correct pattern. For example:

* Price tag pattern of a shopping item.
* Email address pattern.
* Phone number pattern.


Katalon Recorder supports this pattern matching process with several commands. Specifically, commands in Katalon Recorder can take patterns as input to verify several data types on an AUT.

This tutorial shows you how to extract and verify displayed text on an AUT. The pattern used in our case is a *regular expression* (regex): a sequence of characters that specifies a search pattern.

> **Notes**:
>
> * To use the sample project of this tutorial, navigate to **Actions** > **Sample Projects**, then add the **Extract data and verify textual patterns** project.

## Test case scenario

In our example, we have a scenario "extract and verify item price," which consists of these steps:

1. Navigate to the AUT - Katalon Zack Market: `https://demo-store.katalon.com`.
2. On the homepage, select an item.
3. On the item details page, extract the item price.
4. Verify that the item price is in the correct pattern: a currency symbol (`$`) followed by a numeric value.

Our AUT displays the price text of an item as follows:

<a class="pop">
<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/extract-and-verify-textual-patterns/KR-AUT-selected-shopping-item.png" width=100% alt="Katalon Recorder AUT overview">
</a>
<p style="text-align: center;"><em>Click the image to enlarge</em></p>

We can see that the price text consists of the item price (`$25.99`) and the currency code (`CAD`).

To automate the scenario with Katalon Recorder, we propose the following process:

1. Record the test case: we record the test case to open the AUT and select an item.
2. Extract and verify textual patterns: we manually modify the recorded test case to select and verify the price text.

## Record the test case

1. In Katalon Recorder, create a test suite and a test case, then click **Record** to start recording.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/extract-and-verify-textual-patterns/KR-5.8.0-New-test-case.png" width=100% alt="Katalon Recorder new test case">

2. In an active browser tab, navigate to the AUT - Katalon Zack Market: `https://demo-store.katalon.com`.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/extract-and-verify-textual-patterns/KR-AUT.png" width=100% alt="AUT">

3. On the displayed homepage, select an item.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/extract-and-verify-textual-patterns/KR-AUT-select-an-item.png" width=100% alt="AUT - Select an item">

4. In Katalon Recorder, click **Stop** to stop the test recording.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/extract-and-verify-textual-patterns/KR-5.8.0-Click-Stop.png" width=100% alt="Recorded test case">

## Extract and verify textual patterns

To complete the scenario, we manually modify the test case to extract only the price from the displayed price text. Then, we verify that the price is in the correct pattern using a regex.

Open the recorded test case and follow these steps:

1. Store the displayed price text. We want to store the price text into a variable.

    To do so, we use the `storeText` command.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/extract-and-verify-textual-patterns/KR-5.8.0-storeText-command.png" width=100% alt="Katalon Recorder storeText command">

    We need to capture the **Target** (the price text locator) for the command. Click on the **Selector** tool, then hover the cursor over and select the price text on the page.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/extract-and-verify-textual-patterns/KR-5.8.0-Selector-tool.png" width=100% alt="Katalon Recorder capture target">

    In our case, the captured locator is the XPath: `xpath=//div[@id='root']/div/div/div/div[2]/div/div[2]/div/div[3]`. We then store the text into the `displayedPrice` variable.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/extract-and-verify-textual-patterns/KR-5.8.0-storeText-command-with-target-and-value.png" width=100% alt="Katalon Recorder complete storeText command">

    | Command                    | Target                      | Value                                                       |
    |----------------------------|-----------------------------|-------------------------------------------------------------|
    | `storeText` | `xpath=//div[@id='root']/div/div/div/div[2]/div/div[2]/div/div[3]` | `displayedPrice` |

2. Extract the item price.

    We use the `storeEval` command to extract the item price `$25.99` (the first six characters) from the text.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/extract-and-verify-textual-patterns/KR-5.8.0-storeEval-command.png" width=100% alt="Katalon Recorder storeEval command with a Javascript expression">

    | Command                    | Target                      | Value                                                       |
    |----------------------------|-----------------------------|-------------------------------------------------------------|
    | `storeEval` | `"${displayedPrice}".substring(0, 6)` | `itemPrice` |

    The `storeEval` command evaluates a Javascript expression, then stores the result into a variable. In our example, the target Javascript expression is `"${displayedPrice}".substring(0, 6)`. Here, `substring()` is a method that extracts characters from a string, given two indices.

    The expression evaluates the `displayedPrice` variable into its value. Then it extracts and stores the first six characters into the `itemPrice`.

3. Verify the item price with regex.

    We use the `verifyEval` command with a regex in the **Value** field. This command verifies that the item price is displayed in the correct price pattern.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/extract-and-verify-textual-patterns/KR-5.8.0-verifyEval-command.png" width=100% alt="Katalon Recorder verifyEval command with a Javascript expression and regular expression">

    | Command                    | Target                      | Value                                                       |
    |----------------------------|-----------------------------|-------------------------------------------------------------|
    | `verifyEval` | `"${itemPrice}"` | `regexp:^[$](\d+\.\d+)` |

    To input a regex as a value, we prefix the expression with `regexp:`. For our purpose, we use the regex `^[$](\d+\.\d+)` that checks if the item price starts with a dollar sign and ends with a numeric value.

4. Play the test case and verify the **Log** view results.

    <a class="pop">
    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/extract-and-verify-textual-patterns/KR-5.8.0-Log-view-results.png" width=100% alt="Katalon Recorder Log view results">
    </a>
    <p style="text-align: center;"><em>Click the image to enlarge</em></p>