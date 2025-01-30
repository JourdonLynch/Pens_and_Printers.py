# Pens_and_Printers.py

# Introduction
The Pens and Printers company founded in 1984 provides high-quality office products to large organizations. While they don’t directly produce these products, customers trust them to provide quality products. Over time the way consumers buy products changes and to maintain relevance businesses must adapt their sales methods. The pens and Printers company is launching a new product line and are interested in knowing how different sales methods resonate with their customers.

The purpose of this report is to outline the data validation and cleaning process, conduct exploratory analysis on sales methods and customers, define a metric to track performance, and provide a recommendation based on findings.

# Data Validation and Cleaning

• The Pandas, matplotlib.pyplot, and seaborn libraries were imported to conduct the analysis.

• The CSV file was loaded into a pandas dataframe using pd.read_csv() and information on the dataframe was gathered using .head(), .info() and .describe().

• The **Week** column of the int64 data type contained values from 1-6. No null values were observed. No changes were made to this column.

• The **sales_method** column of the object data type contained 5 distinct values (Email, Call, Email + Call, em + call, email) when only 3 were supposed to be observed. Two aditional values were caused by      incorrect capitalization and typos. These were replaced with correct spellings using .replace() so that the column only contained the following unique values: Email, Call, and Email + Call. 

• The **customer_id** column of the object data type contained a combination of letters, numbers and characters representing customers and had no null values. No changes were made to this column.

• The **nb_sold** column of the int64 data type and contained no null or negative values. No changes were made to this column.

• The **years_as_customer** column of the int64 data type contained values between 0 and 63 and no null values. The company was established in 1984; therefore, the maximum value of this column should be 41. Two     fields were found to have values of 47 and 63. These values were assumed to be errors in data entry and replaced with the maximum realistic value of 41.

• The **revenue** column of the float64 data type had 1,074 null values. Instead of removing all rows with missing revenue values, the null values were replaced with the mean revenue of each sales method.

• The **nb_site_visits** column of the int64 data type contained the number of website visits for each customer and had no null values. No changes were made to this column.

• The **state** column of the object data type contained the state of each customer and no null values. As there are only 50 states the column was checked for unique values and returned 50. No chages were made to   this column.

• The dataframe was checked for duplicate rows, and none were found. The final dataframe contained 15000 rows, 8 columns, and 0 null values.

# Exploratory Analysis

   Customers for each sales method approach were found by grouping the customer_id column by sales method using the groupby() function and then counting each group of customers using the count() function. Email was the largest approach, with 7466 customers, followed by call with 4962 and email + call with 2572. 

Figure 1

<img width="591" alt="Screenshot 2025-01-24 at 2 31 16 PM" src="https://github.com/user-attachments/assets/7b1bc3cc-d9e3-4233-b112-72382729f75e" />

#  


    
 Overall, the revenue per customer recorded in dollars had a mean of 95.85  and a standard deviation of 47.96. In addition to this, the revenue had a median value of 90.95 with an interquartile range of 55.10. 

figure 2 
 
<img width="489" alt="Screenshot 2025-01-24 at 10 48 40 PM" src="https://github.com/user-attachments/assets/ca92cadf-7e8f-42f3-8be1-30ec745845f5" />

   Revenue was then grouped by sales method and the mean, standard deviation, median, and interquartile range were calculated. The call method reported a mean of 47.60, a standard deviation of  8.45, a median of 47.60, and an interquartile range of 10.96. The email method reported a mean of 97.13, a standard deviation of 10.79, a median of 96.84, and an interquartile range of 16.07. The email + call method reported a mean of 183.65, a standard deviation of 27.04, a median of 183.65, and an interquartile range of 13.10. This was the highest among all sales strategies.

#  

figure 3

<img width="487" alt="Screenshot 2025-01-25 at 1 55 23 PM" src="https://github.com/user-attachments/assets/9ce747f8-f42d-462c-9c21-3325b60832a4" />

#  

 Over the six week period the email method saw a sharp decline in total revenue, dropping from a weekly revenue of 248,122.68 down to 25,260.79. The call method saw fluctuations in its revenue, starting at a weekly revenue of 27,015.93 and ending at 29252.46. The email + call method experienced a sharp increase in weekly revenue recorded in dollars, starting at 20,007.40 and ending at 128,598.94.

Figure 4

<img width="596" alt="Screenshot 2025-01-24 at 3 31 05 PM" src="https://github.com/user-attachments/assets/57999cef-7744-4373-8c04-29f20cb97abf" />

#  



  Over the six-week period, revenue per customer increased for all three sales methods; however, the email + call sales saw sharper increases, especially in weeks 2, 4, and 6.

Figure 5

<img width="617" alt="Screenshot 2025-01-25 at 2 16 57 PM" src="https://github.com/user-attachments/assets/89139d14-f7ed-47c7-b3fa-38673f1894d6" />


# Customer Demographics

   In order to gain a better understanding of the customer base, customers were grouped into histogram bins with a width of 2 based on their years as a customer. This resulted in a unimodal right-skewed histogram with the largest group of customers in the 0-2 year range. The minimum and maximum years as a customer were 0 and 41, respectively. 

Figure 6 

<img width="574" alt="Screenshot 2025-01-24 at 8 22 14 PM" src="https://github.com/user-attachments/assets/bb983ca2-1767-4ea1-b903-8098c50edb8b" />

   The top 5 states based on the number of customers were California, Texas, New York, Florida and Illinois respectively. These states made up 36.9% of the total customers with California being the only state to comprise more than 10% of customers.

#  

Figure 7 

<img width="622" alt="Screenshot 2025-01-24 at 8 23 02 PM" src="https://github.com/user-attachments/assets/5dfa95ad-7232-4d2c-859b-f40db105c344" />

# Metric:

   To track the effectiveness of sales methods, the revenue week-over-week metric was chosen. Revenue was grouped by weeks since product launch and sales method before summing the total for each week using the sum() function. After this, the unstack() function was used to pivot the data frame based on the sales_method column and return a dataframe with sales method as columns and weeks since launch as rows. The pct_change() function was then used to return the percent change of revenue week-over-week as a decimal. A consistently positive week-over-week metric, along with tracking total revenue over each week during the test period, will indicate which sales method is most effective. Results for the most recent week can be used as a basis moving forward. In week six email, call, and email + call recorded revenue week-over-week values of -68.50%, -47.08% and -12.63% respectively. 

# Recommendations: 

   To support the goal of selling new products effectively the right sales method must be prioritized. Based on the average revenue per customer, revenue over time, and revenue week-over-week(RWOW) metric the email + call method should be selected as it experienced the greatest growth and had a RWOW that was the most consistently positive and therefore the greatest long-term potential.
