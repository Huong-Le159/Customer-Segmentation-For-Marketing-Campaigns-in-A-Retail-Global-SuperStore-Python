# [PYTHON] Customer Segmentation with RFM Analysis
<div align="center">
  <img width="500" height="399" alt="image" src="https://github.com/user-attachments/assets/8e3e23fc-8905-4db6-bbe2-3e92b94ad6c3" />
</div>   

 ---
## I. Overview 
SuperStore is a global retail company with a large customer base. To celebrate Christmas and New Year, the Marketing department wants to launch to show appreciation to loyal customers who have supported the company over the years, as well as to engage potential customers who could become loyal clients.
### 1. About RFM Analysis
- RFM is a marketing analysis technique that stands for Recency, Frequency, and Monetary Value.
   - **Recency**: measures how recently a customer has made a purchase.
   - **Frequency**: measures how often a customer has made purchases.
   - **Monetary Value**: measures the total amount of money a customer has spent on purchases.
- In RFM Analysis, customer database is segmented into different groups based on this Recency - Frequency - Monetary score.
### 2. Business Questions
- The marketing department proposed a plan using RFM model (Recency, Frequency, Monatery) in Python to segment customer, then launch marketing campaigns to give thank you letter to loyal customer, exploit potential customer to become loyal customer.
- Suggest to the Marketing and Sales team with the company's retail model, which of the three indicators R, F, M should be most interested in?

## II.Dataset
| **Column Name** | **Data Type** | **Description**                                    |
| --------------- | ------------- | -------------------------------------------------- |
| InvoiceNo       | INT           | Unique identifier for each transaction (invoice).  |
| StockCode       | TEXT          | Unique product code for each item.                 |
| Description     | TEXT          | Product name or description.                       |
| Quantity        | INT           | Number of items purchased per product per invoice. |
| InvoiceDate     | DATETIME      | Date and time when the transaction occurred.       |
| UnitPrice       | FLOAT         | Price per unit of the product.                     |
| CustomerID      | INT           | Unique identifier for each customer.               |
| Country         | TEXT          | Country where the transaction took place.          |

## III.Python Analysis and Insights
### 1. Find Loyal customer to give Thank you letter in Marketing campaign
<img width="1310" height="734" alt="image" src="https://github.com/user-attachments/assets/6377a871-cc5c-4fef-8229-906c73ac9234" />

- 'New Customer' + 'Potential Loyalist' + 'Promising' = Majority of customer base with large volume group about 15% to 18% but low spending contribution about 5% to 8% => Company should consider to give them nuturing campain such as educational email flows, onboarding welcome discounts.
- 'Loyal' = Steady + Valuable with medium volume about 18% and good spending about 11% which are brand fans for company => They should receive Thank you letter from marketing campaign of company in the future.
    
### 2. Find potential customers to become Loyal customers
<img width="1284" height="901" alt="image" src="https://github.com/user-attachments/assets/3f1a53e3-d1d2-4b19-aa7f-bd6e8a9a1b18" />

- Non Loyal cusotmers have a large portion in q3 and q4 (quantity > 10) which means although they've purchased quite a lot but still aren't tagged as Loyal customer => they are potential customers. Therefore, company should send them personalized offers, encourage them to make another purchase soon to increase Recency score and recommend high-value products to increase Monetary score.
    
#### 3. Find indicator in R, F, and M should be most interested in
<img width="888" height="672" alt="image" src="https://github.com/user-attachments/assets/69389174-a07f-4ac4-8b8c-8cfc6b7cf658" />

- 'Very Recent' customers spend the most who made a purchase most recently and are spending the highest average amount. This is make sense in supermarket settings, the more recently a customer buys, the more they tend to spend => Recency is a powerful driver of revenue in retail industry.



