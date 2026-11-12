# Consumer Complaints Analysis

## Project Overview
Financial institutions receive complaints from consumers regarding various financial products and services, including account management, credit cards, mortgages, credit reporting, and payment services.

This project aims to analyze a dataset of **62,516 consumer complaints** to identify performance trends over time, highlight products with the most friction, and evaluate the organization's operational efficiency in providing timely and satisfactory responses. The project combines Python for initial data profiling and Power BI for deep-dive visual analytics.

## Tools & Technologies Used
*   **Python (Colab Notebook):** Used for initial exploratory data analysis (EDA), data profiling, and statistical summaries.
*   **Power Query:** Used for Transformation and Data Cleaning
*   **DAX (Data Analysis Expressions):** Used for complex KPI calculations and time-intelligence metrics.
*   **Power BI:** Used to build the interactive, four-page interactive dashboard.

##  Data Cleaning & Transformation (Power Query)
To ensure the data was optimized for visualization, the following transformations were applied in Power Query:
1.  **Shortened Product Names:** Added a conditional column named `Product Short` to condense lengthy product descriptions (e.g., converting "Checking or savings account" to "Checking & Savings") for cleaner chart axis labels.
2.  **Handled Missing Data:** Replaced null/blank values in the `Company public response` column with `"Unspecified"` to ensure these records are explicitly categorized rather than showing up as `(Blank)` in visual legends.

##  DAX Methodology & KPI Definitions
Complaints currently marked as **"In progress"** (1,494 records) were actively excluded from resolution-based calculations. Including open cases in SLA metrics artificially deflates performance rates since these cases have not yet reached their final disposition.

Key metrics utilizing this logic include:
*   **Timely Response Rate:** Evaluated only on closed tickets.
*   **Relief Rates (Monetary & Overall):** Calculated only against completed cases.
*   **Average Reply Days & Same-Day Processing:** Measured strictly on resolved complaints.

*Note: For a complete list of DAX formulas and business logic, please refer to the attached **"KPI DEFINITION SHEET.docx"***

## Dashboard Structure
The Power BI report is divided into four highly focused pages:

### 1. Executive Complaint Overview
*   Provides a high-level summary for leadership.
*   Tracks total historical complaint volume (62,516 records).
*   Visualizes geographic distribution across states and overall volume trends by year and month.

### 2. Product and Issue Analysis
*   Drills down into specific friction points for consumers.
*   Identifies the top complained-about products (e.g., Checking & Savings accounts, Credit Cards).
*   Utilizes a Treemap and Matrix to break down overarching products into their specific sub-products and root-cause issues.

### 3. Company Response Analysis
*   Evaluates resolution outcomes and operational performance.
*   Tracks the percentage of complaints closed with monetary vs. non-monetary relief.
*   Highlights which products yield the highest financial payouts and tracks untimely response bottlenecks.

### 4. Complaint Timeline Analysis
*   Focuses on time-series data and the speed of resolution.
*   Tracks Peak Daily Volume, Same-Day Processing Rates (>81% on completed cases), and Delayed Processing Rates (>7 days).


## Python EDA Summary
The attached Python notebook was utilized to validate the structural integrity of the dataset before importing it into Power BI. Key findings included:
*   Confirmed dataset dimensions: 62,516 rows and 12 columns.
*   Identified zero duplicate records.
*   Profiled the distribution of complaints across 51 states and 9 unique product categories.
*   Calculated the preliminary historical median forwarding time (0.0 days) and mean forwarding time (1.22 days).