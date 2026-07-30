# 🚗 OLA Ride-Hailing Sales & Operational Performance Analysis (Power BI + SQL)

![OLA Analytics Banner](Images/dashboard_overview.png)

## 📌 Project Overview
This repository contains a comprehensive **Power BI Business Intelligence & Data Analytics Solution** analyzing **103,024 ride bookings** for **OLA** (July 2024). The project diagnoses ride volume trends, vehicle class performance, revenue distribution by payment channels, top customer segments, driver/customer cancellation drivers, and service quality ratings.

It includes an interactive Power BI report (`.pbix`), optimized SQL analytics scripts, cleaned datasets (103K rows), high-resolution dashboard screenshots, and an interactive web portal.

---

## 📁 Repository Directory Structure

```
Ola_PowerBI_Project/
├── Dashboard/
│   └── OLA_Project.pbix           # Native Power BI Desktop Report File
├── Data/
│   ├── sales_data.csv             # Raw & Transformed Sales Records (103,024 rows)
│   └── customer_data.csv          # Customer Demographics & Profiles (4,990 rows)
├── Images/
│   ├── dashboard_overview.png     # Full Dashboard Executive Summary View
│   ├── page1.png                  # Overall Performance View Screenshot
│   ├── page2.png                  # Vehicle Type Breakdown View Screenshot
│   ├── page3.png                  # Revenue & Payment Share Screenshot
│   └── page4.png                  # Cancellation Diagnostics View Screenshot
├── SQL/
│   └── ola_analytics_queries.sql  # Production SQL Queries (PostgreSQL / MySQL / BigQuery)
├── Web_App/
│   ├── index.html                 # Interactive Web Portal UI
│   ├── styles.css                 # Dark Glassmorphism Design System
│   └── app.js                     # Chart.js Visualizations & Logic
└── README.md                      # Project Documentation
```

---

## 📊 Power BI Dashboard Views

### 1. Overall Performance View (`page1.png`)
*Focuses on macro-level operational metrics, status breakdown, and temporal volume dynamics.*

![Page 1 - Overall View](Images/page1.png)

- **Total Bookings**: `103,024` rides processed in July 2024.
- **Total Booking Value**: `₹35 Million` gross booking potential.
- **Booking Status Breakdown**:
  - **Success**: `63,967` (62.09%)
  - **Canceled by Driver**: `18,430` (17.89%)
  - **Canceled by Customer**: `10,500` (10.19%)
  - **Driver Not Found**: `10,127` (9.83%)
- **Ride Volume Over Time**: Daily ride demand fluctuated between `3,050` and `3,420` rides per day.

---

### 2. Vehicle Type Breakdown View (`page2.png`)
*Analyzes demand, completed gross revenue, and ride distance across 7 vehicle categories.*

![Page 2 - Vehicle Type View](Images/page2.png)

| Vehicle Type | Total Booking Value | Successful Value | Avg Distance (km) | Total Distance (km) |
| :--- | :--- | :--- | :--- | :--- |
| **Prime Sedan** | ₹8.30M | ₹5.22M | 25.01 | 235K |
| **Prime SUV** | ₹7.93M | ₹5.22M | 24.88 | 224K |
| **Prime Plus** | ₹8.05M | ₹5.22M | 25.03 | 227K |
| **Mini** | ₹7.99M | ₹5.22M | 24.98 | 226K |
| **Auto** | ₹8.09M | ₹5.22M | 10.04 | 92K |
| **Bike** | ₹7.99M | ₹5.22M | 24.93 | 228K |
| **E-Bike** | ₹8.18M | ₹5.22M | 25.15 | 231K |

---

### 3. Revenue & Customer Insights View (`page3.png`)
*Evaluates payment channel preferences, distance distributions, and top revenue-generating customers.*

![Page 3 - Revenue View](Images/page3.png)

- **Revenue by Payment Method**:
  - **Cash**: `₹18.5M` (Primary mode for offline bookings)
  - **UPI**: `₹13.8M` (Fastest growing digital channel)
  - **Credit Card**: `₹2.7M`
  - **Debit Card**: `₹2.1M`
- **Top 5 Customers by Booking Value**:
  1. `CID785112` — **₹8,025**
  2. `CID308763` — **₹6,281**
  3. `CID734557` — **₹6,177**
  4. `CID353074` — **₹6,110**
  5. `CID836942` — **₹6,019**

---

### 4. Cancellation Diagnostics View (`page4.png`)
*Deep dive into failure modes, cancellation roots, and fulfillment bottlenecks.*

![Page 4 - Cancellation View](Images/page4.png)

- **Overall Cancellation Rate**: **28.08%** (`28,933` canceled rides).
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

## 🧮 DAX Measures (Power BI)

```dax
-- Total Bookings
Total_Bookings = COUNT(sales_data[Booking_ID])

-- Successful Bookings Count
Successful_Bookings = CALCULATE(COUNT(sales_data[Booking_ID]), sales_data[Booking_Status] = "Success")

-- Total Booking Value
Total_Booking_Value = SUM(sales_data[Booking_Value])

-- Cancellation Rate %
Cancellation_Rate = DIVIDE(
    CALCULATE(COUNT(sales_data[Booking_ID]), sales_data[Booking_Status] IN {"Canceled by Customer", "Canceled by Driver"}),
    [Total_Bookings],
    0
)
```

---

## 🔍 Key SQL Queries Highlights

### Retrieve Top 5 Customers by Booking Value
```sql
SELECT 
    Customer_ID,
    COUNT(Booking_ID) AS Total_Rides,
    SUM(Booking_Value) AS Sum_Booking_Value
FROM sales_data
GROUP BY Customer_ID
ORDER BY Sum_Booking_Value DESC
LIMIT 5;
```

### Driver Personal & Vehicle Issue Cancellations
```sql
SELECT COUNT(*) AS Personal_Car_Cancellations
FROM sales_data
WHERE Canceled_Rides_by_Driver = 'Personal & Car related issue';
```

*(Full suite of 15 queries available in [`SQL/ola_analytics_queries.sql`](SQL/ola_analytics_queries.sql))*

---

## 💡 Strategic Recommendations

1. **Reduce Driver-Induced Cancellations**: 30.2% of customer cancellations stem from drivers idling/not moving toward pickup. Implement automated dispatch rerouting if driver telemetry shows zero movement within 3 minutes of acceptance.
2. **AC Maintenance Protocol**: AC failure accounted for ~1,570 customer cancellations during peak summer. Introduce quarterly vehicle condition audits for Prime Sedan & SUV tiers.
3. **Cash-to-Digital Conversion**: Cash accounts for >50% of revenue. Offer 5% cashback incentives for UPI payments to reduce driver cash handling friction.

---

## 💻 Interactive Web Application

An interactive web application is available in the [`Web_App/`](Web_App/) directory. Open `Web_App/index.html` in any modern browser to explore live interactive charts, tables, and the SQL query runner.

---

*Project created & documented by Satyam Singh | OLA Business Intelligence Analytics Suite*
