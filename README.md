# SQL Data Cleaning Project — Layoffs Dataset

## Project Overview

This guided project was completed as part of **Alex The Analyst's Data Analyst Bootcamp** and focused on cleaning and preparing a layoffs dataset for analysis using **MySQL**.

The project involved identifying duplicate records, standardising inconsistent data, handling NULL and blank values, and correcting data types and formatting issues.

## Tools Used

* MySQL
* SQL
* MySQL Workbench

## Dataset

The dataset contains information related to company layoffs, including fields such as:

* Company
* Location
* Industry
* Total Laid Off
* Percentage Laid Off
* Date
* Country
* Funds Raised

## Data Cleaning Process

### 1. Creating Staging Tables

I created a copy of the original dataset and worked on the staging table instead of modifying the original data. This provided a backup that could be referred to if mistakes were made during the cleaning process.

A second staging table was also created to store the results of the duplicate identification process.

### 2. Removing Duplicates

I used a **CTE** and the **ROW_NUMBER() window function** to identify duplicate records.

The `ROW_NUMBER()` function assigned a sequential number to records within groups of related rows. Records with a row number greater than 1 were identified as duplicates.

After identifying the duplicate records, I removed them from the staging table using `DELETE`.

### 3. Standardising Data

I identified and corrected several inconsistencies in the dataset.

This included:

* Removing unnecessary whitespace from company names using `TRIM()`.
* Standardising inconsistent industry values, including different variations of cryptocurrency-related entries.
* Removing an unnecessary full stop from a country value using `TRIM()` and `TRAILING`.
* Converting the date column from text into a proper date format using `STR_TO_DATE()`.
* Changing the date column's data type to `DATE` using `ALTER TABLE`.

### 4. Handling NULLs and Blank Values

I investigated NULL and blank values in the industry column.

A **self-join** was used to identify cases where information from another record belonging to the same company could be used to populate a missing industry value.

For example, where one Airbnb record contained the industry value `Travel` and another Airbnb record had a blank industry value, the missing value could be populated using the available information.

Where reliable information was not available, the missing values were left unchanged rather than making assumptions.

### 5. Removing Unnecessary Data

I reviewed the remaining NULL values and identified rows and columns that did not contain useful information for the dataset.

Unnecessary data was removed, including the temporary `row_num` column that had been created during the duplicate-removal process.

**Project Screenshots**:

Original Dataset

The original dataset contained several data-quality issues, including duplicate records, inconsistent values, blank fields, and incorrect date formatting.



Identifying Duplicate Records

I used a CTE and the ROW_NUMBER() window function to identify duplicate records before removing them.



Standardising Data

I used SQL functions and statements including TRIM(), UPDATE, STR_TO_DATE(), and ALTER TABLE to standardise and correct inconsistent data.



Final Cleaned Dataset

After completing the cleaning process, the dataset was left in a cleaner and more consistent format for further analysis.

## SQL Concepts Practised

Through this project, I practised:

* CTEs
* Window functions
* `ROW_NUMBER()`
* `TRIM()`
* `STR_TO_DATE()`
* `UPDATE`
* `DELETE`
* `ALTER TABLE`
* Self-joins
* Handling NULL and blank values
* Data standardisation
* Data type conversion
* Working with staging tables

## Key Learning

This project helped me understand the practical process of preparing raw data for analysis. I gained experience identifying data-quality issues, deciding how they should be handled, and using SQL to transform inconsistent data into a cleaner and more analysis-ready dataset.

## Project Type

**Guided Learning Project**
Completed as part of Alex The Analyst's Data Analyst Bootcamp.

