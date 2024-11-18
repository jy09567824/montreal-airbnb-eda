# Montreal Hotel Market Analysis

## 🏨 Project Overview
This project aims to assist an international hotel chain in evaluating the potential of entering the Montreal market. Using Airbnb data and domain knowledge, we provide insights into key market factors and offer strategic recommendations.

### Objectives
- Evaluate the feasibility of entering the Montreal hotel market.
- Analyze key market indicators such as pricing, location potential, and booking behavior.
- Provide actionable strategies for maximizing profitability.

## 📂 Dataset and Variables

### Data Sources
- [Inside Airbnb: Montreal Data](http://insideairbnb.com/montreal/)
- Kaggle References:
  - [NYC Airbnb Open Data](https://www.kaggle.com/datasets/dgomonov/new-york-city-airbnb-open-data)
  - [Boston Airbnb Open Data](https://www.kaggle.com/datasets/airbnb/boston)

### Datasets
1. **`listings.csv`**
   - Contains summary information about Airbnb listings in Montreal.
   - **Key Variables**:
     - `id`: Unique identifier for the listing.
     - `name`: Name of the listing.
     - `neighbourhood`: Location of the listing.
     - `room_type`: Type of accommodation (e.g., Private room, Entire place).
     - `price`: Daily price in local currency.
     - `availability_365`: Number of available days in the next 365 days.
     - (Full details in the [Data Dictionary](#data-dictionary)).

2. **`calendar.csv`**
   - Daily records of listing availability and pricing.
   - **Key Variables**:
     - `date`: Date in the calendar year.
     - `available`: Booking availability (1 for available, 0 for unavailable).
     - `price`: Daily price listed.
     - (Full details in the [Data Dictionary](#data-dictionary)).

---

## 🔄 Project Workflow

### 1. Problem Definition
- **Key Questions**:
  - Which neighborhood has the highest potential for success?
  - How should we price our services to stay competitive?
  - Which factors influence booking rates?
  - How can we maximize profit?

### 2. Data Preparation
#### Cleaning Process
- **`listings.csv`**:
  - Remove duplicates and irrelevant columns (e.g., `neighbourhood_group`, `last_review`).
  - Handle missing values and outliers.
  - Example:
    ```python
    df['reviews_per_month'].fillna(0, inplace=True)
    ```
- **`calendar.csv`**:
  - Convert data types (e.g., `price` to numeric, `available` to binary).
  - Remove unnecessary columns (`minimum_nights`, `maximum_nights`).

### 3. Exploratory Data Analysis (EDA)
#### Key Findings
- **Revenue by Neighborhood**:
  - Top neighborhoods: `Ville-Marie`, `Le Plateau-Mont-Royal`.
  - Visualization:
    ```python
    sns.barplot(data=revenue_by_neighbourhood, x='neighbourhood', y='revenue')
    plt.title('Total Revenue by Neighbourhood')
    ```
- **Hotel Pricing in Ville-Marie**:
  - Average price: **$278**.
  - Insight: Pricing strategy should reflect high-quality services to justify premium rates.

#### Booking Rate Analysis
- Factors such as license, reviews, and room type show weak correlation with booking rates.
- Key metric: `(365 - availability_365) / 365`.

### 4. Profit Maximization Strategy
- **Time Series Analysis**:
  - Availability rates decrease closer to the booking date.
  - Peak season: **June to August** (validated with Google Trends).
- **Recommendation**:
  - Focus on providing competitive pricing and high-quality services during peak seasons.

---

## 🗂 Data Dictionary

### `listings.csv`
| Variable                  | Description                                               |
|---------------------------|-----------------------------------------------------------|
| `id`                      | Airbnb's unique identifier for the listing               |
| `name`                    | Name of the listing                                       |
| `neighbourhood`           | Location of the listing                                   |
| `room_type`               | Type of accommodation                                    |
| `price`                   | Daily price in local currency                            |
| `availability_365`        | Availability in the next 365 days                        |

### `calendar.csv`
| Variable                  | Description                                               |
|---------------------------|-----------------------------------------------------------|
| `listing_id`              | Unique identifier for the listing                         |
| `date`                    | Date in the calendar                                      |
| `available`               | Booking availability (1 for available, 0 for unavailable)|
| `price`                   | Daily price listed                                        |

---

## 📊 Visualizations
### Example
- **Total Revenue by Neighborhood**:
  ![Revenue Visualization](#)

- **Availability Rate Time Series**:
  ![Time Series Analysis](#)

---

## ✨ Key Insights and Recommendations
1. **Location Selection**: Invest in the Ville-Marie neighborhood for maximum profitability.
2. **Pricing Strategy**: Set prices around $278 with a focus on service quality to remain competitive.
3. **Seasonal Strategy**: Optimize bookings during peak travel seasons (June to August).

For more details, check the analysis scripts in the repository.