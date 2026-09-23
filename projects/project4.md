# 📦 Supply Chain Analytics Dashboard

An end-to-end **Supply Chain Analytics Dashboard** built in **Power BI** to provide a unified view of procurement, production, inventory, logistics, sales, and customer operations.

The project integrates multiple operational datasets into a dimensional data model, enabling business users to monitor key supply chain KPIs, identify operational bottlenecks, and make data-driven decisions through interactive dashboards.

<a href ="https://app.powerbi.com/view?r=eyJrIjoiNzY5ZDZhYTEtZWQ3NC00ZGE3LTg2NTQtODVkN2IwMTk1MGUzIiwidCI6ImE2ZGJkZGRlLTU3OTgtNGViYS1hNWE4LTc4ODA3ZTgyZDllYiJ9&embedImagePlaceholder=true">
  Supply Chain Analytics Power BI dashbaord
</a>

---

# Business Problem

Modern supply chains generate data from every stage of operations—from purchasing raw materials to manufacturing products, managing inventory, fulfilling customer orders, and delivering shipments.

However, these functions are often analyzed separately, making it difficult for decision-makers to understand how one area impacts another. Procurement teams monitor suppliers, inventory teams focus on stock levels, logistics tracks deliveries, while sales measures revenue and profitability.

Without a centralized analytical solution, organizations spend significant time consolidating reports instead of identifying operational inefficiencies.

This project aims to solve that problem by creating an integrated Power BI dashboard that combines multiple business functions into a single source of truth for supply chain performance monitoring.

---

# Business Questions

The dashboard was designed to answer questions such as:

## Sales & Customer

- Which customers generate the highest revenue and profit?
- Which sales channels contribute the most revenue?
- How does monthly revenue change throughout the year?
- Which product categories generate the highest sales?
- What is the current overall profit margin?

## Procurement

- Which suppliers have the highest lead times?
- Which suppliers deliver the best quality?
- How are purchase orders distributed across suppliers?
- Which supplier specialties contribute the highest procurement costs?

## Inventory & Production

- Which products are approaching reorder levels?
- How much safety stock should be maintained?
- Which products have the highest defect rates?
- How efficiently is inventory moving through the supply chain?
- How many inventory days are currently available?

## Logistics

- Which carriers experience the highest shipment delays?
- What are the major causes of delayed deliveries?
- Which carriers incur the highest shipment costs?
- What percentage of shipments are delivered successfully?
- How do shipment costs vary throughout the year?

---

# Methodology

## Data Collection

The project uses multiple CSV datasets representing different business functions:

- Sales
- Procurement
- Inventory
- Production
- Shipment
- Product
- Customer
- Supplier
- Facility
- Date

---

# Technology Stack

- Power BI Desktop
- Power Query
- DAX
- Dimensional Data Modeling
- CSV Files

---

## Data Preparation

Power Query was used to:

- Clean and transform raw datasets
- Validate data types
- Handle missing values
- Remove unnecessary columns
- Standardize naming conventions
- Prepare lookup keys for relationships

---

## Data Modeling

The analytical model was designed directly inside Power BI using a dimensional modeling approach.

### Fact Tables

- Fact Sales
- Fact Procurement
- Fact Inventory
- Fact Production
- Fact Shipment

### Dimension Tables

- Dim Product
- Dim Customer
- Dim Supplier
- Dim Facility
- Dim Date

The model follows a star-schema design where shared dimensions connect multiple fact tables, allowing consistent filtering and cross-functional analysis across procurement, production, inventory, logistics, and sales.

> **Data Model**
<img width="882" height="789" alt="Data Modeling" src="https://github.com/user-attachments/assets/52a3b9bc-54d7-4f2b-85fa-497afc64e6bd" />



---

## DAX Measures

Several business KPIs were created using DAX, including:

- Gross Revenue
- Net Revenue
- Total Profit
- Profit Margin %
- Total Quantity Sold
- Inventory Turnover
- Days of Inventory
- Safety Stock
- Perfect Order Rate
- Shipment Delay %
- Average Lead Time
- Average Quality Score
- Sell-through Rate
- Average Shipment Cost
- Defect Rate

---

# Exploratory Data Analysis (EDA)

Before building the dashboard, exploratory analysis was performed to understand operational trends across the supply chain.

### Revenue Analysis

- Revenue by customer
- Revenue by product category
- Revenue by sales channel
- Monthly revenue trends

### Supplier Analysis

- Lead time distribution
- Procurement cost
- Supplier quality score
- Order allocation

### Inventory Analysis

- Current inventory
- Safety stock
- Reorder point
- Product-wise inventory distribution

### Production Analysis

- Defective units
- Monthly production trends
- Product defect rates

### Logistics Analysis

- Shipment status
- Carrier performance
- Shipment cost
- Delay reasons
- Delivery success rate

---

# Key Findings

## Revenue Performance

- Smartphones generated the largest share of total revenue.
- Online and retailer channels outperformed direct sales.
- Revenue remained relatively stable throughout the year with seasonal fluctuations.

## Supplier Performance

- Lead times varied across suppliers, highlighting opportunities to optimize procurement planning.
- Supplier quality scores remained consistently high, while procurement costs differed by supplier specialization.

## Inventory

- Smartphones accounted for nearly half of the total inventory.
- Some products maintained inventory levels well above reorder points, while others approached replenishment thresholds.
- Inventory turnover indicated efficient stock movement across the supply chain.

## Logistics

- Most shipments were delivered successfully, with delayed shipments representing only a small percentage of total orders.
- Carrier capacity, documentation issues, and port congestion were the primary causes of shipment delays.
- Shipment costs remained relatively consistent across the year with peaks during high-volume months.

## Customer Performance

- Revenue was concentrated among a small number of major customers.
- Profit closely followed revenue trends, indicating consistent profitability across key accounts.

---

# Dashboard

The report consists of five interactive pages that provide insights into different areas of the supply chain.

## 🏠 Overview

Provides executive-level KPIs including:

- Revenue
- Profit
- Inventory
- Shipments
- Suppliers
- Customer performance

<img width="1422" height="800" alt="image" src="https://github.com/user-attachments/assets/01bbded9-4433-4684-9266-6cf7844ca1b8" />

---

## 🚢 Supplier Dashboard

Analyzes:

- Supplier lead time
- Procurement cost
- Quality score
- Order distribution
- Supplier performance

<img width="1422" height="800" alt="image" src="https://github.com/user-attachments/assets/a959b512-5d96-46e3-b4b4-3a8856801485" />

---

## 📦 Inventory & Production Dashboard

Analyzes:

- Current inventory
- Safety stock
- Inventory turnover
- Product defect rates
- Reorder levels

<img width="1413" height="795" alt="image" src="https://github.com/user-attachments/assets/50e15ddf-d9ce-44ab-9b3d-93a22d606063" />

---

## 🚚 Shipment Dashboard

Tracks:

- Shipment performance
- Delivery status
- Carrier comparison
- Shipment costs
- Delay reasons

<img width="1423" height="798" alt="image" src="https://github.com/user-attachments/assets/2032920c-693d-4d53-96f9-163fa3cdc900" />

---

## 👥 Customer Dashboard

Explores:

- Customer revenue
- Profitability
- Sales channels
- Monthly revenue trends
- Product performance

<img width="1423" height="798" alt="image" src="https://github.com/user-attachments/assets/97a51f9a-e6b2-49c9-85a2-b492321ee041" />

---

# Repository Structure

```text
Supply-Chain-Analytics-Dashboard/
│
├── Data/
│   ├── dim_customer.csv
│   ├── dim_date.csv
│   ├── dim_facility.csv
│   ├── dim_product.csv
│   ├── dim_supplier.csv
│   ├── fact_inventory.csv
│   ├── fact_procurement.csv
│   ├── fact_production.csv
│   ├── fact_sales.csv
│   └── fact_shipment.csv
│
├── Images/
│   ├── data_model.png
│   ├── overview.png
│   ├── supplier.png
│   ├── inventory.png
│   ├── shipment.png
│   └── customer.png
│
├── Dashboard.pbix
└── README.md
```

---

# Future Work

Possible enhancements include:

- Connect the dashboard to a live SQL database or ERP system instead of CSV files.
- Implement incremental refresh for larger datasets.
- Add demand forecasting using Power BI forecasting or machine learning models.
- Develop supplier risk and inventory optimization metrics.
- Implement Row-Level Security (RLS) for department-specific reporting.
- Introduce predictive KPIs such as stockout probability, demand forecasting, and delivery risk analysis.
