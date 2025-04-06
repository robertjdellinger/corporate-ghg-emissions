---
Corporate GHG Emissions Analysis
---

## Background 

This repository presents an R-based walkthrough that adapts the approach developed by the [Environmental Data and Governance Initiative (EDGI)](https://www.environmentalenforcementwatch.org/) in their [Owning Up: A Tool to Measure US Carbon Emissions by Corporations](https://envirodatagov.org/owning-up-a-tool-to-measure-us-carbon-emissions-by-corporations/). Under the US Environmental Protection Agency’s Greenhouse Gas Reporting Program (GHGRP), facilities must measure and report their greenhouse gas (GHG) emissions annually, and, in addition, disclose ownership information - specifically, the share that each parent company holds in each facility. This reporting enables us not only to identify the facilities with the highest emissions but also determine which corporate entities bear the most responsibility for those emissions. By integrating data from multiple EPA sources—including spreadsheets for direct emitters, suppliers, and facility ownership, this analysis quantifies emissions by corporate ownership, rather than focusing solely on geographic or individual emission metrics. Notably, the concept of a “carbon footprint” was popularized by an advertising and public relations firm working for the fossil fuel company British Petroleum (BP), as part of an effort to shift the responsibility for climate change onto individual consumers. This framework, in line with EPA guidelines and reporting practices, provides a comprehensive approach for assessing the corporate dimensions of GHG emissions and reinforces the need for policy interventions that target the systemic contributors to climate change.

### Key Objectives

- **Data Integration:** Combine EPA data from direct emitters, suppliers, and ownership files.
- **Attribution:** Calculate each parent company’s share of GHG emissions based on ownership stakes.
- **Insights:** Identify which companies account for the highest emissions and enable further analysis by state, county, or sector (e.g., universities, municipalities).
  
---
# Quantifying Corporate Carbon Emissions

## Data Sources

This project relies on several key datasets from the EPA GHGRP, for additional background on the GHGRP and detailed methodology, please refer to the [EPA GHGRP website](https://www.epa.gov/ghgreporting) and the [EPA helpdesk FAQ](https://www.epa.gov/ghgreporting/ghgrp-helpdesk). As defined by the EPA, *direct emitters* are facilities that release GHGs directly into the atmosphere (e.g., power plants), whereas *suppliers* are facilities within the fossil fuel supply chain whose products eventually lead to GHG emissions (e.g., refineries). The EPA further explains, “The GHGRP does not represent total U.S. GHG emissions, but provides facility-level data for large sources of direct emissions, thus representing the majority of U.S. GHG emissions. The GHGRP data collected from direct emitters represent about half of all U.S. emissions.” When supplier data is combined, the dataset can account for up to 90% of U.S. emissions; however, the EPA warns, “Data from direct emitters and suppliers cannot be viewed together because it would cause double counting of emissions in many sectors. In general, it is more accurate to look at upstream (also called suppliers) data separately from downstream (also called direct emitters) data.” Ownership of facility emissions is calculated based on the percentage of each facility owned by different companies. In this project, after merging the emissions data with the facility ownership information, each facility’s total emissions are allocated to its parent companies in proportion to their ownership stakes. For example, if a facility emits 100,000 metric tons of CO2 equivalent and a company owns 25% of that facility, then 25,000 metric tons of emissions are attributed to that company. This method ensures that emissions are fairly distributed among multiple owners.

The following data sources are used in the script: 

- **EPA GHGRP Data Summary Spreadsheets (2023):**  
  This ZIP file contains multiple spreadsheets covering various aspects of EPA emissions data, including:
  - **Direct Point Emitters:** Facilities that release GHGs directly into the atmosphere (e.g., power plants).
  - **Onshore Oil & Gas Production, Gathering & Boosting, Transmission Pipelines, LDC - Direct Emissions, and SF6 from Electrical Equipment:** Various industry sectors that directly report emissions.
  - **Suppliers:** Facilities related to the supply chain for fossil fuels, whose products eventually lead to GHG emissions when used.
  
  [Download Data](https://www.epa.gov/system/files/other-files/2024-10/2023_data_summary_spreadsheets.zip)

- **NAICS Codes (2022):**  
  Provides industry classification codes and titles for facilities. This helps to contextualize the sectors in which facilities operate.
  
  [Download NAICS Codes](https://www.census.gov/naics/2022NAICS/6-digit_2022_Codes.xlsx)

- **EPA GHGRP Parent Company Data (XLSB):**  
  Contains information on the parent companies that own (or partially own) the facilities reporting emissions, including the percentage of ownership. This file is critical for attributing emissions responsibility to corporate entities.
  
  [Download Parent Company Data](https://www.epa.gov/system/files/other-files/2024-10/ghgp_data_parent_company.xlsb)

To load the file go into the Scritps folder and either open the HTML or clone the repostiroy and edit/ knit the r markdow n file 
  
## How to Run/View the Analysis

### Option 1: Using the HTML Report

- You can view the report by clicking the link below or copying it into your browser:
[Corporate Polluters Calculations HTML Report](https://htmlpreview.github.io/?https://raw.githubusercontent.com/robertjdellinger/corporate-ghg-emissions/main/Scripts/corporate-ghg-emissions.html)

### Option 2: Clone and Run the R Markdown File

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/yourusername/corporate-ghg-emissions.git
   cd corporate-ghg-emissions

2.	Install Required R Packages:
Open R or RStudio and run:

install.packages(c("tidyverse", "ggplot2", "readxl", "readxlsb", "janitor", "purrr", "here", "gt", "viridis", "forcats"))

3.	Place the Data Files:
Download the raw EPA data files from the links above and place them in the Data/Raw/ folder.

5.	Open and Knit the R Markdown File:
Open Scripts/Corporate-GHG-Emissions.Rmd in RStudio and click Knit to generate the full analysis report.

---

## Acknowledgments

This analysis is adapted from the EDGI “Owning Up” tool, originally developed using Python. For more details on their work, please visit the [EDGI website](https://www.environmentalenforcementwatch.org/). All files are organized using best practices, with data stored in the **Data** folder and the main R Markdown file in the **Scripts** folder.

---

### **Contact Information:**
**Robert J. Dellinger**  
**Ph.D. Student, Atmospheric & Oceanic Sciences, UCLA**  
**rjdellinger[at]ucla.edu**  

[![GitHub](https://img.shields.io/badge/GitHub-rob--dellinger-181717?logo=github&logoColor=white)](https://github.com/rob-dellinger)  

---

