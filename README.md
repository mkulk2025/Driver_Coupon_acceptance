# Driver_Coupon_acceptance
This is a repository evaluating if the drivers will accept a restaurant coupon 
**Section: 1**
**Understanding the dataset & approach to resolve the problem **

df.count()/ df.info()/df.shape
The dataset has 26 columns. 20 of those has 12684 rows of information. Five( Bar ,CoffeeHouse, CarryAway, RestaurantLessThan20, Restaurant20To50 ) of them has app 12500 rows of information.  And car column has only 108 entries, meaning the column is missing information. 

The dataset columns can be clubbed together in four categories wrt to "Y"

1. Driving_attributes :   destination , passanger, weather,temperature, time, toCoupon_GEQ5min, toCoupon_GEQ15min,toCoupon_GEQ25min,direction_same,direction_opp

2. Coupon_Attributes : coupon, expiration 

3. User_Attributes : gender,age,maritalStatus,has_children,education,occupation,income,car

4. Frequency_Attributes :  Bar,CoffeeHouse, CarryAway, RestaurantLessThan20, Restaurant20To50

 
** Find null values**  
null_counts = df.isna().sum() shows the null values. It seems like Car column is less significant due to maximum number of missing data 

car                     12576
Bar                       107
CoffeeHouse               217
CarryAway                 151
RestaurantLessThan20      130
Restaurant20To50          189


**Checking for the duplicates**

Removing the duplicates using df_no_duplicates = df.drop_duplicates() method indicates bring he dataset count to [12610 rows x 26 columns] compared to [12684 rows x 26 columns] . 

After removing the duplicates, the % of coupon acceptance becomes = 56.75654242664552 

Leaving the column alone, if we remove the null values from rest of the five columns( Bar,CoffeeHouse, CarryAway, RestaurantLessThan20, Restaurant20To50), the acceptance % becomes 56.8418.


**Data Visualization:**

1. Plot#1:  The date visualization/ Bar plot shows that the Coffee House coupon was offered most of the time. It was followed by Restaurant<20, carry out & Take Away, Bar and lastly Restaurant (20-50)
2. Plot#2: The plot#2 show the most accepted coupon. The plot shows Coffee House coupon was accepted most of the time. It was closely followed by Restaurant<20, carry out & Take Away, Bar and lastly Restaurant (20-50)
 
**Investgating Bar coupons:**

#1 The df_bar is a new dataset created after removing the duplicates and the null values. The shape of df_bar is 1906 * 26 

#2 Based on the shape, and after removing the duplicates and the null values, 41.19 % of the coupons were accepted. 

#3 Based on the df_bar.info(), less than three includes never (788), less1(546), and "1~3"(379) counts.  For this group the acceptance ratio is - 37.25
  Next- calculate the acceptance for category who went more than 3 which include 4~8 (147) and gt8(46)  For this group the acceptance ratio comes out to be - 76.17
  Conclusion:  People who went to bar 4plus time has acceptance 2.04 times compared to who went to the bar less than 3 times. This means people who go to the bar 4+ times are like to accept the coupon often. 

 
#4 Assumption: For this question the bar number frequency is not defined. So assuming it is a month. meaning, ['never' 'less1' '1~3' 'gt8' nan '4~8']  less than 1 month, 1~3 month etc etc. 
 Based on this assumption, the acceptance rate for more than one month and age > 25 is 68.98 
 The acceptance rate for all other category is 27.64. 

#5:  
The acceptance rate for the drivers going more than a month with a passenger that is not a kid and occupation other than farming, fishing and forestry = 71.43  While as the acceptance rate for all other remaining is 41.18 

#6 The acceptance rate for the drivers with the given three conditions )go to bars more than once a month, had passengers that were not a kid, and were not widowed OR
go to bars more than once a month and are under the age of 30 OR, go to cheap restaurants more than 4 times a month and income is less than 50K.) is 56.67 
While as for rest of the remaining group is 41.19 
This shows that  drivers who meet any of the three specified conditions have a significantly higher acceptance rate than drivers who do not meet any of those conditions.
 
#7 **Conclusion: **

Overall, drivers accept bar coupons less than half the time (41.2%). However, acceptance rates significantly increase with bar visitation frequency and specific demographic factors. Drivers who visit bars more than three times a month show a dramatically higher acceptance rate of 76.2%, more than double the rate of less frequent visitors (37.3%). Similarly, drivers over 25 who visit bars more than once a month exhibit a 68.3% acceptance rate, and those meeting specific criteria—frequent bar visits, no child passengers, and non-agricultural occupations—show a 71.4% acceptance rate. These findings suggest that targeting frequent bar-goers and those with certain demographic profiles can significantly increase bar coupon redemption.

****Independent Investigation **
I investigated the Coffee House acceptance with age below21 and others. 

The histogram show that the coffee coupons for were acceptance was randomly distributed across various income groups. 
The acceptance rate for the drivers who go the coffeeshop more than once and are below21 is (65.34) almost twice to the remaining/ other drivers (33.73). 
 

