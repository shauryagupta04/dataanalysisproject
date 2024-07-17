import kaggle
#to import data set
kaggle datasets download ankitbansal06/retail-orders  -f orders.csv
import zipfile
#to extract csv file from zip file
zip_ref =  zipfile.ZipFile('orders.csv.zip')
zip_ref.extractall()
zip_ref.close()
#importing pandas
import pandas as pd
#performing data processing
#removing unknown values
df = pd.read_csv('orders.csv',na_values=['Not Available', 'unknown'])
# converting them to lower case
df.columns=df.columns.str.lower()
df.columns=df.columns.str.replace(' ','_')
#adding new column discount
df['discount']=df['list_price']*df['discount_percent']*.01
df['sale_price']= df['list_price']-df['discount']
df['profit']=df['sale_price']-df['cost_price']
df['order_date']=pd.to_datetime(df['order_date'],format ="%Y-%m-%d")
#deleting unnecessary columns
df.drop(columns=['list_price','discount_percent','cost_price'], inplace=True)
import sqlalchemy as sal
engine = sal.create_engine('mssql://DESKTOP-63D6CEJ\\SQLEXPRESS/master?driver=ODBC+DRIVER+17+FOR+SQL+SERVER')
conn =engine.connect()
