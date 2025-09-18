# 🥖 Bakery Buy/Sell Insights with Machine Learning

<div align="center">
  <img src="https://img.shields.io/badge/Step%201-Database%20Connection-blue?style=for-the-badge">
  <img src="https://img.shields.io/badge/Step%202-Data%20Preparation-orange?style=for-the-badge">
  <img src="https://img.shields.io/badge/Step%203-Model%20Training-green?style=for-the-badge">
  <img src="https://img.shields.io/badge/Step%204-Visualization-purple?style=for-the-badge">
</div>

---

## 🌐 **Part 1: Connecting the Bakery Database**

Connect your bakery sales database to the project using Python and your preferred database connector (e.g., `sqlite3`, `mysql-connector-python`, `psycopg2`).  
This step ensures seamless data extraction for analysis and model training.

```python
import sqlite3

conn = sqlite3.connect("bakery_sales.db")
cursor = conn.cursor()
sales_data = cursor.execute("SELECT * FROM sales").fetchall()
```
> 🟦 All database credentials and access details must be configured in the `config.py` file.

---

## 🧹 **Part 2: Data Study & Organization**

In this phase, we analyze and organize the raw sales data:

- Remove duplicates and handle missing values.
- Structure data into clear columns (date, product, quantity, price, etc.).
- Generate summary statistics and visualizations to understand patterns.

```python
import pandas as pd

df = pd.DataFrame(sales_data, columns=["date", "product", "quantity", "price", "buyer_type"])
df.drop_duplicates(inplace=True)
df.fillna(0, inplace=True)
```
> 🟧 This step prepares the data for effective model training.

---

## 🧠 **Part 3: Model Training & MLflow Tracking**

Train machine learning models to identify the advantages (🟩) and disadvantages (🟥) of buying/selling in the bakery.  
Track experiments and metrics using **MLflow** for reproducibility and comparison.

```python
import mlflow
from sklearn.ensemble import RandomForestClassifier

mlflow.start_run()
model = RandomForestClassifier()
model.fit(X_train, y_train)
mlflow.sklearn.log_model(model, "model")
mlflow.log_metrics({"accuracy": accuracy_score(y_test, y_pred)})
mlflow.end_run()
```
> 🟩 MLflow helps you store models, results, and artifacts for future reference.

---

## 📊 **Part 4: Conclusions & Power BI Visualization**

Visualize the results and key findings in **Power BI** for a clear, interactive presentation:

- Import processed data and model predictions into Power BI.
- Create colorful charts to show when buying or selling is most advantageous.
- Clearly distinguish advantages (🟩 green), disadvantages (🟥 red), and neutral findings (🟨 yellow).

> 🟪 Power BI dashboards make insights accessible to everyone in the bakery business.

---

<div align="center">
  <h3>🙏 Thank You!</h3>
  <p>We appreciate your attention and interest in this bakery machine learning study.<br>
  May these insights help your business rise to new heights! 🥐</p>
</div>
