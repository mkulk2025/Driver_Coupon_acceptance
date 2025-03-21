# Driver Coupon Acceptance

This repository evaluates whether drivers accept restaurant coupons.

**Section 1: Dataset Understanding and Problem Approach**

* **Initial Data Exploration:**
    * `df.count()`, `df.info()`, and `df.shape` were used to examine the dataset.
    * The dataset contains 26 columns and 12,684 rows.
    * Five columns (Bar, CoffeeHouse, CarryAway, RestaurantLessThan20, and Restaurant20To50) have approximately 12,500 rows, indicating some missing data.
    * The "car" column has only 108 entries, suggesting a significant amount of missing information.
* **Column Categorization:**
    * The columns were categorized into four groups based on their relationship to coupon acceptance ("Y"):
        1.  **Driving Attributes:** destination, passenger, weather, temperature, time, toCoupon_GEQ5min, toCoupon_GEQ15min, toCoupon_GEQ25min, direction_same, direction_opp.
        2.  **Coupon Attributes:** coupon, expiration.
        3.  **User Attributes:** gender, age, maritalStatus, has_children, education, occupation, income, car.
        4.  **Frequency Attributes:** Bar, CoffeeHouse, CarryAway, RestaurantLessThan20, Restaurant20To50.
* **Null Value Analysis:**
    * `null_counts = df.isna().sum()` was used to identify null values.
    * The "car" column has the most null values (12,576), indicating it may be less significant.
    * Other columns with null values:
        * Bar: 107
        * CoffeeHouse: 217
        * CarryAway: 151
        * RestaurantLessThan20: 130
        * Restaurant20To50: 189
* **Duplicate Removal:**
    * `df_no_duplicates = df.drop_duplicates()` was used to remove duplicate rows.
    * The dataset's dimensions changed from [12,684 rows x 26 columns] to [12,610 rows x 26 columns].
    * After removing duplicates, the overall coupon acceptance rate is 56.76%.
    * Removing null values from the frequency attributes, and then calculating the acceptance rate results in an acceptance rate of 56.84%.
* **Data Visualization:**
    1.  **Plot 1 (Coupon Offer Frequency):** A bar plot shows the frequency of coupon offers, with Coffee House coupons being offered most frequently, followed by Restaurant<20, CarryAway, Bar, and Restaurant20To50.
    2.  **Plot 2 (Coupon Acceptance Frequency):** A bar plot shows the frequency of coupon acceptance, mirroring the offer frequency, with Coffee House coupons being accepted most often, followed by Restaurant<20, CarryAway, Bar, and Restaurant20To50.

**Investigating Bar Coupons:**

1.  **Dataset Creation:** `df_bar` was created by removing duplicates and null values from the original dataset. The resulting dataset has dimensions 1906 x 26.
2.  **Overall Acceptance Rate:** After removing duplicates and null values, the overall bar coupon acceptance rate is 41.19%.
3.  **Frequency-Based Analysis:**
    * Drivers who visit bars three or fewer times a month ("never," "less1," "1~3") have an acceptance rate of 37.25%.
    * Drivers who visit bars more than three times a month ("4~8," "gt8") have an acceptance rate of 76.17%.
    * Conclusion: Drivers who visit bars more than three times a month are approximately 2.04 times more likely to accept bar coupons than those who visit less frequently.
4.  **Age and Frequency Analysis:**
    * Assuming bar visit frequency is monthly, drivers over 25 who visit bars more than once a month have an acceptance rate of 68.98%.
    * The acceptance rate for all other drivers is 27.64%.
5.  **Passenger and Occupation Analysis:**
    * Drivers who visit bars more than once a month, have non-child passengers, and have occupations other than farming, fishing, and forestry have an acceptance rate of 71.43%.
    * The acceptance rate for all other drivers is 41.18%.
6.  **Combined Condition Analysis:**
    * Drivers who meet any of the following conditions have an acceptance rate of 56.67%:
        * Visit bars more than once a month and have non-child passengers and are not widowed.
        * Visit bars more than once a month and are under 30.
        * Visit cheap restaurants more than four times a month and have an income less than $50,000.
    * The acceptance rate for all other drivers is 41.19%.
    * This shows a significantly higher acceptance rate for those that meet one of the three conditions.
7.  **Conclusion:**
    * Overall, the bar coupon acceptance rate is 41.2%.
    * Acceptance rates increase significantly with bar visit frequency and specific demographic factors.
    * Frequent bar-goers (more than three times a month) have a 76.2% acceptance rate, more than double the rate of less frequent visitors (37.3%).
    * Drivers over 25 who visit bars more than once a month have a 68.3% acceptance rate.
    * Drivers meeting specific criteria (frequent bar visits, no child passengers, and non-agricultural occupations) have a 71.4% acceptance rate.
    * Targeting frequent bar-goers and those with specific demographic profiles can significantly increase bar coupon redemption.

**Independent Investigation: Coffee House Coupons**

* A histogram shows the distribution of coffee coupon acceptance across various income groups.
* Drivers who go to the coffee shop more than once a month and are under 21 have an acceptance rate of 65.34%, almost twice the rate of other drivers (33.73%).
