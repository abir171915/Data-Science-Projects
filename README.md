# 🛒 Retail Orders Data Analysis Project

This is an end-to-end data analysis project that demonstrates the process of downloading real-world retail order data, cleaning and transforming it using Python, storing it in a MySQL database, and performing SQL-based analysis to derive insights.

---

## 📥 Dataset Source

- **Kaggle Dataset**: [Retail Orders Dataset](https://www.kaggle.com/datasets/ankitbansal06/retail-orders)

---

## 🔧 Tech Stack

- **Python** (Pandas, SQLAlchemy, PyMySQL, etc.)
- **MySQL** (MariaDB via XAMPP)
- **Jupyter Notebook**
- **Kaggle API**
- **GitHub** (for version control and collaboration)

---

## 📁 Project Workflow

### 1. 📦 Data Acquisition
- Used `kaggle` API to download `orders.csv.zip` from Kaggle.
- Unzipped the dataset and loaded into a Pandas DataFrame.

### 2. 🧹 Data Cleaning & Transformation
- Standardized column names (lowercase, replaced spaces with `_`).
- Derived new columns:
  - `discount = list_price * discount_percent * 0.01`
  - `sale_price = list_price - discount`
  - `profit = sale_price - cost_price`
- Converted `order_date` from string to datetime.
- Dropped unnecessary columns: `list_price`, `cost_price`, `discount_percent`.

### 3. 🗃️ MySQL Database Upload
- Created a MySQL database `orders` using XAMPP/MariaDB.
- Used `SQLAlchemy` + `PyMySQL` to upload cleaned DataFrame to a table named `df_orders`.

```python
# Example Python connection
import sqlalchemy as sal
engine = sal.create_engine("mysql+pymysql://root:YOUR_PASSWORD@localhost:3306/orders")
conn = engine.connect()
df.to_sql('df_orders', con=conn, index=False, if_exists='append')


🙌 Acknowledgments
Dataset by Ankit Bansal on Kaggle

Tools: Kaggle API, Pandas, SQLAlchemy, MySQL
