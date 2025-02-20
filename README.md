# KMeans Applied to Business
This repository references an article that I published in Linkedin. It explains, in details, how KMeans can be applied in a business situation.
Across my LinkedIn feed, topics like Data Analysis, Data Science, and Data Engineering are almost always present. To contribute to the discussion, I decided to create an in-depth analysis of the KMeans algorithm, a Machine Learning technique, applied to a business scenario and how it can drive business development.

This article aims not only to demonstrate how to implement the algorithm but also to detail how we can apply it to a situation that closely simulates a real-world business scenario.

To conduct this experiment, I used a dataset imported from Kaggle, which I adapted to better suit the analysis. The dataset simulates a business scenario, containing information about customers, sold products and the sales. It represents a combination of a fact table (sales) with dimension tables (products and customers), as illustrated in Figure 1.

![1736972732269](https://github.com/user-attachments/assets/e290df62-d904-4f0a-b61b-b4edb4731ee2)
# Scripting KMeans with Python
Initially, the user must select which attributes will be analyzed and from what perspective. This will allow us to create clusters for all customers based on their characteristics. The attributes selected for the customer analysis are:

Gross Income;
Product Line;
Quantity;
Age.

I chose these features to evaluate things like: customer segmentation, product performance by age and quantity, profitability vs quantity purchased, age-based product line preferences and behavorial clustering.
To properly prepare the dataset for applying the algorithm, the first part of the code involves a data preprocessing for aggregating information by "client_id", as illustrated in Figure 2.

![image](https://github.com/user-attachments/assets/1911b953-4ec8-4b25-8666-4c94191e6c68)


StandardScaler and One Hot Encoder
This code prepares the data for KMeans clustering by selecting features: gross_income, quantity, age, and product_line. It separates numerical features for standardization using StandardScaler, which scales data to have a mean of 0 and standard deviation of 1. Categorical features, like product_line, are encoded using OneHotEncoder. ColumnTransformer applies these transformations in a single pipeline, ensuring the dataset is ready for clustering.
We use StandardScaler and OneHotEncoder to prepare data for KMeans because the algorithm is sensitive to differences in scale and data types:

StandardScaler:
1 - Means uses Euclidean distance to measure similarity between data points.
2 - Features with larger scales (e.g., gross_income) would dominate those with smaller scales (e.g., age).
3 - StandardScaler standardizes numerical features by subtracting the mean and dividing by the standard deviation, ensuring all features contribute equally.

OneHotEncoder:

1 - KMeans works only with numerical data, so categorical features like product_line must be encoded as numbers.
2 - OneHotEncoder creates binary columns for each category, preventing the algorithm from incorrectly interpreting categories as numerical values.
3 - Dropping the first category avoids multicollinearity, improving clustering performance.

![image](https://github.com/user-attachments/assets/02bb7e60-cf26-4358-aaa2-8e6dbd0b663a)

# Selecting the Number of Clusters
Another important step for the algorithm to work correctly, is selecting the right number of clusters for the analysis. We don't want to overfit it. So, the code in the Figure 4 shows us how we can do it, by applying the Elbow Method.

![image](https://github.com/user-attachments/assets/9aed5772-0022-42c0-867a-fb9128f7012d)

Basically, the code will run the loop for 1 to 10 clusters, and by plotting the line graph, we can see how many clusters are necessary. The number of clusters selected will be the same as where the graph line stops declining, looking at X. We will then choose 04 clusters.

![image](https://github.com/user-attachments/assets/32ebb84c-3892-43f8-b6be-93bb4418268e)

# Finally, Applying the KMeans !!
Now that we did all the steps do fit the database to a adequate model to apply the algorithm, we can have some action ! The code is very simple, as shown in the Figure 6:

![image](https://github.com/user-attachments/assets/33052436-3594-4f8b-a09a-0be91d8e6a59)

With that script, we now have a column showing us which clusters each client belongs. And from that, the possibilities are almost infinite (just kidding, but we have quite a few !!!!).

# Some Visuals to Shows Us a Little Bit About the Data
We can use some visuals that can tells us a little bit about the data. For example: if we want to check in which intervals of gross income for the business each cluster of clients is, use a BOXPLOT:

![image](https://github.com/user-attachments/assets/a990ae7e-804a-46aa-946c-22c56d8afcd8)

Or, maybe we wanna check in a scatter visual, how our four clusters are divided within age and gross income, to check how our clients are distributed in these features.

![image](https://github.com/user-attachments/assets/e7af0029-9312-465b-9841-7dad962eb2bc)
![image](https://github.com/user-attachments/assets/bc6b0641-9fc6-4b48-a5ab-247a252efd35)

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







