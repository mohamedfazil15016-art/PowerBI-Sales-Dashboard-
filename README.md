# PowerBI-Sales-Dashboard-
# 📊 Sales Analysis Dashboard

A Power BI dashboard project analyzing sales order data — covering data cleaning, transformation, and interactive visualization. **This project is a work in progress**; some report pages are still being built out.

---

## 🚧 Project Status

This dashboard is **not yet complete**. Data cleaning and the data model are in place, and part of the report has been built, but a couple of pages are still placeholders. See [What's Left To Do](#-whats-left-to-do) below.

---

## 📁 Repository Contents

| File | Description |
|---|---|
| `Raw_data_sales_Analysis.xlsx` | Original, unprocessed sales order export |
| `Cleaned data.xlsx` | Cleaned dataset, ready for modeling and analysis |
| `Sales_analysis_Dashboard.pbix` | Power BI dashboard file (data model + report) |

---

## 🗂️ About the Data

The dataset contains individual sales order records with the following fields:

`Order_ID`, `Order_Date`, `Customer_ID`, `Sales_Rep`, `Category`, `Product`, `Unit_Price`, `Quantity`, `Discount_Pct`, `Status` (Completed / Pending / Returned), `Region`, `Channel` (Online / Retail Store / Distributor / Direct Sales)

### Data Cleaning Performed

The raw export had several data quality issues that were fixed in `Cleaned data.xlsx`:

- **Fixed header row** — the raw file's actual column headers were sitting in the first data row instead of the header row, so columns initially loaded as generic `Column1, Column2…`.
- **Split a combined column** — `Region` and `Channel` were merged into a single `Region|Channel` field (e.g. `West|Online`) and have been separated into two clean columns.
- **Handled placeholder values** — `Discount_Pct` used `-1` as a placeholder for "no discount"; this was replaced with `0.00` for correct calculations.
- **Removed duplicate/invalid records** — duplicate `Order_ID` entries were removed.
- **Standardized data types** — dates, prices, quantities, and percentages were cast to consistent types for Power BI modeling.

> ℹ️ Raw export had 530 rows with 30 duplicate Order_IDs. After de-duplication the cleaned dataset contains 500 unique orders with no nulls. — see the two files for the exact before/after counts.

---

## 🧮 Data Model (Power BI)

The `.pbix` file uses a star-schema-style model with the following tables:

- **Sales_Orders** — fact table (order-level transactions)
- **Customers** — dimension table
- **Products** — dimension table
- **Measures** — dedicated table holding DAX measures (e.g. revenue, order counts)

---

## 📑 Report Pages

| Page | Status | Contents |
|---|---|---|
|  | ✅ Overview | KPI summary card |
| Sales | ✅ Mostly built | Main dashboard — KPI card, slicers/filters, trend line chart, bar chart, donut chart, 100% stacked column chart |
| Performance | ✅ In progress | Breakdown table and 100% stacked bar chart |
| Products & Returns | 🔲 Not started | Currently placeholder shapes/textboxes only — layout not yet designed |

---

## 🛠️ Tools Used

- **Microsoft Excel** — raw data review and cleaning
- **Power Query (Excel/Power BI)** — data transformation
- **Power BI Desktop** — data modeling (DAX measures) and dashboard/report building

---

## ▶️ How to View This Project

1. Clone or download this repository.
2. Open `Sales_analysis_Dashboard.pbix` in [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free) to explore the report and data model.
3. Open `Cleaned data.xlsx` or `Raw_data_sales_Analysis.xlsx` in Excel to review the underlying data and cleaning steps.

---

## 📝 What's Left To Do

- [ ] Finish designing Page 4
- [ ] Add more DAX measures (e.g. YoY growth, average order value, return rate)
- [ ] Polish formatting, color theme, and tooltips across all pages
- [ ] Add dashboard screenshots to this README once complete

---

## 📌 Notes

This is a personal/learning project built to practice the end-to-end analytics workflow: raw data → cleaning → data modeling → dashboard design. Feedback and suggestions are welcome!
