---
title: "How to Use Control Flow commands in a Test Case"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-recorder/docs/how-to-use-conditional-statements-in-a-test-case.html
description:
---

Katalon Recorder allows you to control test execution flow with control flow commands. To learn more about available control flow commands, you can refer to this document: [Handle conditional cases in your tests](https://docs.katalon.com/katalon-recorder/docs/conditional-cases.html).

This tutorial shows you how to use control flow commands in a test case.

> **Notes**:
>
> * To use the sample project of this tutorial, navigate to **Actions** > **Sample Projects**, then add the **Implement control flow in a test case** project.

## Test case scenario

In our example, we have a test case with the scenario "Adding items to the shopping cart," which consists of these steps:

1. Navigate to the application under test (AUT): `https://cms.demo.katalon.com`.
2. Select a few items with the text "Add to cart."
3. Verify that, on the right corner of the selected item, there's a confirmation text "View cart" visible.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/conditional-and-loop-tutorial/KR-5.8.0-AUT-Overview.png" width=100% alt="AUT Overview">

We can use control flow commands to automate the task of selecting and verifying the items. The process is as follows:

1. Record the test case: we record the test case to select and verify a few items manually.
2. Create a test case using control flow commands: we analyze the test execution flow and create a new test case using control flow commands.

## Record the test case

Here we record the test case to first select and verify *four* items.

Follow these steps:

1. In Katalon Recorder, create a new test case, then click on the **Record** button to start recording.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/conditional-and-loop-tutorial/KR-5.8.0-New-test-case.png" width=100% alt="KR New test case">

2. In an active browser tab, navigate to the AUT.

    Here the URL for the AUT is `https://cms.demo.katalon.com`.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/conditional-and-loop-tutorial/KR-AUT-Katalon-Zack-Market.png" width=100% alt="KR Application Under Test">

3. Add items to the cart. On the opened page, hover over the displayed items and select the item with the text "Add to cart."

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/conditional-and-loop-tutorial/KR-AUT-Select-an-item.png" width=100% alt="KR Select an item to add to cart">

4. Verify that the item is added to the cart successfully. Right-click on the confirmation text `"View cart"` and select **Katalon Recorder > verifyText**.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/conditional-and-loop-tutorial/KR-AUT-VerifyText.png" width=100% alt="KR Select an item to add to cart">

5. Repeat *step 3* and *step 4* for three more items on the page.

The recorded test case is as follows:

<a class="pop">
<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/conditional-and-loop-tutorial/KR-5.8.0-test-case-recorded-target.png" width=100% alt="Recorded test case">
</a>
<p style="text-align: center;"><em>Click the image to enlarge</em></p>

## Create a test case using control flow commands

### Analyze the test execution flow

We first analyze the recorded test case to identify where we can apply control flow commands.

The recorded test case shows that the `click` and `verifyText` commands are repeatedly used.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/conditional-and-loop-tutorial/KR-5.8.0-test-case-recorded-repeated-steps.png" width=100% alt="Repeated commands in the test case">

The **Target** fields of the `click` and `verifyText` commands are:

<table>
    <thead>
        <tr>
            <th>Command</th>
            <th>Target</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><em>click</em></td>
            <td><code>xpath=//main[@id='main']/div[2]/ul/li[{index value}]/div/a[2]</code></td>
        </tr>
        <tr>
            <td><em>verifyText</em></td>
            <td><code>xpath=//main[@id='main']/div[2]/ul/li[{index value}]/div/a[3]</code></td>
        </tr>
    </tbody>
</table>

From the XPath in the **Target** field, we can see that each item has a unique index value. The associated index value is incremented because the items are selected from the top to the bottom of the page.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/conditional-and-loop-tutorial/KR-5.8.0-test-case-recorded-patterns.png" width=100% alt="Repeated commands in the test case">

Knowing that each item is associated with one index value, we can use control flow commands to automatically iterate over, select, and verify all 12 items on the page.
### Use control flow commands in a test case

Here we propose the following control flow:

<a class="pop">
<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/conditional-and-loop-tutorial/control-flow.png" width=100% alt="Proposed flowchar">
</a>
<p style="text-align: center;"><em>Click the image to enlarge</em></p>

The specific steps in the proposed control flow are:

1. Open the AUT.
2. Get the index value of the current item.
3. Check if the index is valid; otherwise, the test case ends.
4. On the item, if there's a text "Add to cart" visible, click on the text; otherwise, skip to *step 6*.
5. Verify that the added item has the text "View cart" visible.
6. Move on to the next item, and continue with *step 2*.

To apply control flow commands, follow these steps:

1. Create a new test case.

    With the `open` command, navigate to the AUT.

    The URL for the AUT is `https://cms.demo.katalon.com`.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/conditional-and-loop-tutorial/KR-5.8.0-open-command.png" width=100% alt="KR open command">

    | Command                    | Target                      | Value                                                       |
    |----------------------------|-----------------------------|-------------------------------------------------------------|
    | `open` | `https://cms.demo.katalon.com` |  |

2. Get the index value of the current item.

    Here we represent the index value with the variable `index` and use the `store` command to set the first value for the variable.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/conditional-and-loop-tutorial/KR-5.8.0-store-command-index.png" width=100% alt="KR store command">

    | Command                    | Target                      | Value                                                       |
    |----------------------------|-----------------------------|-------------------------------------------------------------|
    | `store` | `1` | `index` |

3. Check if the index value is valid.

    Since we want to iterate over all 12 items on the page, we use the `while` control flow command to start a loop. 

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/conditional-and-loop-tutorial/KR-5.8.0-while-command.png" width=100% alt="KR while command">

    | Command                    | Target                      | Value                                                       |
    |----------------------------|-----------------------------|-------------------------------------------------------------|
    | `while` | `${index} < 13` | |


    Here the `while` command checks if the index value is valid using the expression `${index} < 13`. The placeholder syntax `${index}` expands the `index` variable into its value.

4. Check if there's a text "Add to cart" visible, then click on the text.

    Here we use the three following commands:
    
    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/conditional-and-loop-tutorial/KR-5.8.0-storeText-if-click.png" width=100% alt="KR storeText, if, click commands">

    | Command                    | Target                      | Value                                                       |
    |----------------------------|-----------------------------|-------------------------------------------------------------|
    | `storeText` | `xpath=//main[@id='main']/div[2]/ul/li[${index}]/div/a[2]` | `itemText` |
    | `if` | `"${itemText}" == "Add to cart"` | `itemText` |
    | `click` | `xpath=//main[@id='main']/div[2]/ul/li[${index}]/div/a[2]` | |
    
    We first use the `storeText` command to store the displayed text of the item into a variable. Then we use the `if` conditional command to check if the stored text equals "Add to cart." If the `if` command evaluates to `true`, we use the `click` command to select the text.

    Here XPath for the text "Add to cart" is `xpath=//main[@id='main']/div[2]/ul/li[${index}]/div/a[2]`.

5. Verify that the added item has the text "View cart" visible.

    Here we use the `verifyText` command.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/conditional-and-loop-tutorial/KR-5.8.0-verifyText-command.png" width=100% alt="KR verifyText command">

    | Command                    | Target                      | Value                                                       |
    |----------------------------|-----------------------------|-------------------------------------------------------------|
    | `verifyText` | `xpath=//main[@id='main']/div[2]/ul/li[${index}]/div/a[3]` | `View cart` |

    The XPath for the text "View cart" is `xpath=//main[@id='main']/div[2]/ul/li[${index}]/div/a[3]`.

    The `click` and `verifyText` commands execute only when the `if` command evaluates to `true`. Therefore, we use the `endIf` command to terminate the conditional.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/conditional-and-loop-tutorial/KR-5.8.0-endIf-command.png" width=100% alt="KR endIf command">


6. Move on to the next item.

    To continue selecting and verifying the next item, we use the `storeEval` command to increment the value of the `index` variable.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/conditional-and-loop-tutorial/KR-5.8.0-storeEval-command.png" width=100% alt="KR storeEval command">

    | Command                    | Target                      | Value                                                       |
    |----------------------------|-----------------------------|-------------------------------------------------------------|
    | `storeEval` | `${index} + 1` | `index` |

    The **Target** of the `storeEval` command is the expression `${index} + 1`. This expression increments the value of the `index` variable by 1. As a result, the execution flow continues with the next item on the page.

    The clicking and verifying steps execute inside the `while` loop. Therefore, we use the `endWhile` command to terminate the loop.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/conditional-and-loop-tutorial/KR-5.8.0-endWhile.png" width=100% alt="KR endWhile command">

7. Play the test case and verify the results in the **Log** section.

    The test case should select all the items with the "Add to cart" button from the top to the bottom of the page.

    <a class="pop">
    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/conditional-and-loop-tutorial/KR-5.8.0-test-case-results.png" width=100% alt="KR execution results">
    </a>
    <p style="text-align: center;"><em>Click the image to enlarge</em></p>
