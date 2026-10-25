Website-Visitor-Behavior-Analysis

This project simulates, cleans, analyzes, and visualizes synthetic web traffic and e-commerce session data. It provides a complete end-to-end data pipeline from raw dataset generation to key business takeaways.

Table of Contents

1. [Project Overview](#project-overview)
2. [Data Schema & Features](#data-schema--features)
3. [Data Pipeline Stages](#data-pipeline-stages)
4. [Key Insights & Findings](#key-insights--findings)
5. [Technologies Used](#technologies-used)

Project Overview

The main goal of this project is to analyze user behavior on a website. It tracks user sessions across various acquisition sources, device categories, landing pages, and geographic locations. The analysis focuses on understanding site engagement (session duration, page views, bounce rates) and transaction outcomes (revenue, conversion rates).

Data Schema & Features

The dataset consists of 12,000 unique sessions with the following primary features:

| Feature | Type | Description |
| :--- | :--- | :--- |
| `session_id` | String | Unique identifier for each web session. |
| `date` | Timestamp | Timestamp of the session. |
| `source` | Categorical | Traffic acquisition channel (`Organic`, `Direct`, `Social`, `Email`, `Referral`, `Paid`). |
| `device` | Categorical | Device type used (`Desktop`, `Mobile`, `Tablet`). |
| `browser` | Categorical | Browser type (`Chrome`, `Safari`, `Firefox`, `Edge`). |
| `country` | Categorical | Demographics/Origin country. |
| `page` | String | Landing page path (`/home`, `/products`, `/blog`, `/pricing`, `/about`, `/contact`). |
| `pages` | Integer | Number of pageviews during the session. |
| `seconds` | Numeric | Total session duration in seconds. |
| `clicks` | Integer | Interaction count (clicks). |
| `bounce` | Binary | Binary flag (`1` if the user bounced immediately, `0` otherwise). |
| `revenue` | Numeric | Transaction revenue generated during the session. |

Data Pipeline Stages

1. Environment Setup & Initialization
- Configures the visualization environment using `matplotlib` and `seaborn`.
- Sets a global random seed (`42`) for reproducibility.

2. Dataset Synthesis
- Simulates realistic web traffic patterns (e.g., lower traffic on weekends, specific peak hours, log-normal session durations, and correlation-driven conversions).
- Artificially injects messy data (null values in session durations and browsers, negative values in revenue, and duplicated entries) to replicate real-world data cleaning scenarios.

3. Data Auditing & Exploration
- Audits missing values, duplicates, and general data distribution metrics to map out the required transformations.

4. Data Cleansing & Feature Engineering
- Removes duplicate records.
- Standardizes types and handles abnormal outliers (such as negative revenue or excessive session lengths).
- Imputes missing browser types with the mode, and missing session durations with the median grouped by device.
- Extracts temporal dimensions (hour of day, day of week `dow`) and derives a conversion flag (`conv`).

5. Aggregation & Visualization
- Examines cohort metrics across devices, traffic channels, and time.
- Visualizes traffic trends, session distributions, and engagement scatter plots.

Key Insights & Findings

- **Top Acquisition Device:** Desktop represents the primary driver of site visits.
- **High-Value Channel:** Email stands out as the highest-performing channel for average revenue per session.
- **Peak Traffic Hours:** Activity peaks around 14:00 (2 PM).
- **Bounce & Conversion Metrics:** Overall conversion rate is stabilized at 5.12%, with a baseline bounce rate of 35.4%.

Technologies Used

- **Language:** Python 3
- **Libraries:** `pandas`, `numpy`, `matplotlib`, `seaborn`
