# Uber Trips Data Analytics Case Study

## Problem Statement and Stakeholder Context
Urban mobility providers like Uber need to constantly optimize their operations to maximize revenue, improve driver efficiency, and enhance rider experience. Stakeholders (Operations Managers, City Planners, and Financial Analysts) require a comprehensive view of trip volumes, fare distributions, payment preferences, and geographic hotspots to make informed decisions regarding dynamic pricing, driver allocation, and market expansion.

## Dataset Source and Scope
The analysis is based on the `uber_trips_dataset_50k.csv` dataset, which contains 50,000 anonymized trips.
The scope covers:
- **Geographic Data:** Pickup and drop-off coordinates (`pickup_lat`, `pickup_lng`, `drop_lat`, `drop_lng`) and `city`.
- **Trip Details:** `distance_km`, `fare_amount`, and `status` (Completed, Cancelled, No-Show).
- **Time Data:** `pickup_time` and `drop_time`.
- **User Demographics:** `rider_id`, `driver_id`, and `payment_method` (Cash, Wallet, UPI, Card).

## Cleaning and Transformation Summary
- Filtered out anomalous records with negative distances or fares.
- Handled missing values in trip status and payment methods.
- Created calculated fields for trip duration and time-of-day categorization (e.g., peak vs. off-peak hours).
- Extracted localized hotspots using spatial coordinates.

## KPI Framework
- **Total Revenue (Fare Amount):** To track financial performance.
- **Average Trip Distance:** To understand rider behavior and operational range.
- **Trip Status Distribution:** To monitor operational efficiency (Completed vs. Cancelled/No-Show rates).
- **Payment Method Preference:** To optimize financial transaction channels.

## Key Insights
1. **Hotspot Identification:** Certain downtown areas consistently show high pickup densities, suggesting areas for targeted driver incentives during peak hours.
2. **Revenue Distribution:** A significant portion of revenue is generated during specific timeframes, highlighting the effectiveness of dynamic pricing.
3. **Payment Preferences:** Digital payments (UPI and Wallet) are increasingly preferred over cash, indicating a shift in user behavior.
4. **Cancellation Rates:** Analyzing trip statuses reveals specific zones or times with higher cancellation rates, pointing to potential service bottlenecks.

## Tableau Dashboard
**[🌐 View the Live Dashboard on Tableau Public](https://public.tableau.com/views/UBER_DASHBOARD_17774874825370/Dashboard1?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)**

![Uber Dashboard Preview](Uber_Dashboard/assets/Screenshot%202026-03-15%20at%201.22.16%E2%80%AFPM.png)

## Recommendations and Expected Impact
- **Targeted Driver Incentives:** Allocate more drivers to identified hotspots during peak hours to reduce wait times and cancellations.
- **Promote Digital Payments:** Offer promotions for UPI or Wallet usage to streamline transactions and reduce cash handling overhead.
- **Operational Optimization:** Investigate the root causes of high cancellation rates in specific areas to improve the overall completion rate.
- **Expected Impact:** Implementing these strategies is expected to increase total completed trips, boost overall revenue, and enhance customer satisfaction.
