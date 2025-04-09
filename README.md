# Global-Sustainable-Energy

# 🌍 Global Sustainability Power BI Dashboard

An interactive Power BI report analyzing worldwide progress in sustainable energy, CO₂ emissions reduction, access to clean energy, and green investments across countries and years.

![Alt Text](relative/or/absolute/path/to/Home.png)


---

## 📚 Table of Contents

1. [Introduction](#1-introduction)  
2. [Project Requirements](#2-project-requirements)  
3. [User Requirements Analysis](#3-user-requirements-analysis)  
4. [Data Flow Diagram](#4-data-flow-diagram)  
5. [Data Source Description](#5-data-source-description)  
6. [Dataset Description](#6-dataset-description)  
7. [Power Query Transformations](#7-power-query-transformations)  
8. [Data Model](#8-data-model)  
9. [DAX Measures](#9-dax-measures)  
10. [Report Visuals & Structure](#10-report-visuals--structure)  
11. [Administration & Maintenance](#11-administration--maintenance)  
12. [Conclusions & Recommendations](#12-conclusions--recommendations)  

---

## 1. Introduction

This Power BI dashboard provides a centralized view of key sustainability indicators based on global datasets. It supports data-driven storytelling, policymaking, and investment decisions through visual analysis of renewable energy adoption, emissions reductions, and access to clean energy worldwide.

---

## 2. Project Requirements

### 2.1 System Requirements

- **Tools Used**: Power BI, Excel, Power Query  
- **Data Storage**: CSV/Excel files and Power BI Data Model  

### 2.2 Business Requirements

- Track carbon emissions and renewable energy use  
- Visualize energy access across countries  
- Enable YoY trend analysis  
- Support SDG alignment with country-level metrics  
- Provide exportable, interactive insights

### 2.3 Functional Requirements

- Import structured global data  
- Clean and shape datasets in Power Query  
- Use DAX for dynamic KPIs (e.g., CO₂ per capita, renewable share)  
- Visualize data with play axis and country filters  
- Build dashboard with both high-level and detailed views

---

## 3. User Requirements Analysis

| ID | Role                  | Requirement                        | Business Value                                | Acceptance Criteria                     |
|----|-----------------------|------------------------------------|-----------------------------------------------|------------------------------------------|
| 1  | Energy Analyst        | Track renewable electricity growth | Monitor country progress towards energy goals | Line and bar chart with filters          |
| 2  | Policy Maker          | View CO₂ emissions by region       | Support environmental policy decisions         | CO₂ per capita and YoY emission charts   |
| 3  | NGO Representative    | Compare electricity access levels  | Identify underserved populations               | Access % by year and country             |
| 4  | Report Publisher      | Export impact visuals              | Communicate with external stakeholders         | PDF-ready views with summaries           |

---

## 4. Data Flow Diagram

**Data Sources → Power Query → Data Model → DAX Measures → Visual Reports**

- Data extracted from CSV files (e.g., emissions, GDP, energy access)
- Transformed via Power Query
- Modeled in Power BI using Date & Entity as dimensions
- Visualized with KPIs, YoY trends, and maps

---

## 5. Data Source Description

- **World Bank**: GDP, access to electricity, energy intensity  
- **UN SE4ALL**: Clean cooking, renewable energy share  
- **IEA / OpenEmissions**: Emissions, power generation  
- **Manually Prepared**: Environmental equivalents (e.g. cars/trees)

---

## 6. Dataset Description

| Table Name        | Description                                | Key Columns                                   |
|------------------|--------------------------------------------|-----------------------------------------------|
| `Global_Energy`  | Core dataset with country & energy metrics | Entity, Year, CO₂ Emissions, Renewables, etc. |
| `DateTable`      | Time intelligence support                  | Date, Year, Quarter, Month                    |

---

## 7. Power Query Transformations

- Removed null and outlier values  
- Converted numeric and date types  
- Merged yearly country records  
- Calculated fields: `CO2 per capita`, `Renewables share`  
- Built custom date table (2000–2030)

---

## 8. Data Model

- **Star Schema** with:
  - Fact table: `Global_Energy`
  - Dim table: `DateTable`
- Relationships:
  - `Global_Energy[Year]` ↔ `DateTable[Year]`

---

## 9. DAX Measures

```dax
CO2 Saved (kt) = [Baseline CO2] - SUM('Global_Energy'[CO2 Emissions])

CO2 per Capita (t) = 
DIVIDE(SUM('Global_Energy'[CO2 Emissions]) * 1000, SUM('Global_Energy'[Population]))

Renewable Share (%) = 
DIVIDE(SUM('Global_Energy'[Electricity from Renewables]), [Total Electricity]) * 100
```

Also includes metrics for:
- CO₂ equivalents (cars, coal, trees)
- Access to electricity
- Financial flows
- YoY % changes

---

## 10. Report Visuals & Structure

### 10.1 KPI Overview Page

- 🌍 CO₂ Emissions
- ⚡ Renewable Share
- 🔋 Energy Intensity
- 🧑‍🤝‍🧑 Electricity & Cooking Access
- 🧾 Financial Flows to Energy

### 10.2 YoY Animation Page

- Play Axis showing trends from 2000–2020  
- Dynamic highlight of top 5 CO₂ savers  
- Country ranking with animation

### 10.3 Country Comparison Page

- Filter by region, income group, or year  
- Scatter plots: GDP vs. CO₂  
- Table + chart toggle (with bookmarks)

---

## 11. Administration & Maintenance

- **Data refresh**: Monthly or quarterly updates via Power Query  
- **Data validation**: Check for duplicates and outliers  
- **Performance**: Optimize DAX and avoid excessive filters  
- **User roles**: Define access (edit, view, export)  
- **Export**: Visuals prepared for clean PDF or image export

---

## 12. Conclusions & Recommendations

-  Maintain consistent relationships across new data updates  
-  Validate DAX calculations after model changes  
-  Reduce unnecessary steps in Power Query for performance  
-  Periodically review accuracy and alignment with UN SDGs  
-  Expand with additional sustainability dimensions (e.g., water use, waste)

---

>  Created by Mohamed Zakarya 
> Last Updated: April 2025 
