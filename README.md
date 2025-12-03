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

## 1. 📌Background & Overview

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

## 2. 📂Dataset Description & Data Structure

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

## 3.🧹Data Cleaning & Preprocessing
<details>
<summary> <strong>Print the first five rows of dataset</strong></summary>
  
[In]: 
```python
#Print the first five rows of dataset
df=pd.read_excel(path+'ecommerce retail.xlsx',sheet_name = 'ecommerce retail')
df.head()
```

[Out]:  

<img width="1289" height="252" alt="image" src="https://github.com/user-attachments/assets/b40f8f8b-afde-4c80-afb1-f16f60063210" /> 
</details>

<details>
<summary> <strong>Check the general information of dataset</strong></summary>
  
[In]: 
```python
#Check the general information of df
print(df.info())
print('')
```
[Out]:
  
  <img width="624" height="324" alt="image" src="https://github.com/user-attachments/assets/48647d2b-55a7-4353-88c9-b957fe4533f9" />
</details>

<details>
<summary> <strong>Check data sumamry</strong></summary>
  
[In]: 
```python
#Check data summary
print(df.describe())
print('')
```

[Out]:
  
  <img width="807" height="474" alt="image" src="https://github.com/user-attachments/assets/55ffdf58-bf75-494f-99ec-e55b665ad8e5" />
</details>

<details>
<summary> <strong>⚡ Key Findings</strong></summary>

#### 1. Invalid Numerical Values
During initial data exploration, it was observed that the **Quantity** and **UnitPrice** columns contain negative values.  
These values are not logically valid for retail transactions and require further investigation.

**Possible actions:**
- Verify whether negative values represent refunds or cancellations.
- Check for data entry errors.
- Remove or correct invalid records to ensure accurate analysis.
  
#### 2. Stock Code vs. Description Mismatch
A mismatch was detected between:
- **StockCode count:** 4,070  
- **Description count:** 4,223  
This discrepancy indicates potential data quality issues.

**Possible reasons:**
- Multiple descriptions may exist for the same stock code.
- Some descriptions may not be linked to a valid stock code.
- Missing, duplicated, or improperly recorded stock codes.
  
**Recommendation:**  
Perform additional validation and cleaning to ensure consistency and reliability in downstream analysis.

#### 3. Manual Review Required
Certain orders contain **incorrect or inconsistent product descriptions**.  
A manual review is recommended to:
- Identify and flag incorrect descriptions  
- Classify them as errors  
- Prepare them for cleaning or exclusion in subsequent processing steps

#### 4. Unsual Data Type
Data Types: The following columns have inappropriate data types and should be converted to strings for easier processing:
- InvoiceNo, StockCode, Description, CustomerID, Country.
Data Values:
- Quantity < 0 & InvoiceNo starts with 'C' → These transactions indicate canceled orders and should be removed from the dataset.
- Quantity < 0 but InvoiceNo does NOT start with 'C' → These records contain incorrect descriptions and should be excluded from the dataset.
- UnitPrice < 0 & incorrect Description → These are invalid transactions and should also be removed from the dataset.
</details>

## 4.🔍Exploratory Data Analysis (EDA)
<details>
<summary> <strong>🛠 Step 1. Convert to correct Data type</strong></summary>
  
[In]: 
```python
#Correct data type
print(df.columns)
print('')

column_list = ['InvoiceNo','StockCode','Description','CustomerID','Country']
for c in column_list:
  df[c] = df[c].astype(str)
df.info()
```
</details>

<details>
<summary> <strong>🛠 Step 2. Remove Invalid Transactions</strong></summary>

[In]: 
```python
# @title Handle unsual data value
#drop data values have price < 0
df = df[df['UnitPrice'] > 0]

#drop data values have quantity < 0
df = df[df['Quantity'] > 0]
df = df.replace('nan',None)
df.shape
```
</details>

<details>
<summary> <strong>🛠 Step 3. Checking Missing Values in CustomerID & Error Columns</strong></summary>
  
[In 1]: 
```python
#List out missing data
print('List out missing data')
missing_data = {'volume': df.isnull().sum(), 'percent':df.isnull().sum()/df.shape[0]}
missing_df = pd.DataFrame.from_dict(missing_data, orient='index')
missing_df.head()
```

<details>
<summary>[Out 1]:</summary>
  
<img width="1149" height="154" alt="image" src="https://github.com/user-attachments/assets/028bf1dd-379e-4a8f-8eaa-e4038c45fdcc" />
</details>

[In 2]: 
```python
#Detect reasons about missing data (CustomerID)
print(df[df.CustomerID.isnull()].head())
print('')
print(df[df.CustomerID.isnull()].tail())
df['Day'] = pd.to_datetime(df['InvoiceDate']).dt.date
df['Month'] = df['Day'].apply(lambda x: str(x)[:7]) #Fixed to get the correct month format
df_group_day = df[df.CustomerID.isnull()][['Month','InvoiceNo']].groupby(['Month']).count().reset_index().sort_values(by=['Month'], ascending = True)
df_group_day.head()
```

<details>
<summary>[Out 2]:</summary>
  
<img width="851" height="832" alt="image" src="https://github.com/user-attachments/assets/39671e67-f7ff-443f-92dd-6f3dfdc3dc70" />
</details>

[In 3]: 
```python
#Handle missing data
#drop missing data
df = df[df['CustomerID'].notnull()]
df.head()
```

<details>
<summary>[Out 3]:</summary>

<img width="1622" height="238" alt="image" src="https://github.com/user-attachments/assets/9ebf99de-ca7d-4719-9a28-9d04c701f90e" />
</details>

### 🔍 Investigating Missing CustomerID

Before executing the code: It is important to check if the missing **CustomerID** is concentrated in specific countries or time periods before deciding how to handle it.

#### 🧐 Key Findings:
- **Missing CustomerID** values are **spread across all months & countries**, not just a specific region or time period.
- Likely due to **human errors** (e.g., incomplete updates) or **system recording issues**.

#### Hypothesis:
- **Missing CustomerID** might be concentrated in the **United Kingdom** or could be **distributed evenly** across all countries.
- These missing **CustomerID** values could be limited to specific **time periods** or may be **spread evenly** across the months.

#### ✅ Solution: 
Since **CustomerID is essential**, drop missing values to maintain data integrity.
</details>

<details>
<summary> <strong> 🛠 Step 4. Handle duplicate</strong></summary>

[In 1]: 
```python
#List out duplicated data
df_duplication = df.duplicated(subset=['InvoiceNo','StockCode','InvoiceDate','CustomerID'])
print(df[df_duplication].shape)
print('')
print(df.shape)
```

<details>
<summary>[Out 1]:</summary>
  
<img width="122" height="78" alt="image" src="https://github.com/user-attachments/assets/b801927d-3b7d-4540-a81c-24188ee4207f" />
</details>

[In 2]: 
```python
# @title Detect reasons about duplicated data
print(df[df_duplication].head())
```

<details>
<summary>[Out 2]:</summary>
  
<img width="817" height="442" alt="image" src="https://github.com/user-attachments/assets/4ef1102d-f202-4fa0-a43f-f5d16f4a8d2c" />
</details>

[In 3]: 
```python
#Handle duplicated data
df_drop_dup = df.drop_duplicates(subset=['InvoiceNo','StockCode','InvoiceDate','CustomerID'],keep = 'first')
df_drop_dup.shape
```

<details>
<summary>[Out 3]:</summary>

<img width="145" height="48" alt="image" src="https://github.com/user-attachments/assets/61b55ff4-0d01-440e-b54e-c2dbf7cd2ed7" />
</details>

The result (10038, 11) means there are 10,038 duplicate rows, and they need to be detected and handled
**Duplicates with the Same Quantity**:
   - These duplicates are likely caused by system errors (e.g., duplicate entries with the same quantity).
   - **Action**: Drop the duplicates because they are identical.
</details>

## 5. 🧮Apply RFM Model
#### ✅ Step 1. Calculate RFM Score
[In]: 
```python
#Identify last day
last_day = df_drop_dup['InvoiceDate'].max()
last_day
#Create RFM_df
RFM_df = df_drop_dup.groupby('CustomerID').agg(
    Recency = ('Day',lambda x: (pd.to_datetime(last_day).date() - x.max()).days), # Convert last_day to datetime.date
    Frequency = ('CustomerID','count'),
    Monetary = ('Cost','sum'),
    Start_Day = ('Day','min')).reset_index()
RFM_df.info()
```

<details>
<summary>[Out]:</summary>
  
<img width="398" height="270" alt="image" src="https://github.com/user-attachments/assets/e95502ee-8f78-49e2-b272-756fba878c8e" />
</details>

#### ✅ Step 2. Check outlier
[In]: 
```python
# Create a figure with 1 row and 3 columns
fig, axes = plt.subplots(1, 3, figsize=(18, 5))

# Plot Recency on the first chart (index 0)
sns.boxplot(data=RFM_df, x='Recency', ax=axes[0])
axes[0].set_title('Recency Outliers')

# Plot Monetary on the second chart (index 1)
sns.boxplot(data=RFM_df, x='Monetary', ax=axes[1])
axes[1].set_title('Monetary Outliers')

# Plot Frequency on the third chart (index 2)
sns.boxplot(data=RFM_df, x='Frequency', ax=axes[2])
axes[2].set_title('Frequency Outliers')

# Adjust spacing between charts
plt.tight_layout()
plt.show()
```

[Out]: 

<img width="2291" height="609" alt="image" src="https://github.com/user-attachments/assets/18a974ce-4bc9-4356-bef8-ad097ce6cadf" />

📌 **Solution:** We set a 95% threshold for **Recency**, **Frequency**, and **Monetary** to remove extreme values (outliers) from the dataset. This ensures that the analysis focuses on the majority of the data, improving its reliability for further insights.

#### ✅ Step  3. Assign RFM scores using Qcut
[In]: 
```python
#Create R, F, M (using qcut)
RFM_df['R'] = pd.qcut(RFM_df['Recency'],5,labels = range(1,6)).astype(str)
RFM_df['F'] = pd.qcut(RFM_df['Frequency'],5,labels = range(1,6)).astype(str)
RFM_df['M'] = pd.qcut(RFM_df['Monetary'],5,labels = range(1,6)).astype(str)
RFM_df['RFM'] = RFM_df.apply(lambda x: x.R + x.F + x.M, axis = 1)
RFM_df.head()
```

<details>
<summary>[Out]:</summary> 

<img width="817" height="239" alt="image" src="https://github.com/user-attachments/assets/625c7e96-063c-4963-a592-8ba0f751ac76" />
</details>

#### ✅ Step  4. Calculate RFM Score and Identify Segmentation
[In]: 
```python
# Flatten the segmentation table by splitting the 'RFM Score' column
df_seg['RFM Score'] = df_seg['RFM Score'].astype(str).str.split(',')
df_seg = df_seg.explode('RFM Score').reset_index(drop=True)

# Trim spaces in the 'RFM Score' column to ensure proper merging
df_seg['RFM Score'] = df_seg['RFM Score'].str.strip()

# Merge the segmentation table with the RFM table based on the 'RFM Score'
RFM_final = RFM_df.merge(df_seg, how='left', left_on='RFM', right_on='RFM Score')

# Display the final RFM segmentation table
RFM_final
```

<details>
<summary>[Out]:</summary> 

<img width="1146" height="519" alt="image" src="https://github.com/user-attachments/assets/0a00b7e8-dec7-4ad3-814b-0df4cf44bd4a" />
</details>

## 6. 📊Visualization & Analysis
