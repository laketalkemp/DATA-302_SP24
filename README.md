# CAN-GRAIN Project

An analysis of global crop productivity and its relationship to intellectual property rights for plant breeders.

## Stakeholders
[GRAIN](https://grain.org/) is an international nonprofit organization established in 1990 and headquartered in Barcelona, Spain.  Its mission is to support small farmers and social movements in their quest for community-controlled and biodiversity-based food systems, primarily in Africa, Asia, and Latin America.

[The University of Chicago Data Science Institute](https://datascience.uchicago.edu/) (DSI), founded in 2021, executes the university's bold, innovative vision of Data Science as a new discipline. Through a grant received from the 11th Hour Project run by the Schmidt Family Foundation, its staff consults with social impact organizations to provide technical solutions at no cost. 

## Background

Plant breeding is essential for achieving food security in the context of modern population growth and climate change.  Improved plant fertility, pest and disease resistance, salt and drought tolerance, and nutrient absorption, among other adaptations, result in larger crop yields while minimizing harm to the natural environment. However, successful plant breeding requires expertise, time (10-15 years for many species), and to scale, significant investments in land and specialized equipment like greenhouses, growth chambers, and laboratories. 

The [International Union for the Protection of New Varieties of Plants](https://www.upov.int/portal/index.html.en) (UPOV)—an intergovernmental organization founded in 1961 and based in Geneva, Switzerland—argues that plant breeders must be incentivized to continue their work given that a new plant variety can easily be reproduced and reused by others once discovered.  To safeguard economic profits for breeders, UPOV has developed a "blueprint" regulatory framework of intellectual property rights (i.e., the UPOV Convention) that awards breeders monopolies on new plant varieties and requires other farmers to seek their authorization for marketing and sale of the varieties (e.g., through licensing fees). Today, a country or intergovernmental organization can become a member of UPOV by adapting the intellectual property laws in the UPOV Convention to their own legal jurisdictions.  As of May 2023, UPOV had 78 members representing more than a third of the world’s countries.

However, this growth in membership has not been without controversy.  Grassroots organizations and nonprofits like GRAIN argue that UPOV favors seeds from “Big Ag” companies like Bayer (who acquired Monsanto), Syngenta, Corteva, and BASF over those from small farmers. These companies typically grow export crops using _monoculture farming_, an unsustainable practice that depletes the soil of nutrients over time and requires extensive irrigation, fertilizers, and pesticides that harm the environment. On June 1st, 2023, a coalition of farmers’ organizations, women’s organizations, trade activists, and consumer groups released a joint statement to express their concern over Benin’s potential membership in UPOV, urging the nation to protect its food sovereignty from foreign companies and promote the use of indigenous seeds better adapted to the local environment. The outcome of these efforts is still to be determined, but they hope to continue lobbying against UPOV.

## Problem

GRAIN suspects that the growth of the UPOV has **not** resulted in larger crop yields over time and would like to test their hypothesis by analyzing publicly available data from the [Food and Agriculture Organization](https://www.fao.org/faostat/en/#data/QCL) (FAO) of the United Nations. This dataset records hectares of land area harvested and tons of output produced for different primary crops (e.g., almonds, papayas, avocadoes) each year from 1961 to 2021 for over 200 countries.  It is also supplemented by additional datasets listing standardized country codes, units of measurement, and quality control flags and countries' membership in UPOV over time.

An exploratory data analysis (EDA) could explore the following questions:

- How are crop types currently distributed across countries, and how has this changed over time, if at all?
- For each crop type, has there been an overall increase or decrease in the number of tons produced? In the area harvested?  Are there certain countries where production or land area of the crop has dramatically increased or decreased? Explain.
- For each country, how has the total area harvested and tons of crops produced changed over time? Cross-reference these time series with current events to better understand why this might be the case.
- How are the quality flags (official figure, estimate value, imputed value, etc.) distributed across the dataset? Is data collected for certain years or geographic areas seemingly more robust?

Meanwhile, our main research questions are as follows:

- Is membership in UPOV positively correlated with, or predictive of, higher crop yields?  Is the effect noticeable after a certain amount of time has passed since joining?
- What effect does joining UPOV have on the area harvested of specific crops? Are there crops that seem to have been more affected?  If so, conduct a case study of one to two crops to better understand what factors may have contributed to that outcome.

## Expected Deliverables

Each team is expected to turn in:

1. A Python script with functions to clean and standardize the crop dataset.
2. An EDA that loads the data and then answers the questions above using one or more Jupyter notebooks.
3. A Jupyter notebook that explores the correlation between UPOV membership and crop yields and determines the extent to which UPOV membership is predictive of yields.
4. A Jupyter notebook that explores the effect joining UPOV had on the area harvested for different crops.
5. A written (2-3 pages) or digital report that walks through your data, methodology, analysis, and conclusions and provides data visualizations.

## Working with the Data

This repository only contains the data for use by this project. All datasets are saved as comma-separated files and can be read by any analysis tool which opens standard CSV. 

The data in this repository should be considered a starting point for this project. There are numerous directions that the analysis could go and leveraging additional datasets to support your conclusions is strongly encouraged.

## Data Dictionary

### faostat_country_codes.csv

This CSV file maps country names to United Nations country codes and ISO2 and ISO3 codes from the [International Organization for Standardization](https://www.iso.org/about-us.html). It was downloaded directly from the FAOSTAT website.

| Column Name  | Data Type | Description | Example Value |
| ------------- | ------------- | ------------- | --|
| Country Code  | String  |  A likely auto-generated code. | `"2"` |
| Country |  String  | The country name. | `"Afghanistan"` |
| M49 Code |  String  | The United Nations M49 standard code. | `"'004"` |
| ISO2 Code |  String  | The ISO2 standard code. | `"AF"` |
| ISO3 Code |  String  | The ISO3 standard code. | `"AFG"` |
| Start Year |  Integer  | --- | --- |
| End Year |  Integer  | --- | --- |

### faostat_crops.csv

This CSV file contains information on crop production and harvested area size over time for different countries. It was downloaded directly from the FAOSTAT website. Please note that data cleaning should drop irrelevant columns and only keep the `Area harvested` and `Production` metrics.

| Column Name  | Data Type | Description | Example Value |
| ------------- | ------------- | ------------- | ---|
| Area Code |  String  |  A unique identifer for the country. Likely automatically generated. | `"2"` |
| Area Code (M49) |  String  | A unique identifer for the country. Uses the United Nations' M49 standard. | `"'004"` |
| Area |  String  | The country name. | `"Afghanistan"` |
| Item Code |  String  | A unique identifier for the crop grown. Likely automatically generated. | `"221"` |
| Item Code (CPC) |  String  | A unique identifier for the crop grown. Uses the Central Product Classification System standard. | `"'01371"` |
| Item |  String  | The crop name. | `"Almonds, in shell"` |
| Element Code |  String  | A unique identifier for the metric observed. | `"5312"` |
| Element |  String  | The name of the metric observed. | `"Area harvested"` |
| Unit |  String  | The units used to measure the metric. | `"ha"` |
| Y**** |  String  | The value of the metric for the given year. In the column name, the asterisks are replaced by a year (e.g., `Y1976`). | `"5900"` |
| Y****F |  String  | The quality control flag for the metric in the given year. In the column name, the asterisks are replaced by a year (e.g., `Y1976F`).| `"E"` |
| Y****N |  String  | Notes about the quality control flag used for the metric. In the column name, the asterisks are replaced by a year (e.g., `Y1976N`).| `"Unofficial figure"` |

### faostat_flags.csv

This CSV file describes the meaning of each quality control flag in the crop dataset. It was downloaded directly from the FAOSTAT website.

| Column Name  | Data Type | Description | Example Value |
| ------------- | ------------- | ------------- | --|
| Flag  | String  |  The flag value. | `"Q"` |
| Flags |  String  | The flag meaning/interpretation. | `"Missing value; suppressed"` |

### faostat_units.csv

This CSV file describes the meaning of each unit of measurement in the crop dataset. It was downloaded directly from the FAOSTAT website.

| Column Name  | Data Type | Description | Example Value |
| ------------- | ------------- | ------------- | --|
| Unit Name  | String  |  The unit value. | `"100 g/ha"` |
| Description |  String  | The unit meaning/interpretation. | `"hundred Grams per hectare"` |

### upov_members.csv

This CSV file contains information on when different countries joined the UPOV.  It was provided directly by GRAIN and lightly cleaned by a DSI staff member.  

| Column Name  | Data Type | Description | Example Value |
| ------------- | ------------- | ------------- | --|
| Country  | String  | The country name. | `"Australia"` |
| Entry Year  | Integer  | The year the country joined the UPOV. | `1989` |
