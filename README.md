# Library Censorship Dataset

This dataset was created for Data Curation course at the University of Washington iSchool. It is a collection of various data related to library and educational censorship between 2016 and 2022. The intended audience is the general public, in particular citizen activists and researchers, with the goal of building a public understanding of past and ongoing censorship activities, as well as an awareness of the present state of open data availability about this topic.

The dataset is available as three .csv files collected from the following sources:

1. [School Library Journal's Controversial Books Survey on Self-Censorship](https://www.slj.com/page/features-self-censorship):
    - File: `2016-slj-controversial_books_survey.csv`
2. [National Coalition Against Censorship's Youth Censorship Database](https://ncac.org/youth-censorship-database)
    - File: `2022-ncac-youth_censorship_database.csv`
3. [PEN America's Educational Gag Orders Index](https://pen.org/steep-rise-gag-orders-many-sloppily-drafted/)
    - File: `2022-pen_america-educational_gag_orders.csv`

## Table of Contents

- [Directory Structure](#directory-structure)
- [Naming](#naming)
- [Data Normalization](#data-normalization)
- [Data Dictionary](#data-dictionary)
- [Metadata](#metadata)
- [Security](#security)
- [Contact](#contact)

    How data have been normalized
    The file naming convention that your dataset uses
    Any information about variable names, definitions etc. (you may choose to structure this like a data dictionary)

## Directory Structure

This dataset repository contains the following directories:

```code
/data           # The curated data files belonging to the dataset
/notebooks      # Jupyter notebooks used to fetch and normalize the data
/unprocessed    # The original un-normalized data files as retrieved from the sources, not part of the dataset
README.md       # This project documentation
```

_Note: The unprocessed data files are included in this repository in the state that they were retrieved from the sources as an archive for reference purposes.
However they are not considered a part of the curated dataset for purposes of documentation or sharing._

## Naming

The naming convention of the files is as follows:

`year-source-originaldataset.csv`

Which is composed of the following parts

- `year`: The year on which the data is being reported (or final year, if the dataset includes a range).
- `source`: A short name for the organization that was the source of the data.
- `originaldataset`: The name of the original report, index, or database that the curated data was originally drawn from.

## Data Normalization

Each of the data files was normalized with some variation of the following processing steps:

## Data Dictionary

## Metadata

## Security

While the original data are publicly available on the websites of their respective sources, they are offered there without any explicit data license agreement. They are collected and offered here with an understanding that any attempt should be made to request permission from the originators before this data is incorporated into any downstream data product.

## Contact

Scott Johnson
scott.philips.johnson@gmail.com
