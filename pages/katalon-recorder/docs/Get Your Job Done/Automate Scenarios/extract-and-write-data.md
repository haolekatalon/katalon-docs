---
title: "How to extract and write data in a test case"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-recorder/docs/write-and-extract-data.html
description: "How to extract and write data from a website in a test case."
---

When testing a website with Katalon Recorder, you might want to extract data from the website and store the data in an external file. Katalon Recorder facilitates this process of extracting and writing data with several commands.

This tutorial shows you how to use Katalon Recorder to extract data from a website and write the data to a CSV file.

> **Notes**:
>
> * To use the sample project of this tutorial, navigate to **Actions** > **Sample Projects**, then add the **Extract and write data to a CSV file** project.

## Test case scenario

In our example, we follow the scenario "extract and write product information to a file", which consists of these steps:

1. Navigate to the application under test (AUT) - the Katalon Zack Market page: `https://demo-store.katalon.com/`.
2. Select a shopping item.
3. On the item page, get the name and price of the selected item.
4. Write the name and price information to a CSV file.

The item page displays the item with name and price as follows:

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/write-and-extract-data/AUT-overview.png" width=100% alt="Overview of the AUT">

We can use Katalon Recorder to first extract and store the item name and price. Then with the `appendToCSV` command, we can append the extracted data to a CSV file.

## Prepare a CSV file

As Katalon Recorder navigates using column names in a CSV file, we need to create a CSV file with specific column names for data extraction. In our case, we need two columns for name and price.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/write-and-extract-data/KR-Sample-CSV.png" width=70% alt="Prepared CSV file">

## Add the CSV file to the workspace

Follow these steps:

1. Open Katalon Recorder. In the **Workspace** sidebar, click on **Open a Data File** in the **Test Data** section.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/write-and-extract-data/KR-5.8.0-Add-test-data.png" width=100% alt="Test Data section">

2. In the displayed file explorer, select the CSV file.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/write-and-extract-data/KR-5.8.0-file-explorer.png" width=100% alt="File dialog">

    The added CSV file is displayed under the **Test Data** section.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/write-and-extract-data/KR-5.8.0-Added-test-data.png" width=100% alt="Added CSV file">

## Extract and write the data

After adding the CSV file to the workspace, we create a test case that navigates to the shopping item page, then extracts and writes item information to the CSV file.

Follow these steps:

1. In Katalon Recorder, create a test suite, then create a test case inside that test suite. Click **Record** to start recording.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/write-and-extract-data/KR-5.8.0-New-test-case.png" width=100% alt="KR new test case">

2. In an active browser tab, navigate to the AUT - Katalon Zack Market: `https://demo-store.katalon.com`.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/write-and-extract-data/KR-5.8.0-AUT-page.png" width=100% alt="AUT page">

3. Click on a shopping item.

4. Get the item name and price.

    While recording a test case, you can manually add a test step for an element by right-clicking on it.

    To get item name, right-click on the name text and select **Katalon Recorder** > **storeText**.

    <a class="pop">
    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/write-and-extract-data/KR-5.8.0-right-click-store-text-cropped.png" width=100% alt="KR Right-click on AUT">
    </a>
    <p style="text-align: center;"><em>Click the image to enlarge it</em></p>

    Katalon Recorder then asks you to enter the variable name that stores the name text. Here, we name the variable `itemName`. 

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/write-and-extract-data/KR-5.8.0-Enter-variable-name-for-item-name.png" width=100% alt="KR Right-click on AUT">

    To get the item price, right-click on the price text and select **Katalon Recorder** > **storeText**.

    <a class="pop">
    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/write-and-extract-data/KR-5.8.0-right-lick-store-text-item-price-cropped.png" width=100% alt="KR Right-click on AUT">
    </a>
    <p style="text-align: center;"><em>Click the image to enlarge it</em></p>

    Here, we name the variable for the price text `itemPrice`.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/write-and-extract-data/KR-5.8.0-Enter-variable-name-for-item-price.png" width=100% alt="KR Right-click on AUT">


5. Click **Stop** to stop the test recording.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/write-and-extract-data/KR-5.8.0-stop-button.png" width=100% alt="KR Stop button">

6. Write the name and price to the CSV file.

    In the test case recorded, we add another test step and use the `appendToCSV` command to write the name and price to the added CSV file.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/write-and-extract-data/KR-5.8.0-appendToCSV-command.png" width=100% alt="KR appendToCSV command">

    | Command                    | Target                      | Value                                                       |
    |----------------------------|-----------------------------|-------------------------------------------------------------|
    | `appendToCSV` | `name-price.csv` | `${itemName}, ${itemPrice}` |

    The **Target** here is the name of the added CSV file.
    
    In the **Value** field, we specify the values to write to the CSV file: `${itemName}` and `${itemPrice}`. The placeholder syntax `${variable_name}` here expands a variable into its value. As a result, when Katalon Recorder runs the `appendToCSV` command, it writes the name and price values to the next empty row of the `name-price.csv` file.

7. Play the test case until it finishes and download the CSV file.

    <a class="pop">
    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/write-and-extract-data/KR-5.8.0-click-download-test-data.png" width=100% alt="KR Download the CSV file">
    </a>
    <p style="text-align: center;"><em>Click the image to enlarge it</em></p>

8. Open the downloaded CSV file and verify the results.

    The downloaded CSV file should display the extracted item name and price.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-recorder/docs/write-and-extract-data/Downloaded-CSV.png" width=100% alt="View the downloaded CSV file">

> **Notes**:
>
> * As a browser extension, Katalon Recorder cannot write data directly to the user file system; the extension only writes to the version of the data file that is added to the workspace. Therefore, you need to download the data file again to view the extracted data.