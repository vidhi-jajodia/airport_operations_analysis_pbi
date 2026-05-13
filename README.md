# Airport Operations Performance Dashboard

Power BI dashboard project for analyzing airport operations across flights, passengers, security, baggage, retail, staffing, and maintenance.

The report uses a multi-table airport operations dataset and presents both operational KPIs and drill-down analysis across five core report pages plus a dynamic insights page.

## Project Overview

This dashboard answers key airport performance questions:

- Are flights departing on time?
- Which airlines, gates, routes, and delay reasons need attention?
- How are passengers moving through check-in and security?
- Where are baggage handling exceptions occurring?
- Which retail categories and stores generate the most revenue?
- How are staff coverage, overtime, and aircraft maintenance affecting operations?

## Dataset

The model is built from an Excel workbook generated from raw CSV files:

```text
airport_powerbi_import.xlsx
```

Source tables include:

- `flights`
- `passengers`
- `baggage`
- `gate_events`
- `security`
- `staff_shifts`
- `retail`
- `maintenance`
- `dim_flight`
- `dim_passenger`
- `dim_staff`

## Data Model

The report uses a star-style model with dimension tables filtering fact tables.

Main dimensions:

- `dim_flight`
- `dim_passenger`
- `dim_staff`
- `dim_date`
- `dim_time`

Main fact tables:

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

## Key DAX Measures

Examples of core measures used in the report:

```DAX
Total Flights =
COUNTROWS(fact_flights)
```

```DAX
Delay Rate % =
DIVIDE(
    [Delayed Flights],
    [Total Flights]
)
```

```DAX
Load Factor % =
DIVIDE(
    [Total Passengers Booked],
    [Total Capacity]
)
```

```DAX
Retail Revenue =
SUM(fact_retail[net_amount])
```

```DAX
Mishandled Bag Rate % =
DIVIDE(
    [Mishandled Bags],
    [Total Bags]
)
```

```DAX
Avg Queue Wait Min =
DIVIDE(
    [Avg Queue Wait Sec],
    60
)
```

## File Path Parameterization

The Power Query source can be parameterized instead of hardcoding the Excel file path.

Recommended parameters:

```text
pFolderPath
pFileName
```

Example values:

```text
pFolderPath = C:\Users\Sanjay\Downloads\multi table\airport-operations-dataset
pFileName = airport_powerbi_import.xlsx
```

Power Query source:

```powerquery
let
    SourcePath = pFolderPath & "\" & pFileName,
    Source = Excel.Workbook(File.Contents(SourcePath), null, true)
in
    Source
```

For cleaner maintenance, create a shared query named `SourceWorkbook` and reference it from each table query.

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

## Exported Report

The final dashboard can be exported as:

```text
airport-operations.pdf
```

## Notes

- The raw dataset originally had numeric placeholder headers, so business-friendly column names were added during preparation.
- Some sample data was adjusted to add realistic variation for baggage locations, baggage statuses, payment methods, departments, maintenance types, and components.
- Use single-direction relationships to avoid ambiguous filter paths.
- If sharing the report, consider saving it as a Power BI template file (`.pbit`) so users can enter their own source path parameters.

## Report Name

```text
Airport Operations Performance Dashboard
```
