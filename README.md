# 🛒 Customer Segmentation For Marketing Campaigns in A Retail Global SuperStore | Python
<img width="1670" height="905" alt="image" src="https://github.com/user-attachments/assets/16dc8b94-6e70-4495-aafd-b44c2e5cc682" />

**Author:** Huong Le | **Date:** May 2025 | **Tools Used:** Python 

## Table of Contents
1. 📌 [Background & Overview](#-background--overview)
2. 📁 [Dataset Description & Data Structure](#-dataset-description--data-structure)
3. 🧠 [Design Thinking Process](#-design-thinking-process)
4. 📊 [Key Insights & Visualizations](#-key-insights--visualizations)
5. 🔍 [Final Conclusion & Recommendation](#-final-conclusion--recommendation)

---

## 📌 Background & Overview

**Objective:**

**📖 What is this project about?**

- The Marketing team aims to launch personalized campaigns to enhance customer retention and acquisition during the holiday season. However, because the dataset is large, manual segmentation is no longer efficient.
- To solve this, the **RFM (Recency–Frequency–Monetary) model** is applied using **Python (Google Colab)** to classify customers based on past purchasing behavior.
- This project includes:
  - Data cleaning & preparation  
  - RFM score calculation  
  - Customer segmentation  
  - Visualization  
  - Actionable business recommendations  

**👤 Who is this project for?**
- Marketing & Sales Department  
- Business stakeholders & decision-makers 

**🔍 Why use RFM?**

RFM (Recency, Frequency, Monetary) is a customer analytics technique used to evaluate purchasing behavior and categorize customers into meaningful segments. Each customer receives a score based on the three RFM dimensions, helping businesses identify high-value audiences for targeted marketing and sales strategies.

- **Recency:** Measures how long it has been since the customer's last purchase.  
- **Frequency:** Evaluates how often the customer makes purchases.  
- **Monetary:** Calculates the total amount spent by the customer.

By applying RFM, businesses can segment customers based on their value, allowing them to personalize campaigns, prioritize high-value groups, and improve customer engagement strategies.

## 📂 Dataset Description & Data Structure

### **📌 Data Source** 
- **Source:** Provided dataset for E-commerce retail analysis  
- **Size:** **541,910** rows × **8** columns (Sheet 1: *E-commerce Retail*). Additional segmentation details in Sheet 2  
- **Format:** `.xlsx` (Excel file with **two** sheets)

### 📊 **Data Structure**  
The dataset consists of **two tables (sheets):**
- **Sheet 1 – E-commerce Retail:** Transaction-level records (order details, customer IDs, purchase info)  
<details>
<summary><strong>📁 Dataset Schema</strong></summary>

| Column Name  | Data Type       | Description                                                                 |
|--------------|-----------------|------------------------------------------------------------------------------|
| `InvoiceNo`  | `object`        | Unique invoice number for each transaction (6-digit). If it starts with `C`, it indicates a **cancellation**. |
| `StockCode`  | `object`        | Unique product (item) code (5-digit).                                       |
| `Description`| `object`        | Product (item) name.                                                         |
| `Quantity`   | `int64`         | Number of units purchased per transaction.                                   |
| `InvoiceDate`| `datetime64[ns]`| Date and time when the transaction occurred.                                 |
| `UnitPrice`  | `float64`       | Price per unit of the product (GBP).                                         |
| `CustomerID` | `float64`       | Unique **5-digit** identifier for each customer.                             |
| `Country`    | `object`        | Country where the customer resides.                                          |
</details>

- **Sheet 2 – Segmentation:** Customer segments with their **RFM** scores 
<details>
<summary><strong>📊 RFM Segmentation Mapping</strong></summary>

| Segment               | RFM Score                                                                                                                                                                  |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Champions**        | 555, 554, 544, 545, 454, 455, 445                                                                                                                                            |
| **Loyal**            | 543, 444, 435, 355, 354, 345, 344, 335                                                                                                                                        |
| **Potential Loyalist** | 553, 551, 552, 541, 542, 533, 532, 531, 452, 451, 442, 441, 431, 453, 433, 432, 423, 353, 352, 351, 342, 341, 333, 323                                                       |
| **New Customers**    | 512, 511, 422, 421, 412, 411, 311                                                                                                                                            |
| **Promising**        | 525, 524, 523, 522, 521, 515, 514, 513, 425, 424, 413, 414, 415, 315, 314, 313                                                                                                |
| **Need Attention**   | 535, 534, 443, 434, 343, 334, 325, 324                                                                                                                                        |
| **About To Sleep**   | 331, 321, 312, 221, 213, 231, 241, 251                                                                                                                                        |
| **At Risk**          | 255, 254, 245, 244, 253, 252, 243, 242, 235, 234, 225, 224, 153, 152, 145, 143, 142, 135, 134, 133, 125, 124                                                                  |
| **Cannot Lose Them** | 155, 154, 144, 214, 215, 115, 114, 113                                                                                                                                        |
| **Hibernating Customers** | 332, 322, 233, 232, 223, 222, 132, 123, 122, 212, 211                                                                                                                   |
| **Lost Customers**   | 111, 112, 121, 131, 141, 151 
</details>

## 🧹 Data Cleaning & Preprocessing
[In 1]: 
```python
#Print the first five rows of dataset
df=pd.read_excel(path+'ecommerce retail.xlsx',sheet_name = 'ecommerce retail')
df.head()
```
<details>
  <summary>[Out 1]:</summary>
  
  <img width="1289" height="252" alt="image" src="https://github.com/user-attachments/assets/b40f8f8b-afde-4c80-afb1-f16f60063210" />
</details>

[In 2]: 
```python
#Check the general information of df
print(df.info())
print('')
```
<details>
  <summary>[Out 2]:</summary>
  
  <img width="624" height="324" alt="image" src="https://github.com/user-attachments/assets/48647d2b-55a7-4353-88c9-b957fe4533f9" />
</details>
