# Philippine Trade Structure and Balance Analysis (2019–2024): A Sector-Level Study Using WITS Data 
🚧 In Progress

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

The workbook currently supports analytical views via Pivot Tables:

By Partner – Exports
- Total export value (USD)
- Share of total exports
- Ranking by export contribution

By Partner – Imports
- Total import value (USD)
- Share of total imports
- Ranking by import contribution

Structural Concentration
- Top 1 and Top 5 partner contribution to total trade
- Trend analysis of partner dependence (2019–2024)

Sector Composition
- Sector-level share of total trade over time

Dashboard visualization and KPI summary sheets are currently under development.

# 🔎 Preliminary Insights

Initial findings indicate:
- Machinery and Electrical products consistently dominate Philippine trade, suggesting structural dependence on this sector.
- Export markets show moderate diversification, with Top 5 export share declining from ~66% to ~61%.
- Import concentration risk increased in 2024, with Top 1 partner share rising to ~25.6%.
- The United States consistently ranks as the Philippines’ top export destination.
- China remains the largest source of imports throughout 2019–2024.

These patterns suggest improving export diversification but potential import-side vulnerability.

# 💡 Skills Demonstrated

- Data Cleaning & Transformation (Power Query)
- Dimensional Data Modeling (Star Schema)
- DAX & Analytical Measure Development
- Time-Series & Growth Analysis
- Concentration & Share Metrics
- Trade Data Interpretation
- Structured Pivot Table Reporting

# 🚀 Planned Enhancements

- Executive KPI Dashboard
- Interactive slicers for sector and partner filtering
- Policy-period comparison modeling
- Enhanced data visualization for executive-level reporting
