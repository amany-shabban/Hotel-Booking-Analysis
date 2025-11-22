# Hotel Booking Analysis
## Dataset
- **Source**: Kaggle hotel booking dataset :contentReference https://www.kaggle.com/datasets/mojtaba142/hotel-booking   
- **Description**: The dataset includes reservation data for city and resort hotels, with features like booking date, arrival date, lead time, cancellation status, average daily rate (ADR), number of special requests, and more.
The dataset comprises 119,390 booking records from:
- **City Hotel (H2)**: 79,330 bookings
- **Resort Hotel (H1)**: 40,060 bookings

## Data Processing Pipeline
### 1. Data Acquisition & Profiling
- Downloaded flat CSV file from Kaggle containing 31 original variables
- Conducted initial data profiling to understand structure, data types, and business context
- Reviewed variable descriptions from original research paper

### 2. Data Quality Assessment & Cleaning
- **Duplicate Detection**: Verified no duplicate booking records exist
- **Missing Value Analysis**: Identified and handled null values in country, agent, and company fields
- **Outlier Treatment**: Applied statistical methods to detect and treat anomalies in lead_time, ADR, and stays
- **Data Validation**: Ensured referential integrity across booking components

### 3. Dimensional Modeling
Transformed denormalized dataset into star schema architecture:
**Fact Table**
- `Fact_Hotels_Booking`: Central fact table with 33 columns including booking metrics, financial data, and behavioral indicators
**Dimension Tables**
- `DimDate`: Custom calendar dimension with Year, Month, Day hierarchy for time-based analysis
- `dimCustomer`: Customer profiles extracted from booking data (customer_type, demographics)
- `dimCountry`: Geographic dimension based on ISO 3155-3:2013 country codes
- `dimHotel_type`: Hotel classification (City Hotel vs Resort Hotel)
- `dimDeposit`: Deposit type categories (No Deposit, Non-Refund, Refundable)
**Relationships**
- Implemented one-to-many relationships with proper cardinality
- Active relationship established on `Arrival_Date` to `DimDate`
- Inactive relationship on `reservation_status_date` for alternative temporal analysis
### 4. Measure Development
Created DAX measures aligned with hospitality industry KPIs:
- Booking volume metrics and cancellation analytics
- Revenue calculations (ADR × nights stayed)
- Occupancy and utilization rates
- Customer retention indicators (repeat guest percentage)
- Average length of stay calculations
### 5. Dashboard Development
Built multi-page analytical dashboards covering:
- Executive KPI overview
- Revenue performance and pricing analysis
- Booking trends and seasonality patterns
- Customer segmentation and behavior
- Cancellation analysis and risk indicators

## Dashboard KPIs
The dashboards feature the following key performance indicators:
### Primary Business Metrics
- **Total Bookings**: Total count of all booking records (119,390)
- **Total Revenue**: Aggregate revenue generated from all bookings ($42.7M)
- **Completed Bookings**: Number of bookings that were not canceled (75,180)
- **Total Cancelation**: Count of canceled bookings (44,210)

### Performance Indicators
- **Cancelation Rate**: Percentage of bookings that were canceled (37.04%)
- **Occupancy Rate**: Percentage of completed bookings vs total bookings (62.96%)
- **Average ADR**: Average Daily Rate across all bookings ($101.79)
- **Avg LOS**: Average Length of Stay in nights
- **Repeat Guest %**: Percentage of bookings from returning customers

### Operational Metrics
- **Total Gustes**: Total number of guests (adults + children + babies) across all bookings

All KPIs are interactive and can be filtered by:
- Date range (Year, Month, Day)
- Hotel type (City Hotel vs Resort Hotel)
- Market segment and distribution channel
- Customer type and country
- Booking status and deposit type

## Key Insights & Recommendations
### Dashboard 1: Revenue & Market Performance
**Insights:**
- City Hotels generate 59% of total revenue ($25.3M vs $17.4M) with higher booking volume (79,330 vs 40,060 bookings)
- Online Travel Agencies dominate distribution channels with $23.9M revenue (56% of total) but exhibit 36.7% cancellation rate

### Dashboard 2: Customer Behavior & Operational Patterns
**Insights:**
- Transient customers account for 79% of all bookings (94,496), representing core business segment
- Repeat guests show significantly lower cancellation rate (14.5%) compared to first-time guests (37.8%), demonstrating 2.6x better retention
- Bed & Breakfast meal plan dominates with 77% of bookings (92,310) generating $31.1M revenue
- Portuguese domestic market represents 41% of total bookings (48,590), followed by UK (10%) and France (9%)
- Non-refundable deposits paradoxically correlate with 99.4% cancellation rate (14,587 bookings), suggesting pricing or policy issues
- Peak season concentration in July-August generates 62% higher revenue than winter months, creating operational capacity challenges
**Recommendations:**
- Launch loyalty rewards program specifically targeting Transient segment to convert first-time guests into repeaters and reduce 37.8% cancellation rate
- Investigate non-refundable deposit policy effectiveness as current 99.4% cancellation rate indicates potential fraud or system misclassification
- Create seasonal promotional campaigns for shoulder periods (January-March, September-November) to smooth demand curves and improve annual occupancy rates
- Develop domestic market retention strategies targeting Portuguese guests who comprise largest booking segment
- Expand meal package options beyond BB to capture upsell opportunities, particularly Half-Board packages for resort properties
- Implement predictive cancellation model prioritizing high-risk factors: no deposit, TA/TO channel, and long lead times for proactive intervention


<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/510c6a48-556d-4c1c-8aa2-f6c8f3d770cf" width="400"/></td>
    <td><img src="https://github.com/user-attachments/assets/b7b60ca8-acb8-4cda-87e9-a850586186fd" width="400"/></td>
  </tr>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/3578c2cf-eb39-42e1-8193-12f60adb3149" width="400"/></td>
    <td><img src="https://github.com/user-attachments/assets/b538b1d8-5971-49c4-b8e8-dcec637e96f7" width="400"/></td>
  </tr>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/0d05f657-0865-478c-90d4-7aacb6578ef6" width="400"/></td>
    <td><img src="https://github.com/user-attachments/assets/14c5371f-af93-4b66-bf63-6db611d26bb1" width="400"/></td>
  </tr>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/e296fc94-3f1e-4f3b-b11c-cc47039c08d5" width="400"/></td>
    <td><img src="https://github.com/user-attachments/assets/f88a7088-3fa3-4309-9755-32028f3c8295" width="400"/></td>
  </tr>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/1d3ba0aa-a8b7-4713-9101-4b02e788c390" width="400"/></td>
    <td><img src="https://github.com/user-attachments/assets/a4b86919-573d-4ba5-abc0-d2af0cdb3afc" width="400"/></td>
  </tr>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/4babd3e5-7cdf-4efe-b831-2ed044f52f92" width="400"/></td>
  </tr>
</table>
