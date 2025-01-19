# Pens_and_Printers.py

# Introduction
The Pens and Printers provides was founded in 1984 and provides high-quality office products to large organizations. While they don’t directly produce these products, customers trust them to provide quality products. Over time the way consumers buy products changes and to maintain relevance businesses must adapt their sales methods. The pens and Printers company is launching a new product line and are interested in knowing how different sales methods resonate with their customers.


# Problem statement
Launching a new product line is expensive and Pens and Printers need to ensure that they are using the most effective technique to sell their new product line.


# Data Validation
After loading the csv file into a pandas dataframe using pd.read_csv(), the dtypes attribute was used to return the data type of each column. The first 10 rows of the dataframe were taken using the head() function.  Columns week, nb_sold, years_as_customer, and nb_site_visits remained as the int64 datatype, and revenue was left as the float64 datatype. The sales_method, customer_id, and state columns were converted from object datatype to string datatype using the astype() function.


# Data Cleaning
The sales method column appeared to contain improperly formatted strings, so the value_counts() function was used to group entries, allowing errors to be identified. The replace() function was then used on the dataframe to replace typos with correct spellings. It was found that the revenue column contained a number of null values for observations where there were products sold. This was found using the isnull() function in conjunction with the sum() function to return 1,074 nulls. The min() function was applied to the nb_sold column, which returned a positive number to ensure that in every observation there was a product sold. Observations with products sold but no revenue were removed using the pd.dropna() function. The decision to do this was based on the assumption that if there were products sold, there had to be resulting revenue.

# Exploratory Analysis
Customers for each sales method approach were found by grouping the customer_id column by sales method using the groupby() function and then counting each group of customers using the count() function. Email was the largest approach, with 6922 customers, followed by call with 4781 and email and call with 2223. 

Figure 1

<img width="490" alt="Screenshot 2025-01-17 at 11 29 37 PM" src="https://github.com/user-attachments/assets/a2f027ad-2077-41f3-a863-4b7d9d3fc8a1" />


In order to gain a better understanding of the customer base, customers were grouped into histogram bins with a width of 4 based on their years as a customer using sns.histplot(). This resulted in a unimodal right-skewed histogram with the largest group of customers in the 0-4 range. The minimum and maximum years as a customer were 0 and 63, respectively. While not pictured, it is interesting to note that California, Texas, and New York account for 36.8% of customers. This was found by grouping customer ids using the groupby() function in conjunction with the count() and sort_values functions.

figure 2 

<img width="637" alt="Screenshot 2025-01-12 at 2 12 05 PM" src="https://github.com/user-attachments/assets/a830e1dc-6ab2-4b80-b237-a5dbd99d566b" />


Overall, the revenue per customer recorded in dollars had a mean of 93.93 and a standard deviation of 47.44. In addition to this, the revenue had a median value of 89.50 with an interquartile range of 54.86. This was found by applying the mean(), std(), median(), and quantile() functions to the revenue column.

figure 3

<img width="499" alt="Screenshot 2025-01-18 at 4 15 09 PM" src="https://github.com/user-attachments/assets/8bf781d5-afb7-4603-9f72-f026a0b4f685" />


Revenue was then separated by sales method using .groupby() and the mean, standard deviation, median, and interquartile range were calculated using the methods stated previously. The email and call method reported a mean of 183.65, a standard deviation of 29.08, a median of 184.74, and an interquartile range of 35.34. This was the highest among all sales strategies. The call method reported a mean of 47.60, a standard deviation of 8.61, a median of 49.07, and an interquartile range of 11.21. The email method reported a mean of 97.13, a standard deviation of 11.21, a median of 95.58, and an interquartile range of 17.29.

figure 4 

<img width="493" alt="Screenshot 2025-01-12 at 2 38 00 PM" src="https://github.com/user-attachments/assets/ebf20833-3556-4cb3-bc4c-7cb53232037f" />


To understand how different sales methods performed better at different points during the product launch revenue by sales method was further broken down by week. The median sales revenue per customer and minimum interquartile range value per customer increased for all sales methods increased throughout the period. However the email + call sales method saw sharper increases throughout the period as time went on.

figure 5

<img width="615" alt="Screenshot 2025-01-18 at 4 47 15 PM" src="https://github.com/user-attachments/assets/bb5a11dd-be41-4d8c-9ed3-b5f74df894a1" />


Over the six week period the email and call method experienced a sharp increase in weekly revenue recorded in dollars, starting at 16,885 and ending at 111,152. The call method saw fluctuations in its revenue, starting at a weekly revenue of 26,159 and ending at 28,253. Lastly the email method saw a sharp decline in total revenue, dropping from a weekly revenue of 230,000 down to 23,706.

figure 5

<img width="691" alt="Screenshot 2025-01-12 at 4 06 23 PM" src="https://github.com/user-attachments/assets/45322356-135e-4a05-a4ae-693eaa59c2e7" />


To track the effectiveness of sales methods, the revenue week-over-week metric was chosen. Revenue was grouped by weeks since product launch and sales method before summing the total for each week using the sum() function. After this, the unstack() function was used to pivot the data frame based on the sales_method column and return a dataframe with sales method as columns and weeks since launch as rows. The pct_change() function was then used to return the percent change of revenue week-over-week as a decimal. A consistently positive week-over-week metric, along with tracking total revenue over each week during the test period, will indicate which sales method is most effective. Results for the most recent week can be used as a basis moving forward. In week six email and call, call, and email recorded revenue week-over-week values of -12.35%, -47.21% and -68.12%% respectively.



# Recommendations
To support the goal of selling new products effectively the right sales method must be prioritized. Based on the revenue week-over-week metric, revenue spread across time, and the revenue spread across sales methods the email and call sales method is the most effecient at generating revenue making it the best method to sell the new product line and recoup the company's capital investment. It provides the highest average sales price per customer. While it required more effort than the email method alone, it required less total time investment than the call method. The email sales method showed greater revenue over the short term, however this was due to the method being used more frequently. It is recommended that the email and call method is used to  market the new product lines to customers.



