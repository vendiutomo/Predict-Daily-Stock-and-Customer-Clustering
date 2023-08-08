# Predict-Daily-Stock-and-Customer-Clustering
Project-Based Virtual Intern: Data Scientist | Kalbe Nutritionals x Rakamin Academy | [Presentation is Here](https://www.canva.com/design/DAFpswM-zW8/_UQjb-DgfQPC88Fme9D8Yw/view?utm_content=DAFpswM-zW8&utm_campaign=designshare&utm_medium=link&utm_source=publishsharelink)!

> In this project I am a Data Scientist who assists the inventory team in predicting daily stock requirements and also helps the marketing team group customers into several segments/clusters to increase the effectiveness of marketing activities.

> Dataset is data from the company that contains 10 products, 14 stores, 447 customers, and 5020 transactions made in 2022.

## Exploratory Data Analysis with SQL
- Average age of the customers per marital status,
- Average age of the customers per gender,
- Store (name) that has the highest total quantity of products purchased,
- The best-selling product that has the largest total amount.

## Create a Dashboard with Tableau
<div class='tableauPlaceholder' id='viz1691464520463' style='position: relative'><noscript><a href='#'><img alt='Sales Transactions in 2022 ' src='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;VI&#47;VIXDSKalbeNutritionalsxRakaminAcademy&#47;SalesTransactionsin2022&#47;1_rss.png' style='border: none' /></a></noscript><object class='tableauViz'  style='display:none;'><param name='host_url' value='https%3A%2F%2Fpublic.tableau.com%2F' /> <param name='embed_code_version' value='3' /> <param name='site_root' value='' /><param name='name' value='VIXDSKalbeNutritionalsxRakaminAcademy&#47;SalesTransactionsin2022' /><param name='tabs' value='no' /><param name='toolbar' value='yes' /><param name='static_image' value='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;VI&#47;VIXDSKalbeNutritionalsxRakaminAcademy&#47;SalesTransactionsin2022&#47;1.png' /> <param name='animate_transition' value='yes' /><param name='display_static_image' value='yes' /><param name='display_spinner' value='yes' /><param name='display_overlay' value='yes' /><param name='display_count' value='yes' /><param name='language' value='en-US' /></object></div>

## Modeling
- Data Cleansing
  - No Duplicated Data,
  - There are missing values in the marital status column, imputing it with the mode value,
  - Data Type Adjustment - adjust data type of column 'datetransaction' from 'object' to 'datetime'. Then make new column, 'day', which contains information on what day in 2022 (1-365),
  - Feature Selection - drop useless columns, such as 'storeid.1', 'latitude', 'longitude', 'customerid.1', 'productid.1' and 'price.1'.
  
### Predict Daily Stock
![image](https://github.com/vendiutomo/Predict-Daily-Stock-and-Customer-Clustering/assets/128874036/924dffed-f5ef-4bdf-9619-d91038c7e9cd)

Machine Learning: Linear Regression

![image](https://github.com/vendiutomo/Predict-Daily-Stock-and-Customer-Clustering/assets/128874036/2d83ed88-d322-4d28-8a7a-27c8cc1a283e)

- r-squared score: 0.780
- mean squared error: 58.095

- Model Linear Regression: y = 3.815x - 1.624

### Customer Clustering
Machine Learning: KMeans Clustering

1. Find The Optimal Number of Cluster

![image](https://github.com/vendiutomo/Predict-Daily-Stock-and-Customer-Clustering/assets/128874036/e5022ca2-1ce7-4235-a6ce-289d01f2bcc6)

From clusters 1 to 3 the distance between clusters is quite far apart, but from clusters 3 to 4 onwards the distance is quite close and getting closer. It can be said that cluster 3 is an optimal cluster.

2. Modeling wth 3 clusters

![image](https://github.com/vendiutomo/Predict-Daily-Stock-and-Customer-Clustering/assets/128874036/48bf1c23-600a-4f38-b57e-be10f1ae73de)

![image](https://github.com/vendiutomo/Predict-Daily-Stock-and-Customer-Clustering/assets/128874036/d23d1856-4114-46cc-a4ae-4e03bc627dc3)

> **Interpretation**:
> 
>**Cluster 0**
>- transaction: 7 - 16
>- quantity product: 26 - 63
>- spending amount: IDR 308.800 - 459.100
>Customers in this group make transactions in a fairly rare amount, although not as many as cluster 1 but not the smallest. This group defined as **Mid Spender**.
>
>**Cluster 1**
>- transaction: 6 - 15
>- quantity product:41 - 79
>- spending amount: IDR 462.700 - 846.700
>This group has the highest average transactions, highest average product purchase quantity and largest average total purchases compared to other groups. This group is defined as **High Spender**.
>
>**Cluster 2**
>- transaction : 3 - 14
>- quantity product: 10 - 46
>- spending amount: IDR 92.100 - 306.400
>This group has the smallest transactions, quantities, and purchases compared to other groups. This group tends to make purchases in small quantities and with small frequency. This cluster is defined as **Low Spender**.

> **Recommendation**:
> 1. Monitoring transactions and retention from the **High Spender** group can **improve service** so that these groups do not churn in the future.
> 2. For the **Mid Spender** group, further analysis can be carried out on **how to increase transactions by providing more personal recommendations**, as well as deeper analysis on how to optimize promos in this segment and keep shopping.
> 3. For the **Low Spender** group, further analysis can also be carried out on **how to increase the desire to make transactions**. This can be caused by products or prices that do not match.
