# 🚗 OLA Ride-Hailing Sales & Operational Performance Analysis (Power BI)

An interactive **Power BI Data Analytics Solution** analyzing **103,024 ride bookings** for **OLA** across July 2024. This project uncovers ride demand trends, revenue potential, vehicle category efficiencies, payment channel distribution, cancellation failure modes, and two-way service satisfaction ratings built entirely in **Power BI Desktop**.

---

## 📁 Repository Directory Structure

```
Ola_PowerBI_Project/
├── Dashboard/
│   └── OLA_Project.pbix           # Native Power BI Desktop Report File
├── Data/
│   ├── sales_data.csv             # Cleaned Ride Transaction Data (103,024 rows)
│   └── customer_data.csv          # Customer Profiles & Demographics (4,990 rows)
├── Web_App/
│   ├── index.html                 # Interactive Web Dashboard Portal
│   ├── styles.css                 # Dark Glassmorphism Styling
│   └── app.js                     # Chart.js Visualizations & Logic
└── README.md                      # Complete Project Documentation
```

---

## 📊 Power BI Report Structure by Page Number

---

### 🔹 Page 1: Overall Performance Dashboard

*Focuses on macro-level operational KPIs, booking status breakdown, and temporal volume dynamics.*

#### Key Metrics & Figures:
* **Total Booking Volume**: `103,024` rides
* **Total Booking Value**: `₹35.00 Million` gross demand potential
* **Booking Status Composition**:
  * **Success**: `63,967` rides (**62.09%**)
  * **Canceled by Driver**: `18,430` rides (**17.89%**)
  * **Canceled by Customer**: `10,500` rides (**10.19%**)
  * **Driver Not Found**: `10,127` rides (**9.83%**)
* **Ride Volume Over Time**: Daily booking counts hovered between `3,050` and `3,420` rides per day throughout July 2024.

---

### 🔹 Page 2: Vehicle Type Performance Matrix

*Evaluates gross demand, completed revenue, and ride distance across 7 vehicle categories.*

#### Category Breakdown:

| Vehicle Type | Total Booking Value | Successful Booking Value | Avg. Distance (km) | Total Distance (km) |
| :--- | :---: | :---: | :---: | :---: |
| **Prime Sedan** | ₹8.30M | ₹5.22M | 25.01 | 235K |
| **Prime SUV** | ₹7.93M | ₹5.22M | 24.88 | 224K |
| **Prime Plus** | ₹8.05M | ₹5.22M | 25.03 | 227K |
| **Mini** | ₹7.99M | ₹5.22M | 24.98 | 226K |
| **Auto** | ₹8.09M | ₹5.22M | 10.04 | 92K |
| **Bike** | ₹7.99M | ₹5.22M | 24.93 | 228K |
| **E-Bike** | ₹8.18M | ₹5.22M | 25.15 | 231K |

---

### 🔹 Page 3: Revenue & Customer Insights

*Analyzes payment channel market share, daily distance trends, and top customer value rankings.*

#### Financial & Passenger Metrics:
* **Revenue by Payment Method**:
  * **Cash**: `₹18.5M` (Primary payment method)
  * **UPI**: `₹13.8M` (Leading digital payment channel)
  * **Credit Card**: `₹2.7M`
  * **Debit Card**: `₹2.1M`
* **Top 5 Customers by Booking Value**:
  1. `CID785112` — **₹8,025**
  2. `CID308763` — **₹6,281**
  3. `CID734557` — **₹6,177**
  4. `CID353074` — **₹6,110**
  5. `CID836942` — **₹6,019**
  * **Top 5 Combined Value**: **₹32,612**

---

### 🔹 Page 4: Cancellation Diagnostics

*Pinpoints fulfillment failures, unfulfilled demand, and driver/customer cancellation drivers.*

#### Operational Failure Breakdown:
* **Total Cancellations**: `28,933` rides (**28.08%** cancellation rate)
* **Driver Not Found**: `10,127` unassigned rides (**9.83%** of total demand)
* **Customer Cancellation Reasons**:
  1. *Driver is not moving towards pickup*: **30.24%** (3,180 rides)
  2. *Driver asked to cancel*: **25.43%** (2,670 rides)
  3. *Change of plans*: **19.82%** (2,080 rides)
  4. *AC is Not working*: **14.93%** (1,570 rides)
  5. *Wrong Address*: **9.57%** (1,010 rides)
* **Driver Cancellation Reasons**:
  1. *Personal & Car related issue*: **35.49%** (6,540 rides)
  2. *Customer related issue*: **29.36%** (5,410 rides)
  3. *Customer was coughing/sick*: **19.82%** (3,650 rides)
  4. *More than permitted people*: **15.32%** (2,830 rides)

---

### 🔹 Page 5: Ratings & Service Quality Analysis

*Measures two-way service ratings between drivers and customers across all vehicle categories.*

#### Ratings Comparison Matrix:

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

## 🧮 Key Power BI DAX Measures

```dax
-- Total Bookings Count
Total_Bookings = COUNT(sales_data[Booking_ID])

-- Successful Bookings Count
Successful_Bookings = CALCULATE(
    COUNT(sales_data[Booking_ID]), 
    sales_data[Booking_Status] = "Success"
)

-- Total Booking Value
Total_Booking_Value = SUM(sales_data[Booking_Value])

-- Successful Booking Value
Successful_Booking_Value = CALCULATE(
    SUM(sales_data[Booking_Value]),
    sales_data[Booking_Status] = "Success"
)

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

## 💡 Strategic Business Insights & Recommendations

1. **Automate Idle Rerouting**: 30.24% of customer cancellations occur because the driver is not moving towards pickup. Implementing an automated re-dispatch system after 3 minutes of zero movement will recover ~3,000 lost bookings per month.
2. **Standardize AC Quality Audits**: AC breakdown caused 1,570 customer cancellations. Require mandatory pre-summer climate control compliance for Prime Sedan, SUV, and Plus vehicles.
3. **Incentivize Digital UPI Payments**: Cash represents over 50% of payment volume (₹18.5M). Offering 5% instant cashback for UPI transactions will streamline driver cash collection and reduce dispute rates.

---

## 🌐 Interactive Web Application

Launch the web portal locally by opening [`Web_App/index.html`](Web_App/index.html) in any web browser to view dynamic Chart.js visualizations, explore vehicle tables, and interact with the Power BI dashboard metrics.

---

*Project created & documented by **Satyam Singh** | OLA Power BI Business Intelligence Analytics Suite*
