# Vehicle Sales Analysis

## Table of Contents

- [Project Overview](#project-overview)
- [Tools and Techniques](#tools-and-techniques)
- [Key Accomplishments](#key-accomplishments)
- [Data Cleaning and Preparation](#data-cleaning-and-preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Inferences and Conclusions](#inferences-and-conclusions)
- [Recommedations](#recommedations)
  
## *Project Overview*
Analyzed a comprehensive vehicle sales dataset, exploring relationships between attributes (condition, age, color, etc.) and prices. Used Python, Pandas, and visualization to uncover insights like condition impact on pricing, geographic price trends, and top-selling models. Showcases data analysis and problem-solving skills. The dataset has 16 rows and 558837 columns.

## *Tools and Techniques*:
- Python for data cleaning, analysis, visualization, and statistical modeling
- Pandas for data manipulation and analysis
- Matplotlib and Seaborn for data visualization
- Conducted exploratory data analysis and derived insights
- Kaggle for the dataset source. (car_prices.csv) [Download Here](https://www.kaggle.com/datasets/syedanwarafridi/vehicle-sales-data)

## *Key Accomplishments*:
- Analyzed the impact of vehicle condition on selling prices, finding that condition ratings were weakly associated with significantly higher selling prices.
- Investigated the relationship between vehicle age, condition, and selling prices, uncovering trends and patterns.
- Identified the most common vehicle exterior and interior colors in the dataset.
- Compared the Manheim Market Report (MMR) values to the actual selling prices, providing insights into the accuracy of the market value estimates.
- Performed price-vs-mileage analysis to understand the depreciation curve of vehicles.
- Identified the states with the highest and lowest average selling prices, revealing geographic trends in the vehicle market.
- Determined the vehicle model with the highest average selling price, highlighting the most valuable assets in the dataset.

## *Data cleaning and Preparation*
- Removed nan/ empty values
- Handled missing values
- Removed Duplicates
- Removed trailing and leading whitespaces
- Removed outliers and anomalies

## *Exploratory Data Analysis*
- What is the distribution of vehicle ages in the dataset?
- What is the distribution of selling prices by vehicle interior and exterior color
- Generated comprehensive descriptive statistics for the vehicle dataset like mean etc. for key numeric attributes. 
- Correlation on numeric columns.
- Selling price distribution against states where the vehicle was registered
- Yearly distribution of selling price

## *Data Analysis*
### Some interesting questions:
1. How does vehicle condition impact the selling price?
``` python
# Define the bins and labels
bins = [0, 10, 20, 30, 40, 50]
labels = ['poor', 'bad', 'average', 'good', 'excellent']
# Create a new column for the condition categories
vehicle_df['condition_category'] = pd.cut(vehicle_df['condition'], bins=bins, labels=labels, right=False)
# Get average selling price for each condition category
avg_sellingprice_by_condition = vehicle_df.groupby('condition_category')['sellingprice'].mean()
#Visualisation
sns.barplot(x=avg_sellingprice_by_condition.index, y=avg_sellingprice_by_condition.values)
plt.xlabel('Condition Category')
plt.ylabel('Average Selling Price')
plt.title('Average Selling Price by Vehicle Condition')
plt.show()
```
2. How does the market value estimate (MMR) compare to actual selling prices?
``` python
plt.scatter(vehicle_df['mmr'], vehicle_df['sellingprice'])
plt.xlabel('MMR')
plt.ylabel('Selling Price')
plt.title('Comparison of MMR and Selling Prices')
plt.show()
```
3. Price vs Milleage Analysis?
``` python
sns.scatterplot(x = vehicle_df.odometer , y =vehicle_df.sellingprice, alpha= 0.5);
sns.regplot(x='odometer', y='sellingprice', data=vehicle_df, scatter=False, color='red')
```
## *Inferences and Conclusions*
1. High mileage (odometer) tends to negatively impact both the market value and selling price.
2. MMR, as a market valuation metric, aligns very closely with actual selling prices, showing that it is a reliable indicator in this dataset.
3.There correlation between price and condition is weak as vehicles in the poor condition category has a higher mean selling price than that of the average conditon category
4. Massachusetts is the state with the lowest average selling price while Tennessee is the state with the highest average selling price
5. The highest selling price is 28,212.92 for the 6-10 vehicle age category in the "excellent condition".
6. The lowest selling price is 1,709.14 for the 20+ vehicle age category in the "poor" condition.
7. Though black occurs the most in the data frame, Charcoal is the color with the highest mean average selling price of 16208.94
8. The vehicle of 458 Italia has the highest average selling price of 183000

## Recommedations
1. Focus on Mileage Management: Given the negative correlation between high mileage and both market value and selling price, dealers should prioritize sourcing and maintaining vehicles with lower odometer readings. This may involve targeted procurement strategies, as well as effective maintenance and repair programs to preserve low-mileage vehicles.
2. Leverage Manheim Market Report: The close alignment between MMR and actual selling prices confirms that this industry benchmark is a reliable indicator for vehicle valuation. Dealers should continue to use the MMR as a key reference point when pricing their inventory to ensure they remain competitive and in tune with market dynamics.
3. Reassess Condition-based Pricing: The weak correlation between price and condition, along with the finding that "poor" condition vehicles have a higher mean selling price than "average" condition, suggests that the relationship between condition and pricing may be more complex. Dealers should further investigate this dynamic and potentially adjust their pricing models to better account for nuances in vehicle condition.
4. Explore Geographic Pricing Strategies: The significant difference in average selling prices between Massachusetts and Tennessee indicates the presence of regional market disparities. Dealers could benefit from developing targeted geographic pricing and sourcing strategies to capitalize on these regional variations, potentially by procuring inventory from lower-priced markets and selling in higher-priced ones.
5. Prioritize Inventory Management for High-Value Segments: The findings related to the highest and lowest selling prices based on age and condition categories provide valuable insights for inventory management. Dealers should focus on sourcing and maintaining vehicles in the 6-10 age range and "excellent" condition, as they command the highest prices. Conversely, they should exercise caution with older, poorly-conditioned vehicles, as they tend to fetch significantly lower prices.
6. Optimize Pricing for Specific Color Preferences: The analysis revealing Charcoal as the color with the highest mean selling price, despite black being the most common, suggests that certain color preferences may be more valuable to customers. Dealers could leverage this insight to strategically price their inventory and potentially adjust their procurement strategies to cater to these color-based market dynamics.
7. Highlight Unique, High-End Vehicles: The exceptionally high average selling price for the 458 Italia model indicates that dealers can potentially command premium prices for unique, high-end vehicles. Highlighting and effectively marketing these rare and desirable vehicles could be a valuable strategy for maximizing profitability.

## *Limitations*
- Some values under the color and interior columns were "-" and they had to be removed
- I removed duplicate values and rows which had empty cells and also outliers
- I had to create additional columns like vehicle age, vehicle age category and condition category
