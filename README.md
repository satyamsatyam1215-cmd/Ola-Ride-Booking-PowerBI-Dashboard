# 🚗 OLA Ride-Hailing Sales & Operational Performance Analysis (Power BI + SQL)

![OLA Executive Banner](Images/page1.png)

## 📌 Executive Summary
This repository houses an end-to-end **Power BI & SQL Data Analytics Solution** analyzing **103,024 ride bookings** for **OLA** across July 2024. The analytics suite evaluates key business drivers including ride booking volumes, gross booking values, vehicle category efficiencies, payment channel distribution, customer lifetime values, cancellation failure modes, and driver/customer service satisfaction ratings.

The project features a **5-Page Power BI Desktop Report**, clean datasets (103K rows), 15 production SQL queries, and an interactive dark-mode web application portal.

---

## 📁 Repository Directory Structure

```
Ola_PowerBI_Project/
├── Dashboard/
│   └── OLA_Project.pbix           # Native Power BI Desktop Report File
├── Data/
│   ├── sales_data.csv             # Raw & Processed Ride Transactions (103,024 rows)
│   └── customer_data.csv          # Customer Profiles & Demographics (4,990 rows)
├── Images/
│   ├── dashboard_overview.png     # Executive Summary Banner View
│   ├── page1.png                  # Page 1: Overall Performance Dashboard
│   ├── page2.png                  # Page 2: Vehicle Type Performance Matrix
│   ├── page3.png                  # Page 3: Revenue & Payment Method Distribution
│   ├── page4.png                  # Page 4: Cancellation Diagnostics & Root Causes
│   └── page5.png                  # Page 5: Customer & Driver Ratings Analysis
├── SQL/
│   └── ola_analytics_queries.sql  # Production SQL Analysis Queries
├── Web_App/
│   ├── index.html                 # Interactive Web Dashboard Portal UI
│   ├── styles.css                 # Dark Glassmorphism Design System
│   └── app.js                     # Chart.js Visualizations & Logic
└── README.md                      # Complete Technical & Business Documentation
```

---

## 📊 5-Page Power BI Dashboard Gallery & Detailed Metrics

---

### 1. Page 1 — Overall Performance View
*Focuses on high-level operational KPIs, booking status composition, and daily volume trends.*

[![Page 1 - Overall View](Images/page1.png)](Images/page1.png)

#### 🔢 Key Metrics & Breakdown:
- **Total Booking Volume**: `103,024` rides.
- **Total Booking Value**: `₹35.00 Million` gross potential.
- **Booking Status Composition**:
  - **Success**: `63,967` rides (**62.09%**)
  - **Canceled by Driver**: `18,430` rides (**17.89%**)
  - **Canceled by Customer**: `10,500` rides (**10.19%**)
  - **Driver Not Found**: `10,127` rides (**9.83%**)
- **Ride Volume Over Time**: Daily booking counts hovered between `3,050` and `3,420` rides per day throughout July 2024.

---

### 2. Page 2 — Vehicle Type Breakdown View
*Evaluates gross demand, completed revenue, and ride distance across 7 vehicle categories.*

[![Page 2 - Vehicle Type View](Images/page2.png)](Images/page2.png)

#### 🚘 Vehicle Performance Matrix:

| Vehicle Type | Total Booking Value | Successful Value | Avg. Distance (km) | Total Distance (km) |
| :--- | :--- | :--- | :--- | :--- |
| **Prime Sedan** | **₹8.30M** | **₹5.22M** | **25.01** | **235K** |
| **Prime SUV** | **₹7.93M** | **₹5.22M** | **24.88** | **224K** |
| **Prime Plus** | **₹8.05M** | **₹5.22M** | **25.03** | **227K** |
| **Mini** | **₹7.99M** | **₹5.22M** | **24.98** | **226K** |
| **Auto** | **₹8.09M** | **₹5.22M** | **10.04** | **92K** |
| **Bike** | **₹7.99M** | **₹5.22M** | **24.93** | **228K** |
| **E-Bike** | **₹8.18M** | **₹5.22M** | **25.15** | **231K** |

---

### 3. Page 3 — Revenue & Customer Insights View
*Analyzes payment channel market share, daily distance trends, and top customer value rankings.*

[![Page 3 - Revenue View](Images/page3.png)](Images/page3.png)

#### 💳 Financial Highlights:
- **Revenue by Payment Channel**:
  - **Cash**: `₹18.5M` (Primary payment method)
  - **UPI**: `₹13.8M` (Leading digital payment channel)
  - **Credit Card**: `₹2.7M`
  - **Debit Card**: `₹2.1M`
- **Top 5 Customers by Booking Value**:
  1. `CID785112` — **₹8,025**
  2. `CID308763` — **₹6,281**
  3. `CID734557` — **₹6,177**
  4. `CID353074` — **₹6,110**
  5. `CID836942` — **₹6,019**
  - **Combined Top 5 Total**: **₹32,612**

---

### 4. Page 4 — Cancellation Diagnostics View
*Pinpoints fulfillment failures, unfulfilled demand, and driver/customer cancellation drivers.*

[![Page 4 - Cancellation View](Images/page4.png)](Images/page4.png)

#### 🚫 Failure Diagnostics:
- **Total Cancellations**: `28,933` rides (**28.08%** cancellation rate).
- **Driver Not Found**: `10,127` unassigned rides (**9.83%** of total demand).
- **Customer Cancellation Reasons**:
  1. *Driver is not moving towards pickup*: **30.24%** (3,180 rides)
  2. *Driver asked to cancel*: **25.43%** (2,670 rides)
  3. *Change of plans*: **19.82%** (2,080 rides)
  4. *AC is Not working*: **14.93%** (1,570 rides)
  5. *Wrong Address*: **9.57%** (1,010 rides)
- **Driver Cancellation Reasons**:
  1. *Personal & Car related issue*: **35.49%** (6,540 rides)
  2. *Customer related issue*: **29.36%** (5,410 rides)
  3. *Customer was coughing/sick*: **19.82%** (3,650 rides)
  4. *More than permitted people*: **15.32%** (2,830 rides)

---

### 5. Page 5 — Ratings & Quality View
*Measures two-way service ratings between drivers and customers across all vehicle categories.*

[![Page 5 - Ratings View](Images/page5.png)](Images/page5.png)

#### ⭐️ Rating Comparison Matrix:

| Vehicle Type | Avg. Customer Rating | Avg. Driver Rating |
| :--- | :---: | :---: |
| **Prime Sedan** | `3.99` | `4.00` |
| **Prime SUV** | `4.01` | `4.00` |
| **Prime Plus** | `4.00` | `4.01` |
| **Mini** | `3.99` | `4.00` |
| **Auto** | `4.00` | `4.00` |
| **Bike** | `3.98` | `3.99` |
| **E-Bike** | `4.01` | `3.99` |

---

## 🧮 Key DAX Measures

```dax
-- Total Bookings
Total_Bookings = COUNT(sales_data[Booking_ID])

-- Successful Bookings Count
Successful_Bookings = CALCULATE(
    COUNT(sales_data[Booking_ID]), 
    sales_data[Booking_Status] = "Success"
)

-- Total Booking Value
Total_Booking_Value = SUM(sales_data[Booking_Value])

-- Cancellation Rate %
Cancellation_Rate = DIVIDE(
    CALCULATE(
        COUNT(sales_data[Booking_ID]), 
        sales_data[Booking_Status] IN {"Canceled by Customer", "Canceled by Driver"}
    ),
    [Total_Bookings],
    0
)

-- Average Distance per Ride
Avg_Ride_Distance = AVERAGE(sales_data[Ride_Distance])
```

---

## 🔍 Featured SQL Queries

Production SQL scripts are available in [`SQL/ola_analytics_queries.sql`](SQL/ola_analytics_queries.sql).

```sql
-- 1. Retrieve all successful bookings
SELECT * 
FROM sales_data 
WHERE Booking_Status = 'Success';

-- 2. Find average ride distance for each vehicle type
SELECT 
    Vehicle_Type, 
    ROUND(AVG(Ride_Distance), 2) AS Avg_Distance_KM 
FROM sales_data 
GROUP BY Vehicle_Type 
ORDER BY Avg_Distance_KM DESC;

-- 3. Top 5 customers by total booking value
SELECT 
    Customer_ID, 
    COUNT(Booking_ID) AS Total_Rides, 
    SUM(Booking_Value) AS Sum_Booking_Value 
FROM sales_data 
GROUP BY Customer_ID 
ORDER BY Sum_Booking_Value DESC 
LIMIT 5;

-- 4. Driver cancellations due to personal & car issues
SELECT COUNT(*) AS Personal_Car_Cancellations 
FROM sales_data 
WHERE Canceled_Rides_by_Driver = 'Personal & Car related issue';
```

---

## 💡 Strategic Business Insights & Recommendations

1. **Automate Idle Rerouting**: 30.24% of customer cancellations occur because the driver is not moving towards pickup. Implementing an automated re-dispatch system after 3 minutes of zero movement will recover ~3,000 lost bookings per month.
2. **Standardize AC Quality Audits**: AC breakdown caused 1,570 customer cancellations. Require mandatory pre-summer climate control compliance for Prime Sedan, SUV, and Plus vehicles.
3. **Incentivize Digital UPI Payments**: Cash represents over 50% of payment volume (₹18.5M). Offering 5% instant cashback for UPI transactions will streamline driver cash collection and reduce dispute rates.

---

## 🌐 Interactive Web Application

Launch the web portal locally by opening [`Web_App/index.html`](Web_App/index.html) in any web browser to view dynamic Chart.js visualizations, explore vehicle tables, and run interactive SQL queries.

---

*Project created & documented by Satyam Singh | OLA Power BI Business Intelligence Analytics Suite*
