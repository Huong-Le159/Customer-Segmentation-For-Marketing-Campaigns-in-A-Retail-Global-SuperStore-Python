# [PYTHON] Customer Segmentation with RFM Analysis
 ---
## 📑 Table of Contents  
1. [📌Overview](#-background--overview)  
2. [📂 Dataset](#-dataset-description--data-structure)  
3. [🔎 Final Conclusion & Recommendations](#-final-conclusion--recommendations)
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
---
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

## III.Python Analysis
### 3. Applying RFM model to release marketing campaign for loyal customer to give Thank you letter
#### 3.1. Distribution customer volume and spending by segmentation
<img width="1310" height="734" alt="image" src="https://github.com/user-attachments/assets/6377a871-cc5c-4fef-8229-906c73ac9234" />



