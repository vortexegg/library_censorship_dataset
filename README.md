# Library Censorship Dataset

This dataset was created for Data Curation course at the University of Washington iSchool. It is a collection of various data related to library and educational censorship between 2016 and 2022. The intended audience is the general public, in particular citizen activists and researchers, with the goal of building a public understanding of past and ongoing censorship activities, as well as an awareness of the present state of open data availability about this topic.

The dataset is available as three .csv files collected from the following sources:

1. Source: [School Library Journal's Controversial Books Survey on Self-Censorship](https://www.slj.com/page/features-self-censorship)
    - File: [2016-slj-controversial_books_survey.csv](/data/2016-slj-controversial_books_survey.csv)
2. Source: [National Coalition Against Censorship's Youth Censorship Database](https://ncac.org/youth-censorship-database)
    - File: [2022-ncac-youth_censorship_database.csv](/data/2022-ncac-youth_censorship_database.csv)
3. Source: [PEN America's Educational Gag Orders Index](https://pen.org/steep-rise-gag-orders-many-sloppily-drafted/)
    - File: [2022-pen_america-educational_gag_orders.csv](/data/2022-pen_america-educational_gag_orders.csv)

## Table of Contents

- [Directory Structure](#directory-structure)
- [Naming](#naming)
- [Data Normalization](#data-normalization)
- [Data Dictionary](#data-dictionary)
    - [1. Documentation for SLJ Controversial Books Survey dataset](#1-documentation-for-slj-controversial-books-survey-dataset)
    - [2. Documentation for NCAC Youth Censorship Database dataset](#2-documentation-for-ncac-youth-censorship-database-dataset)
    - [3. Documentation for PEN America Educational Gag Orders dataset](#3-documentation-for-pen-america-educational-gag-orders-dataset)
- [Metadata](#metadata)
    - [ A. Metadata for SLJ Controversial Books Survey dataset](#a-metadata-for-slj-controversial-books-survey-dataset)
    - [B. Metadata for NCAC Youth Censorship Database dataset](#b-metadata-for-ncac-youth-censorship-database-dataset)
    - [C. Metadata for PEN America Educational Gag Orders dataset](#c-metadata-for-pen-america-educational-gag-orders-dataset)
- [Security](#security)

## Directory Structure

This dataset repository contains the following directories:

```code
/data           # The curated data files belonging to the dataset
/notebooks      # Jupyter notebooks used to fetch and normalize the data, not part of the dataset
/unprocessed    # The original un-normalized data files as retrieved from the sources, not part of the dataset
README.md       # This project documentation
```

_Note: The Jupyter notebooks and unprocessed files are included in this repository for archival and reference purposes only. They are not considered to be a part of the curated dataset for purposes of data sharing, nor are they included in the data documentation below._

## Naming

The naming convention of the dataset files is as follows:

`year-source-original_data_set.csv`

This naming scheme is composed of the following parts:

- `year`: The year on which the data is being reported (or final year, if the dataset includes a range).
- `source`: A short name for the organization that was the source of the data.
- `original_data_set`: The name of the original report, index, or database that the curated data was originally drawn from.

## Data Normalization

Each of the data files was normalized with some variation of the following processing steps:

- Split out embedded HTML hyperlink URLs into their own columns from the anchor text
- Split out columns that contained multiple categorical values within a single column into separate unique columns each with a single, one-hot encoded, value
- Replace empty cells with the placeholder value "N/A"
- Rename column headers/field names to have a consistent standard (all lowercase, underscores)
- Replace newline characters within columns with an appropriate separator
- Clean up incorrectly encoded characters
- Remove empty rows

The specific normalization that was applied to each file is documented in the three Jupyter notebooks included in [/notebooks](/notebooks/).

## Data Dictionary

_Note: The data dictionary does not include a **Measurement Unit** column as none of the values represents a measurement taken in a particular unit._

### 1. Documentation for SLJ Controversial Books Survey dataset

[2016-slj-controversial_books_survey.csv](/data/2016-slj-controversial_books_survey.csv):

| **Variable** | **Variable Name** | **Variable Type**  | **Allowed Values** | **Definition** |
| --- | --- | --- | --- | --- |
| **survey_name** | Survey Name | String | [Weighing Subject Matter, Comments About Age-Appropriateness, Comments About Book Challenges] | The name of the particular survey question the observation is in response to |
| **librarian_comments** | Librarian Comments | String | Any | The comment by the librarian responding to the survey question |
| **region** | Region | String | [Midwest, Mountain, Northeast, Pacific, South Atlantic, South Central] | The general region of the US where the response is from |
| **locality** | Locality | String | [Rural, Small Town, Suburban, Urban] | The type of community area based on general population level |
| **elementary_school** | Elementary School Level | Integer | 0 or 1 | Whether this response applies to an Elementary School level (Pre K - 5) |
| **middle_school** | Middle School Level | Integer | 0 or 1 | Whether this response applies to a Middle School level (6 - 8) |
| **high_school** | High School Level | Integer | 0 or 1 | Whether this response applies to a High School level (9 - 12) |

### 2. Documentation for NCAC Youth Censorship Database dataset

[2022-ncac-youth_censorship_database.csv](/data/2022-ncac-youth_censorship_database.csv):

| **Variable** | **Variable Name** | **Variable Type** | **Allowed Values** | **Definition** |
| --- | --- | --- | --- | --- |
| **summary** | Summary | String | Any | A summary of the nature or target of the censorship incident |
| **censor_reason** | Censor Reason | String | Any | The reason provided as justification for censorship |
| **link** | Link | String | Any | A link to additional information or new article about the incident |
| **type** | Type | String | Any | A categorization of the type of thing the censorship applied to |
| **year** | Year | Date | YYYY | The year in which the incident occurred |
| **challenger** | Challenger | String | Any | The nature of the person or entity issuing the censorship challenge |
| **book_theme** | Book Theme | String | Any | The theme of the book that is subject to the challenge, if relevant, otherwise N/A |
| **school_district** | School District | String | Any | The name of the school district where the challenge occurred |
| **notes** | Notes | String | Any | Additional details related to the incident |
| **state** | State | String | US State names | The name of the US state where the incident occurred |
| **impacted_high_school** | High School Impacted | Integer | 0 or 1 | Whether the impacted population was a High School |
| **impacted_public_library** | Public Library Impacted | Integer | 0 or 1 | Whether the impacted population was a Public Library |
| **impacted_elementary_school** | Elementary School Impacted | Integer | 0 or 1 | Whether the impacted population was an Elementary School |
| **impacted_middle_school** | Middle School Impacted | Integer | 0 or 1 | Whether the impacted population was a Middle School |
| **impacted_K-12** | K-12 Impacted | Integer | 0 or 1 | Whether the impacted population was K - 12 students |
| **impacted_P-8** | P-8 Impacted | Integer | 0 or 1 | Whether the impacted population was Preschool through 8th students |

### 3. Documentation for PEN America Educational Gag Orders dataset

[2022-pen_america-educational_gag_orders.csv](/data/2022-pen_america-educational_gag_orders.csv):

| **Variable** | **Variable Name** | **Variable Type** | **Allowed Values** | **Definition** |
| --- | --- | --- | --- | --- |
| **state** | State | String | Any | The US state where the gag order occurred |
| **bill_number** | Bill Number | String | Any | The bill number of the bill introducing the gag order |
| **date_introduced** | Date Introduced | Date | YYYY-MM-DD | The date when the order was introduced |
| **status** | Status | String | Any | The present legal status of the order |
| **primary_sponsor** | Primary Sponsor | String | Any | The primary person or organization sponsoring the bill |
| **description** | Description | String | Any | A description of what the gag order disallows within the targeted institutions |
| **enforcement_penalties** | Enforcement/Penalties | String | Any | The legal penalties stipulated for violating the gag order |
| **bill_hyperlink** | Bill Hyperlink | String | Any | A link to additional documentation about the bill's details |
| **status_hyperlink** | Status Hyperlink | String | Any | A link to additional documentation about the present status of the bill |
| **targets_k-12** | Targets K-12 | Integer | 0 or 1 | Whether the order targets K - 12 schools |
| **targets_colleges** | Targets Colleges | Integer | 0 or 1 | Whether the order targets Colleges |
| **targets_state_institutions** | Targets State Institutions | Integer | 0 or 1 | Whether the order targets State Institutions |
| **targets_state_contractors** | Targets State Contractors | Integer | 0 or 1 | Whether the order targets State Contractors |
| **targets_state_agencies** | Targets State Agencies | Integer | 0 or 1 | Whether the order targets State Agencies |
| **targets_political_subdivisions** | Targets Political Subdivisions | Integer | 0 or 1 | Whether the order targets Political Subdivisions |
| **targets_charter_schools** | Targets Charter Schools | Integer | 0 or 1 | Whether the order targets Charter Schools |
| **targets_employers** | Targets Employers | Integer | 0 or 1 | Whether the order targets Employers |
| **targets_state_contractor** | Targets State Contractors | Integer | 0 or 1 | Whether the order targets State Contractors |
| **targets_state_entities** | Targets State Entities | Integer | 0 or 1 | Whether the order targets State Entities |
| **targets_private_business** | Targets Private Businesses | Integer | 0 or 1 | Whether the order targets Private Businesses |
| **targets_non-profits** | Targets Non-Profits | Integer | 0 or 1 | Whether the order targets Non-Profits |
| **targets_tax_exempt_organizations** | Targets Tax Exempt Organizations | Integer | 0 or 1 | Whether the order target Tax Exempt organizations |

## Metadata

Schema: [Dublin Core](https://www.dublincore.org)

### A. Metadata for SLJ Controversial Books Survey dataset

| Attribute | Value |
| -- | -- |
| Title | SLJ Controversial Books Survey dataset |
| Creator | School Library Journal |
| Subject | censorship, libraries, librarians, self-censorship, survey-results |
| Description | Data containing survey responses from school library personnel about self-censorship from 2016 |
| Contributor | Scott Johnson |
| Coverage | Spatial: United States, Temporal: 2016 |
| Date | Created: 2022-03-01 |
| Type | Dataset |
| Format | CSV |
| Source | https://www.slj.com/page/features-self-censorship |
| Audience | General public |
| Language | English |
| Relation | N/A |
| Identifier | https://github.com/vortexegg/library_censorship_dataset/blob/main/data/2016-slj-controversial_books_survey.csv |

### B. Metadata for NCAC Youth Censorship Database dataset

| Attribute | Value |
| -- | -- |
| Title | NCAC Youth Censorship Database dataset |
| Creator | National Coalition Against Censorship |
| Subject | censorship, schools, libraries, youth, challenges |
| Description | Data of censorship incidents affecting K-12 students |
| Contributor | Scott Johnson |
| Coverage | Spatial: United States, Temporal: 2018-2022 |
| Date | Created: 2022-03-01 |
| Type | Dataset |
| Format | CSV |
| Source | https://ncac.org/youth-censorship-database |
| Audience | General public |
| Language | English |
| Identifier | https://github.com/vortexegg/library_censorship_dataset/blob/main/data/2022-ncac-youth_censorship_database.csv |

### C. Metadata for PEN America Educational Gag Orders dataset

| Attribute | Value |
| -- | -- |
| Title | PEN America Educational Gag Orders dataset |
| Creator | PEN America |
| Subject | censorship, schools, libraries, gag orders, education, challenges, bills |
| Description | Data of bills stipulating legal gag orders and their enforcement |
| Contributor | Scott Johnson |
| Coverage | Spatial: United States, Temporal: 2021 - 2022  |
| Date | Created: 2022-03-01 |
| Type | Dataset |
| Format | CSV |
| Source | https://pen.org/steep-rise-gag-orders-many-sloppily-drafted/ |
| Audience | General public |
| Language | English |
| Identifier | https://github.com/vortexegg/library_censorship_dataset/blob/main/data/2022-pen_america-educational_gag_orders.csv |

## Security

While the original data are publicly available on the websites of their respective sources, they are offered there without any explicit data license agreement. They are collected and offered here with an understanding that any attempt should be made to request permission from the originators before this data is incorporated into any downstream data product.
