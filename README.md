# Walmart-sales-analysis

1**. Walmart Sales Analysis:**

A. Analyze the performance of sales and revenue at the city and branch level:
Overview:Based on the accessible Walmart sales statistics, sales and revenue were analyzed
at the branch and city levels. The data was grouped by City and Branch, and the total sales for
each combination were added together to assess the performance.

**Key Insights:**
● Mandalay (Branch B) has the highest total revenue.
● Yangon (Branch A) has the second-highest revenue.
● Mandalay (Branch C) has the lowest revenue among the branches
Here is the Python code which I used to show performance of sales and revenue at city
and branch level.

**city_branch_performance = df.groupby(['City', 'Branch'])['Total Sales'].sum().reset_index()
Performance of Sales and Revenue at City and Branch Level:**

City Branch Total Sales
1 Mandalay B 37215.93
3 Naypyitaw A 35985.64
7 Yangon B 35193.51
4 Naypyitaw B 35157.75
5 Naypyitaw C 34160.14
0 Mandalay A 34130.09
6 Yangon A 33647.27
8 Yangon C 32302.43
2 Mandalay C 29794.62

**B. What is the average price of an item sold at each branch of the city:**
**Overview:** The average price of an item sold at each branch was calculated by grouping the
data by City and Branch, and then calculating the mean of the Unit Price for each group.
**Key Insights:**
● Mandalay and Naypyidaw generally have higher average unit prices compared to
Yangon.
● Branch C in each city tends to have lower average unit prices.
Here is the python code i used to get the avg price of an item sold at each branch of the
city;

**average_price_per_item = df.groupby(['City', 'Branch'])['Unit price'].mean().reset_index()
Average Price of Items Sold at Each Branch of the City:**

City Branch Unit price
0 Mandalay A 53.353866
1 Mandalay B 56.133305
2 Mandalay C 57.958316
3 Naypyitaw A 54.123182
4 Naypyitaw B 57.785688
5 Naypyitaw C 57.941009
6 Yangon A 55.639298
7 Yangon B 56.011062
8 Yangon C 52.684602

**C. Analyze the performance of sales and revenue, Month over Month across the Product
line, Gender, and Payment Method, and identify the focus areas to get better sales for
April 2019:**

**Overview: The performance of sales and revenue was analyzed month-over-month (MoM) for
various product lines, genders, and payment methods. Key trends were identified, and areas for
improvement in April 2019 were highlighted.**

**Key Insights:
● Product Line: Some product lines, like Electronics, showed a dip in sales.
● Gender: Sales from female customers were lower compared to male customers, which
could indicate a need for more targeted promotions.
● Payment Method: Credit card payments were underutilized, suggesting potential
promotional strategies to increase its usage.**

In this I checked the date format and to extract month and year and for the product,gender and
payment analysis I used the following python code for analyzing data.
**#Product analysis
product_line_analysis = df.groupby(['Month-Year', 'Product line'])['Total Sales'].sum().unstack()**

**#Gender Analysis
gender_analysis = df.groupby(['Month-Year', 'Gender'])['Total Sales'].sum().unstack()**

**# Payment Method Analysis
payment_method_analysis = df.groupby(['Month-Year', 'Payment'])['Total Sales'].sum().unstack()**

**For analyzing month over month
april_2019_product_line = product_line_analysis.loc['2019-03']
april_2019_gender = gender_analysis.loc['2019-03']
april_2019_payment_method = payment_method_analysis.loc['2019-03']**

The above is for analyzing for one month sales

For one month over month change

**monthly_sales['MoM Change (%)'] = monthly_sales['Total Sales'].pct_change() * 100**

**To visualize MOM I used matplotlib**
**import matplotlib.pyplot as plt
plt.figure(figsize=(10,6))
plt.plot(monthly_sales['Month-Year'].astype(str), monthly_sales['MoM Change (%)'], marker='o',
linestyle='-', color='b')
plt.title('Month-over-Month Sales Change') plt.xlabel('Month-Year') plt.ylabel('MoM Change (%)')
plt.xticks(rotation=45) plt.grid(True) plt.show()**


