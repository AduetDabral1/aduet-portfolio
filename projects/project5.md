# IPL 2026 Live Dashboard

## Project Link
https://app.powerbi.com/view?r=eyJrIjoiNDM3ZDk1NDMtOWY2OS00ZDExLTgxOWYtZTY3ZjI2MjQ3ZTA0IiwidCI6ImE2ZGJkZGRlLTU3OTgtNGViYS1hNWE4LTc4ODA3ZTgyZDllYiJ9&embedImagePlaceholder=true&pageName=37c85bd29990ae491913

---

## 🛡️ License
This project is licensed under the MIT License.

---

## ☕ Support & Attribution
This dashboard was developed as a replication and enhancement project focused on modern data engineering and BI techniques.
**# IPL 2026 Live Analytics Dashboard 🏏

A high-performance, real-time Power BI solution for the **Indian Premier League (IPL) 2026**. This project integrates live API data with scraped historical and squad data to provide a 360-degree view of the tournament.

---

## 🚀 Key Features

*   **Live Score Integration:** Real-time updates fetched via the **Cricbuzz API** (RapidAPI).
*   **Web Scraping:** Automated extraction of player statistics and team squads from web sources.
*   **Advanced Data Modeling:** Implementation of complex Star Schema architecture with optimized relationships.
*   **Dynamic Tooltips:** Custom hover-over reports for in-depth Batsman and Bowler performance analysis.
*   **Automated Data Cleaning:** Robust ETL pipelines using **Power Query (M)** and **Excel**.

---

## 🛠️ Tech Stack

*   **Visualization:** Power BI Desktop
*   **Data Sources:** RapidAPI (Cricbuzz), Web Scraping (CSV), Excel
*   **Languages:** DAX (Data Analysis Expressions), M (Power Query)
*   **Data Modeling:** Medallion Architecture (Bronze/Silver/Gold)

---

## 📊 Dashboard Overview

### 1. Home Page
The landing page featuring high-impact visuals of the 2026 captains and quick navigation to all analytical sections.
<img width="1054" height="546" alt="Screenshot 2026-05-05 103333" src="https://github.com/user-attachments/assets/9cbf2a41-4769-4e8f-80c1-f14376db74e6" />


### 2. Live Score Center
Provides a ball-by-ball feel with live Run Rate, Required Run Rate, and partnership details. It features a "Top Performers" segment for immediate match impact analysis.
<img width="1408" height="792" alt="Screenshot 2026-05-05 103422" src="https://github.com/user-attachments/assets/fa564027-4c4d-4bb7-858e-12cc27d2ba5b" />


### 3. Points Table
A dynamic standings report including Matches Played, Won, Lost, Points, and **Net Run Rate (NRR)**. Users can select specific team logos to see a summary of their current standing.
<img width="1410" height="791" alt="Screenshot 2026-05-05 103543" src="https://github.com/user-attachments/assets/3d7397d8-a58b-45db-86b9-7b55d0f3a5d9" />


### 4. Squad Analysis
A detailed roster for all 10 teams. Displays player headshots, roles (WK-Batter, Allrounder, Bowler), and technical styles (Batting/Bowling hands).
<img width="1411" height="790" alt="Screenshot 2026-05-05 103613" src="https://github.com/user-attachments/assets/0e7d900a-c60b-4bf8-8abd-c99fe4f7d110" />


### 5. Performance Tooltips
Custom-built tooltips for a granular look at individual players. 
*   **Batsman Tooltip:** Runs, Balls Faced, Fours, Sixes, and Strike Rate.
<img width="1412" height="791" alt="Screenshot 2026-05-05 103453" src="https://github.com/user-attachments/assets/bd45b5a4-7724-4e5b-8985-77e636b81ed3" />

*   **Bowler Tooltip:** Overs, Maidens, Runs Conceded, Wickets, and Economy.
<img width="1408" height="789" alt="Screenshot 2026-05-05 103507" src="https://github.com/user-attachments/assets/396f2282-4ab1-4a84-81b0-71a5a60bb2db" />

---

## 📐 Data Modeling & DAX

The project utilizes advanced DAX measures to calculate real-time tournament metrics.



### Example Measures:
*   **Dynamic Inning Filtering:** 
    ```dax
    Is_Current_Inning = 
    VAR LatestInning = CALCULATE(MAX(Live_Score[Inning]), ALL(Live_Score))
    RETURN IF(SELECTEDVALUE(Live_Score[Inning]) = LatestInning, 1, 0)
    ```
*   **Net Run Rate (NRR) Calculations**
*   **Strike Rate & Economy Rate Logic**

---

## 📂 Repository Structure
```text
IPL 2026 Dashboard/
├── Datasets/                 # CSVs from web scraping & Excel cleaning
├── Scripts/                  # M-code snippets for API calls
├── Images/                   # Dashboard screenshots & Captain headshots
├── Dashboard_Slides.pdf      # Screenshots of all dashboard pages in a PDF
├── IPL_2026_Dashboard.pbix   # Main Power BI Report file
└── README.md                 # Project Documentation
