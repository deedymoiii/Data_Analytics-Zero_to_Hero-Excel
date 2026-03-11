# Philippine Trade Structure and Balance Analysis (2019–2024): A Sector-Level Study Using WITS Data

# 👤 About the Author

Hi, I’m Engr. Ed-Vir Mercado, a Computer Engineer transitioning into Data Analytics.

This project is part of my analytics portfolio, developed to demonstrate practical skills in data cleaning, modeling, and analytical reporting using Excel’s Power Query, Power Pivot, and DAX. It reflects my shift from guided tutorials toward independent, problem-driven analysis.

# 📌 Project Overview

This project analyzes the Philippine trade structure from 2019 to 2024 through:

- Trade magnitude (total imports & exports)
- Structural composition (sector contribution)
- Growth dynamics (Year-over-Year changes)
- Trade concentration metrics (Top partner dependence)

The goal is to simulate a trade intelligence reporting framework similar to what may be used in policy or economic analysis settings.

## Key Analytical Questions

- How did Philippine trade perform before, during, and after the COVID-19 pandemic?
- Which sectors dominate total trade, and does this imply structural dependence?
- Is the country becoming more or less diversified in its export and import markets?
- Are there emerging concentration risks in key trade partners?

### 📅 Why 2019–2024?

This period captures:
- Pre-pandemic conditions (2019)
- Pandemic disruption (2020–2021)
- Post-pandemic recovery (2022–2024)
- Two distinct policy environments

Analyzing this timeframe allows for evaluation of structural resilience and recovery dynamics across sectors and partners.

### 🧩 Why Sector-Level Analysis?

Using HS 2017 2-digit classification enables:
- Identification of dominant product groups
- Evaluation of sectoral trade dependence
- Assessment of diversification opportunities

Sector-level analysis provides insight into which industries drive Philippine external trade and which may present structural vulnerability.

# 📊 Data Source

Data was extracted from the World Bank’s World Integrated Trade Solution (WITS) platform with the following filters:
- **Nomenclature**: HS 2017
- **Tier**: Chapter (2-digit HS codes)
- **Reporter**: Philippines (PHL)
- **Years**: 2019–2024
- **Flow**: Gross Exports and Gross Imports
- **Partner**: All Partners

The 2-digit HS level was selected to balance analytical clarity and interpretability, particularly for high-level structural analysis.

My familiarity with WITS stems from prior internship exposure at the Department of Trade and Industry, where it is commonly used for trade-related data gathering and policy support.

# 🛠 Data Cleaning & Transformation (Power Query)

Using Power Query, I performed the following transformations:
- Removed non-essential metadata columns (e.g., ReporterName and redundant identifiers)
- Standardized numeric formats for trade values
- Created a calculated column TradeValueUSD by converting “Trade Value (1000 USD)” into full USD values
- Ensured consistent naming conventions across sector and partner fields
- Structured the dataset to support dimensional modeling

Detailed cleaning steps are documented in the following screenshot.

<img width="398" height="870" alt="Data Cleaning" src="https://github.com/user-attachments/assets/5674f07a-3009-419b-b551-ba0f3f6c8866" />


# 🧩 Data Model

A star schema model was implemented using Power Pivot.

<img width="1920" height="1032" alt="Star Schema" src="https://github.com/user-attachments/assets/0eb88d3c-9d67-423f-99ff-67ed1886bde5" />

## Fact Table
Fact_Trade
- Grain: One row per HS2 Code × Partner × Year × Trade Flow
- Contains trade value metrics

## Dimension Tables
Dim_Product
- HS2_Code (primary key)
- HS2_Description
- HS2017_Classification
- HS2_Sort (custom sorting for Pivot Tables)

Dim_Partner
- Deduplicated partner names

Dim_Year
- Trade year values (2019–2024)

Each dimension table is connected to the fact table via one-to-many relationships.

This structure improves scalability, filter performance, and DAX measure flexibility.

# 📐 DAX Measures

To simulate structured trade reporting, the following measures were developed: 

**Total Trade Value**
- Sum of exports and imports. Used to measure trade magnitude.

**Trade Balance**
- Exports minus imports. Indicates trade surplus or deficit.

**Year-over-Year (YoY %) Growth**
- Measures relative annual change to assess momentum and recovery.

**Sector/Partner Share (%)**
- Contribution to total trade. Used to evaluate structural composition.

**Ranking Measures**
- Ranks sectors and partners based on trade value to identify dominance patterns.

All measures are documented in a consolidated Measures.txt file within the repository.

# 📊 Current Outputs

The workbook provides several analytical views of Philippine trade structure using **Power Pivot**, **Pivot Tables**, and **dashboard visualizations**.

## 01_Executive_Overview

A high-level summary dashboard presenting key indicators of Philippine trade.

Includes:
- Total exports and imports (USD)
- Overall trade balance
- Top export and import partners
- Year slicer to analyze trends from 2019–2024

## 02_Partner_Structure

Analysis of trade concentration by partner country.

Exports:
- Total export value (USD)
- Share of total exports
- Ranking by export contribution

Imports:
- Total import value (USD)
- Share of total imports
- Ranking by import contribution

Structural concentration metrics:
- Top 1 partner share
- Top 5 partner share
- Trend analysis of partner dependence (2019–2024)

## 03_Sector_Composition

Sector-level breakdown of Philippine trade.

Includes:
- Sector share of total exports
- Sector share of total imports
- Comparative view of sector importance across years
- Interactive filtering using a Year slicer

This sheet highlights which industries dominate the country’s trade structure.

## 04_Trade_Balance_Analysis

Sector-level trade balance visualization.

Includes:
- Trade balance by sector (Exports – Imports)
- Horizontal bar chart separating surplus and deficit sectors
- Identification of:
  - Largest surplus sector
  - Largest deficit sector
- Analytical summary highlighting structural patterns in the Philippine trade economy

# 🔎 Preliminary Insights

Initial findings indicate:
- **Machinery and Electrical products** consistently dominate Philippine exports, indicating strong specialization in electronics and semiconductor-related industries.
- Export markets show **moderate diversification**, with the Top 5 export partner share declining from approximately **66% to ~61%** between 2019 and 2024.
- Import concentration risk increased in **2024**, with the Top 1 partner share rising to about **25.6%**.
- The **United States** consistently ranks as the Philippines’ top export destination.
- **China** remains the largest source of imports throughout 2019–2024.
- Sector-level analysis shows large trade deficits in **Mineral Products**, **Transportation Equipment**, and **Chemicals**, reflecting reliance on imported energy, machinery, and industrial inputs.

These patterns suggest **gradual diversification of export markets but persistent structural dependence on imported industrial goods and fuel**.

# 🛠 Tools & Techniques Used

Data Processing
- Microsoft Excel Power Pivot for data modeling
- Fact and dimension table structure (star schema)

Data Analysis
- DAX measures for trade value aggregation and share calculations
- Ranking functions for identifying top trade partners
- Trade concentration metrics (Top 1 / Top 5 partner shares)

Data Visualization
- Pivot Tables for structured analysis
- Dashboard sheets for analytical summaries
- Interactive Year slicer for dynamic filtering

Analytical Techniques
- Trade partner concentration analysis
- Sector composition analysis
- Sector-level trade balance analysis (Exports – Imports)
- Identification of structural trade surpluses and deficits
