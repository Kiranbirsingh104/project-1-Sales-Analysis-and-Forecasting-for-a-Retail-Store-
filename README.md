# project-1-Sales-Analysis-and-Forecasting-for-a-Retail-Store-
import numpy as np 
import pandas as pd
import os
for dirname, _, filenames in os.walk('/kaggle/input'):
    for filename in filenames:
        print(os.path.join(dirname, filename))
        import pandas as pd 
import numpy as np
store = pd.read_csv("/kaggle/input/superstore-sales/superstore_final_dataset (1).csv",encoding='latin-1')
store.head()
store = store.rename(columns={'Order_Date':'Date','Product_ID':'ProductID','Sales':'Price'})
data = store[['Date','ProductID',"Price"]]
store["Quantity"]=np.random.poisson(lam=3)
store['Totalsales']=data['Quantity']*data['Price']
store.head()
data = store[['Date','ProductID',"Price",'Quantity','Totalsales']]
data.head()
#dataprepocessing
#usedformissingvalue
data.isnull().sum()
#usedwhereduplicatevale
data.duplicated().sum()
#tellsdatatype
data['Date'] = pd.to_datetime(data['Date'])
type(data,[0]) 
# Line plot for sales trends over time
plt.figure(figsize=(14, 7))
plt.plot(sales_trends['Date'], sales_trends['Totalsales'])
plt.title('Sales Trends Over Time')
plt.xlabel('Date')
plt.ylabel('Total Sales')
plt.show()
# Aggregate total sales by product
top_products = data.groupby('ProductID').agg({'Totalsales': 'sum'}).sort_values(by='Totalsales', ascending=False).head(10).reset_index()
# Bar plot for top-selling products
plt.figure(figsize=(14, 7))
plt.bar(top_products['ProductID'], top_products['Totalsales'])
plt.title('Top-Selling Products')
plt.xlabel('Product ID')
plt.ylabel('Total Sales')
plt.show()
import seaborn as sns
# Compute the correlation matrix
correlation_matrix = data[['Quantity', 'Price', 'Totalsales']].corr()
# Heatmap for the correlation matrix
plt.figure(figsize=(5, 4))
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', fmt='.2f')
plt.title('Correlation Matrix')
plt.show()
import seaborn as sns
# Compute the correlation matrix
correlation_matrix = data[['Quantity', 'Price', 'Totalsales']].corr()
# Heatmap for the correlation matrix
plt.figure(figsize=(5, 4))
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', fmt='.2f')
plt.title('Correlation Matrix')
plt.show()
