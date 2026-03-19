# Driving Coupon Acceptance Analysis

## Introduction

This project analyzes the factors that influence whether drivers accept digital coupons delivered to their mobile devices while driving. The goal is to use visualizations and statistical analysis to distinguish between customers who accepted driving coupons versus those who declined them.

The dataset comes from the UCI Machine Learning repository and was collected via a survey on Amazon Mechanical Turk. Respondents were presented with different driving scenarios—including destination, time, weather, passenger type, and coupon details—and asked whether they would accept the coupon if they were the driver. Acceptance is coded as Y = 1 (would drive there "right away" or "later before expiration") and rejection as Y = 0 (no interest in the coupon).

The dataset includes five coupon categories:

- Coffee houses
- Restaurants (under $20)
- Carry out & take away
- Bars
- Restaurants ($20-$50)

## Understanding the Data

The dataset contains multiple attributes that can be studied upon:

- Demographics: gender, age, marital status, number of children
- Education and occupation
- Annual income
- Frequency of visits to bars, coffee houses, takeaway restaurants, and dine-in restaurants
- Driving destination (home, work, no urgent destination)
- Weather conditions (sunny, rainy, snowy)
- Temperature (30°F, 55°F, 80°F)
- Time of day (10AM, 2PM, 6PM)
- Passenger type (alone, partner, kids, friends)
- Expiration time (2 hours or 1 day)

### Data Distribution

The pie charts below visualize the distribution of coupon types and weather conditions in the dataset:

![Coupon Types Distribution](images/data_understanding.jpg)

## Data Cleanup

The raw dataset contained several data quality issues that were addressed to enable accurate analysis:

**Handling Missing Values:**

- Several columns contained null values including `car`, `Bar`, `CoffeeHouse`, `CarryAway`, `RestaurantLessThan20`, and `Restaurant20To50`
- Rather than dropping rows (which would reduce our dataset significantly), missing values were replaced with sensible defaults:
  - `car`: replaced with "do not drive"
  - Venue visit frequency columns: replaced with "never" (indicating the person doesn't visit that venue type)
- This approach preserved data integrity while maintaining a large sample size for analysis—**almost no rows were dropped**

**Data Type Corrections:**

- **Age:** Converted from categorical strings (e.g., "below21", "21-25", "50plus") to numeric values for quantitative analysis
- **Income:** Converted from income range strings (e.g., "$25000 - $37499") to numeric values representing the upper bound of each range for easier comparison and filtering
- These conversions enabled more sophisticated statistical analyses and filtering operations

The cleaned dataset is now ready for exploratory data analysis and visualization to identify patterns in coupon acceptance behavior.

## Key Findings & Conclusions

Analysis of the coupon acceptance data reveals several important patterns:

### Overall Acceptance Rates

**Across all coupon types:**

- Overall coupon acceptance rate: **41%** (41% of all delivered coupons were accepted)
- This baseline provides context for understanding which customer segments are more or less likely to engage with offers

### Acceptance by Coupon Type

Acceptance rate of coupon categories is:

- **Coffee House coupons**: ~50%
- **Carry Out & Take Away coupons**: ~49%
- **Restaurant coupons (under $20)**: ~41%
- **Bar coupons**: ~27%
- **Expensive Restaurant coupons ($20-$50)**: ~24%

### Bar Coupon Insights (Deep Dive)

Among bar coupon recipients specifically, differences emerge based on customer behavior:

**Frequency of bar visits:**

- Drivers who visit bars **more than 3 times per month**: **76% acceptance**
- Drivers who visit bars **3 times or fewer per month**: **37% acceptance**
- **Key insight**: Repeat customers are more likely to accept bar coupons

**Age matters:**

- Drivers **under age 30** who visit bars regularly: **72% acceptance**
- Drivers **over age 25** who visit bars regularly: **68% acceptance**
- Younger, frequent bar-goers are the highest-value target segment

**Passengers matter:**

- Drivers with **adult passengers** (partner or friends): Higher acceptance rates
- Drivers with **children** in the car: Lower acceptance rates

### Conclusion

1. **Target frequent customers**: Focus marketing efforts on established customers. The data shows repeat customers have 2-3x higher acceptance rates than infrequent visitors.

2. **Coffee and casual dining are strong performers**: These coupon categories naturally drive higher engagement—consider investing more resources here.

3. **Bar coupons need better positioning**: The low overall bar coupon acceptance suggests messaging or timing issues. Consider delivering bar coupons specifically to frequent bar-goers rather than the general population.

4. **Consider passenger type and time of delivery**: Adult passengers increase acceptance, while families with children do not. Coupons delivered during times when drivers are likely traveling alone or with adults may perform better.

5. **Age segmentation**: Young adults (under 30) are particularly responsive to offers for social venues like bars. This demographic should be a priority segment.
