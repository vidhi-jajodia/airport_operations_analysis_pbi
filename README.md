# ✈️ Airport Operations Analysis Dashboard | Power BI
### Flight Performance, Delay Analysis, Passenger Trends & Operational Intelligence

The report uses a multi-table airport operations dataset and presents both operational KPIs and drill-down analysis across five core report pages plus a dynamic insights page.

## Project Overview

This dashboard answers key airport performance questions:

- Are flights departing on time?
- Which airlines, gates, routes, and delay reasons need attention?
- How are passengers moving through check-in and security?
- Where are baggage handling exceptions occurring?
- Which retail categories and stores generate the most revenue?
- How are staff coverage, overtime, and aircraft maintenance affecting operations?


## Data Model

The report uses a star-style model with dimension tables filtering fact tables.

Dimension Tables:

- `dim_flight`
- `dim_passenger`
- `dim_staff`
- `dim_date`
- `dim_time`

Fact Tables:

- `fact_flights`
- `fact_passengers`
- `fact_baggage`
- `fact_gate_events`
- `fact_security_clearance`
- `fact_retail`
- `fact_staff_shifts`
- `fact_flight_maintenance`

Relationships use single-direction filtering from dimensions to fact tables.

## Report Pages

### 1. Executive Overview

High-level airport performance summary.

KPIs and visuals include:

- Total Flights
- Total Passengers
- Delay Rate
- Average Delay
- Load Factor
- Retail Revenue
- Mishandled Bag Rate
- Average Queue Wait
- Flight Volume Trend
- Delay Rate by Airline
- Flights by Route Type
- Flights by Delay Category
- Retail Revenue by Product Category

### 2. Flight Operations

Operational analysis of flight delays and turnaround performance.

Includes:

- On-Time Rate
- Cancellation Rate
- Passengers per Flight
- Flights by Delay Reason
- Average Delay by Airline
- Average Turnaround by Aircraft Type
- Delay Rate by Weather Impact
- Gate Performance Matrix

### 3. Passenger & Security Flow

Passenger journey and security processing analysis.

Includes:

- Checked-In Passengers
- No Show Rate
- Average Queue Wait
- Average Screening Duration
- Secondary Screening Rate
- Missed Flights After Security
- Passengers by Cabin Class
- No-Show Rate by Airline
- Queue Wait by Security Lane
- Security Volume and SLA Breaches

### 4. Baggage & Retail

Baggage operations and commercial revenue performance.

Includes:

- Total Bags
- Mishandled Bags
- Mishandled Bag Rate
- Average Bag Weight
- Retail Revenue
- Average Transaction Value
- Retail Revenue per Passenger
- Bags by Current Location
- Baggage Status Breakdown
- Retail Revenue by Product Category
- Retail Revenue by Store
- Average Transaction Value by Payment Method

### 5. Staff & Maintenance

Workforce and aircraft maintenance performance.

Includes:

- Active Staff
- Staff Shifts
- Scheduled Staff Hours
- Overtime Shift Rate
- Maintenance Work Orders
- Grounded Work Orders
- Average Downtime Hours
- Staff Shifts by Department
- Overtime Shift Rate by Department
- Work Orders by Maintenance Type
- Average Downtime by Aircraft Type
- Maintenance Issues by Component
- Maintenance Risk Matrix

### 6. Overall Insights

Dynamic insights page using DAX text measures. Insights update when slicers are changed.

Examples:

- Top airline by delay rate
- Leading delay reason
- Top retail category
- Highest baggage risk airline
- Longest security queue lane
- Highest maintenance downtime aircraft

## 📚 Skills Demonstrated
- Data Cleaning
- Data Modeling
- DAX Calculations
- Dashboard Storytelling
- Aviation Operations Analytics
  
# 📂 Project Structure

```bash
airport_operations_analysis_pbi/
│
├── data/                                                      # Raw dataset
├── export/                                                    # PDF Export
├── screenshots/                                               # Dashboard visuals
├── Airport Operations Performance Dashboard.pbix              # Power BI eXchange File
└── README.md
```

## How To Use

1. Open the Power BI report file in Power BI Desktop.
2. Confirm the source file path parameters point to the local Excel workbook.
3. Refresh the model.
4. Review relationships in Model view.
5. Check measure formatting:
   - Percent measures as percentage
   - Revenue measures as currency
   - Duration measures as decimal numbers
6. Export to PDF or publish to Power BI Service.

---

# 👨‍💻 Author

## Vidhi Jajodia

### Connect:

* GitHub: [vidhi-jajodia](https://github.com/vidhi-jajodia)
* LinkedIn: [vidhi-jajodia](https://www.linkedin.com/in/vidhi-jajodia/)

---

