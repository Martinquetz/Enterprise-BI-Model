# Enterprise-BI-Model
Enterprise BI Model – SQLite‑Backed Semantic Layer for Power BI

## Overview
The Enterprise BI Model project showcases a fully engineered semantic layer built on a SQLite relational database, designed to power a scalable, analytically rich Power BI solution.
This repository highlights how a dashboard evolves into a structured, model‑driven BI system, emphasizing relational modeling, semantic architecture, and enterprise‑grade measure design.

Unlike the original Advanced_BI_Insight project, which focuses on visual storytelling and UX, this repository dives into the data modeling foundations that enable high‑quality analytics. It demonstrates how to build a clean star schema, enforce SQL‑level integrity, and design a semantic layer that is maintainable, auditable, and ready for real‑world BI environments.

---

## Table of Contents
- [Project Purpose](#project-purpose)  
- [Architecture Overview](#architecture-overview)  
- [Dataset & Sources](#dataset--sources)  
- [Semantic Model Design](#semantic-model-design)  
- [Fact & Dimension Tables](#fact--dimension-tables)  
- [Measure Layer](#measure-layer)  
- [Calculation Groups](#calculation-groups)  
- [Data Model Diagram](#data-model-diagram)  
- [Dashboard Pages](#dashboard-pages)  
- [Installation & Setup](#installation--setup)  
- [Project Structure](#project-structure)  
- [Future Enhancements](#future-enhancements)  
- [License & Attribution](#license--attribution)

---

## Project Purpose
This repository showcases how to build a **semantic‑first BI solution**, emphasizing:

- relational modeling  
- SQL‑driven data integrity  
- structured measure design  
- documented business logic  
- enterprise‑grade architecture  

It complements the original *Advanced_BI_Insight* dashboard by exposing the **engineering layer** behind a polished BI experience.

---

## Architecture Overview
The solution follows a classic **star schema** pattern:

- Fact table: transactional sales data  
- Dimension tables: product, customer, geography, date  
- Reference tables: target metrics, country metadata  
- SQLite database: centralized relational store  
- Power BI semantic model: measures, hierarchies, relationships  

This architecture ensures clean filter propagation, optimized DAX, and scalable analytics.

---

## Dataset & Sources
- Superstore Orders dataset (cleaned and normalized into SQLite)  
- Countries & Continents metadata  
- Target profit and fulfillment tables  

All tables were imported into SQLite and modeled using foreign keys, surrogate keys, and hierarchies.

---

## Semantic Model Design
The semantic layer includes:

- Table roles (Fact, Dimension, Reference)  
- Primary and foreign keys  
- Hierarchies  
- Measure groups  
- Documentation  

### Key Principles
- Dimensions filter facts (one‑directional relationships)  
- All measures live in a dedicated `_Measures` table  
- Naming conventions follow business‑friendly patterns  
- Hierarchies support intuitive drill‑downs  
- SQL enforces data integrity before Power BI consumes it  

---

## Fact & Dimension Tables

### Fact Table
**Fact_Sales**  
Contains order‑level metrics: sales, profit, quantity, shipping cost, dates, product IDs, customer IDs, and GeoID.

### Dimension Tables
**Dim_Product** – category, subcategory, product name, unit cost  
**Dim_Customer** – customer name, region, state, country  
**Dim_Geo** – continent, country, region, state, GeoID  
**Dates** – full calendar table with hierarchies  

### Reference Tables
**TargetProfitContinent** – profit targets by continent  
**TargetOrderShip** – fulfillment targets  
**countries** – ISO codes, capitals, metadata  

---

## Measure Layer
All measures are centralized in `_Measures` and grouped logically:

### Performance Metrics
- Total Sales  
- Total Profit  
- Profit Margin  
- Total Quantity  

### Operational Metrics
- Avg Days to Fulfill Order  
- Total Shipping Cost  
- Number of Orders  

### Time Intelligence
- Sales Previous Period  
- Total Profit YoY%  
- Total Sales YoY%  

### Strategic Metrics
- Target Profit (Continent-Level)  
- Sales Growth Rate  

Each measure includes:
- Business definition  
- Calculation logic  
- Dependencies  
- Usage notes  

---

## Calculation Groups
(If Tabular Editor is used)

- Time Intelligence: YTD, QTD, MTD, YoY  
- Formatting: currency, percentage, whole number  
- Scenario Modeling: actual, target, variance  

These groups reduce DAX duplication and improve maintainability.

---

## Data Model Diagram
A clean star schema diagram is included in the repo under:

```
/assets/model_diagram.png
```

It illustrates:
- Fact table at the center  
- Dimensions radiating outward  
- One‑directional relationships  
- Hierarchies and keys  

---

## Dashboard Pages
The Power BI report mirrors the original dashboard but is now powered by the semantic model:

- Sales & Profit Overview  
- Management KPIs  
- Customer & Region Insights  
- Metrics Review  
- Filter Page  
- Semantic Layer Overview  

Each page includes improved clarity, hierarchy, and narrative framing.

---

## Installation & Setup

### Requirements
- Power BI Desktop  
- SQLite database engine  
- DB Browser for SQLite (optional)  

### Steps
1. Clone this repository  
2. Open the `.pbix` file  
3. Ensure the SQLite database path matches your environment  
4. Refresh the model  

---

## Project Structure
```
Semantic_BI/
│
├── data/
│   ├── semantic_model.sqlite
│   ├── countries_continents.xlsx
│   └── target_tables/
│
├── assets/
│   ├── model_diagram.png
│   └── screenshots/
│
├── Semantic_BI.pbix
└── README.md
```

---

## Future Enhancements
- Scenario modeling (forecast vs actual)  
- Row‑level security  
- Automated SQLite ETL scripts  
- Dynamic KPI commentary  

---

## License & Attribution
This project is open for learning, portfolio use, and BI engineering demonstration.
