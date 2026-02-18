# Fitness Center Analytics Dashboard

Power BI dashboard for fitness center operations management, built with custom data modeling, DAX measures, and interactive health calculators. Uses SATS fitness chain as the case study.

## Dashboard Overview

Four-page interactive dashboard designed to answer daily management questions and enable proactive member retention.

```
Home --> Overall --> Calculator --> Members
  |         |            |             |
Landing   KPIs &      BMI/BMR       Member
 Page    Financials   TDEE Calc    Details
```

## Dashboard Pages

### 1. Home
Landing page with SATS branding and navigation to all dashboard sections.

### 2. Overall (Operations View)

**Key Performance Indicators:**
| Metric | Value |
|--------|-------|
| Total Clients | 100 |
| Trainers | 20 |
| Revenue | 4.1M |
| Expenses | 1.2M |
| Profit | 2.9M |

**Visualizations:**
- Monthly financial trend (Revenue, Expenses, Profit)
- Membership tier breakdown (Platinum, Gold, Silver)
- Active vs. Expired membership status
- Monthly member acquisition chart
- Client membership table with completion percentage

### 3. Calculator (Health Metrics)

Interactive calorie and body composition calculator.

**Inputs:**
- Gender (Male/Female)
- Age
- Height
- Weight
- Activity Type (Light, Moderate, Heavy exercise frequency)

**Calculated Outputs:**
| Metric | Description |
|--------|-------------|
| BMI | Body Mass Index with status indicator (Normal/Overweight/Obese) |
| BMR | Basal Metabolic Rate |
| TDEE | Total Daily Energy Expenditure |
| Maintenance Calories | Daily intake to maintain weight |
| Mild Weight Loss | Calorie target for gradual reduction |
| Weight Loss | Moderate deficit target |
| Extreme Weight Loss | Maximum deficit target |

### 4. Members (Individual View)

Detailed member information with filtering and drill-down capabilities.

**Demographics:**
- Members by Age and Gender (bar chart)
- Members by Age and Status (Active/Expired)

**Member Table Columns:**
- Name
- Gender
- Status (Active/Expired)
- Goal (Maintenance/Muscle Gain/Weight Loss)
- Membership Progress (%)
- Age
- BMI
- Membership Tier

## Data Model

Custom dataset built from scratch with proper relationships and star schema design.

**Entities:**
- Members (dimension)
- Trainers (dimension)
- Membership Tiers (dimension)
- Transactions (fact)
- Calendar (date dimension)

## DAX Measures

Key calculated measures powering the dashboard:

```dax
// Example measure patterns used
Total Revenue = SUM(Transactions[Amount])
Active Members = CALCULATE(COUNT(Members[ID]), Members[Status] = "Active")
Profit = [Total Revenue] - [Total Expenses]
Membership % = DIVIDE([Days Active], [Total Membership Days], 0)

// BMR Calculation (Mifflin-St Jeor)
BMR Male = 10 * [Weight] + 6.25 * [Height] - 5 * [Age] + 5
BMR Female = 10 * [Weight] + 6.25 * [Height] - 5 * [Age] - 161

// TDEE = BMR * Activity Multiplier
```

## Features

**Operational Intelligence:**
- Real-time KPI monitoring
- Financial trend analysis
- Membership status tracking at tier level
- Proactive churn identification (expiring members flagged)

**Member Engagement:**
- Individual member profiles
- Goal tracking (Weight Loss, Muscle Gain, Maintenance)
- Health metric calculations
- Personalized calorie recommendations

**Design:**
- Dark theme optimized for screen display
- SATS brand integration
- Consistent navigation across pages
- Mobile-responsive card layouts

## Project Structure

```
.
├── Fitness-Performance-Data-Analysis.pbix
├── Data/
│   ├── members.csv
│   ├── trainers.csv
│   ├── transactions.csv
│   └── memberships.csv
└── README.md
```

## Technical Stack

| Component | Technology |
|-----------|------------|
| Visualization | Power BI Desktop |
| Data Modeling | Star Schema |
| Calculations | DAX |
| Data Source | Custom CSV dataset |

## Use Cases

- Daily operations monitoring for gym managers
- Member retention through early expiration alerts
- Financial performance tracking
- Personalized member health guidance
- Trainer-to-client ratio optimization

## Author

Kesara Rathnasiri
