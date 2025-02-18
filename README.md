# KMeans Applied to Business
This repository references an article that I published in Linkedin. It explains, in details, how KMeans can be applied in a business situation.
Across my LinkedIn feed, topics like Data Analysis, Data Science, and Data Engineering are almost always present. To contribute to the discussion, I decided to create an in-depth analysis of the KMeans algorithm, a Machine Learning technique, applied to a business scenario and how it can drive business development.

This article aims not only to demonstrate how to implement the algorithm but also to detail how we can apply it to a situation that closely simulates a real-world business scenario.

Database
To conduct this experiment, I used a dataset imported from Kaggle, which I adapted to better suit the analysis (the modifications made will be detailed in another article). The dataset simulates a business scenario, containing information about customers, sold products, and the sales themselves. It represents a combination of a fact table (sales) with dimension tables (products and customers), as illustrated in Figure 1.

![1736972732269](https://github.com/user-attachments/assets/e290df62-d904-4f0a-b61b-b4edb4731ee2)
# Scripting KMeans with Python
Importing and Transforming
Initially, the user must select which attributes will be analyzed and from what perspective. This will allow us to create clusters for all customers based on their characteristics. The attributes selected for the customer analysis are:

Gross Income;
Product Line;
Age.

To properly prepare the dataset for applying the algorithm, the first part of the code involves a data preprocessing for aggregating information by "client_id", as illustrated in Figure 2.
![1](https://github.com/user-attachments/assets/821487c2-7caa-491e-89a8-01ddb3cf9bf3)

# StandardScaler()
By using the StandardScaler() from the Scikit-Learn library, we are able to normalize all our data, to avoid that large scales between the values interfere with our final result. If the variables have different scales of values, we may have distortion with the final analysis.

![3](https://github.com/user-attachments/assets/f9d89734-8a08-495c-8f0c-2f0295d8a184)

It is important to say that we only need to apply that for the attributes that we initialy choosed. It is not necessary to apply that for the "client_id" column. That's why we have to filter the columns with the statment "iloc[ : , 1: ]", which select all the rows and all the columns, except the first one.

# Selecting the Number of Clusters
Another important step for the algorithm to work correctly, is selecting the right number of clusters for the analysis. We don't want to overfit it. So, the code in the Figure 4 shows us how we can do it.

![4](https://github.com/user-attachments/assets/4198b9d4-ca53-431a-bac3-0694c816df23)

Basically, the code will run the loop for 1 to 11 clusters, and by plotting the scatter graph, we can see how many clusters are necessary. The final result will be this one from the Figure 5:

![5](https://github.com/user-attachments/assets/e4f4d100-172a-42c2-8413-bff4a9066646)

What we need to see here, is decline in the graph. It is quite clear that after 3 clusters, the decline is almost the same. That's the spot we have to look at. Whenever the live gives is a continuos decline, it is when the model would overfit. So... we choose 3 clusters !!!

# Finally, Applying the KMeans !!
Now that we did all the steps do fit the database to a adequate model to apply the algorithm, we can have some action ! The code is very simple, as shown in the Figure 6:

![6](https://github.com/user-attachments/assets/a3407d76-b8b1-43d1-afb8-0a6826fcf0f2)

With that script, we now have a column within our aggregated database, that shows us which cluster each client is in. And from that, the possibilities are almost infinite (just kidding, but we have quite a few possibilities!!).

# Some Visuals to Shows Us a Little Bit About the Data
We can use some visuals that can tells us a little bit about the data. For example: if we want to check in which intervals of gross income for the business each cluster of clients is, use a BOXPLOT:

![2](https://github.com/user-attachments/assets/e4f0ef8c-33f3-4702-9f6f-c6078330c659)

Or, maybe we wanna check in a 3D visual, the how our three clusters are divided within Gross Income, Product Line and Age, use a Scatter Graph (3D):

![8](https://github.com/user-attachments/assets/4ffc412b-039c-4810-a10d-34a8306f57ca)
![3](https://github.com/user-attachments/assets/ea3d054c-5d56-45de-831b-59ae70c2776a)


# Some Insights That Are Possible Now
The analysis focuses on identifying customer profiles, such as Premium Buyers (high spenders), Economic Buyers (low spenders), Diverse Shoppers (broad product variety), and Satisfied Customers (high ratings). These profiles enable tailored strategies and insights into purchasing preferences, including popular product categories, brands, and demographic patterns.

Key areas of focus include:

Strategic Prioritization:

Retention of High-Value Customers: Foster loyalty through exclusive offers and rewards.
Growth Opportunities: Target low-spending customers with high potential through personalized campaigns.
Experience Improvement: Address dissatisfaction by linking ratings to purchasing behavior.

Operational Efficiency:

Optimize inventory for high-demand products.
Design targeted promotions for specific customer segments.
Streamline logistics to focus on valuable clusters.

Sales Planning:

Upsell or cross-sell to Economic Buyers with bundled offers or discounts.
Recommend complementary products to Diverse Shoppers.
Enhance engagement for low-rating customers through improved service or product quality.

Product Insights:

Identify top-performing brands and product lines favored by high-value customers.
Analyze seasonal or regional purchasing trends to guide inventory and marketing strategies.

Example Actions by Cluster:
High Spenders: Promote premium products and loyalty rewards.
Low Spenders: Offer price-sensitive promotions and recurring purchase incentives.
Diverse Shoppers: Provide personalized recommendations and introduce new categories or brands.

I hope that I could give a good example of how to use the KMeans, in a simulation of what could be a real business solution.







