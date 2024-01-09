# Power BI Dashboards

## Table of Contents 

- [Boiler Plant Simulation](#boiler-plant-simulation)
- [Brokerage Dashboard](#brokerage-dashboard)
- [Forecasting Global Temperatures](#forecasting-global-temperatures)
- [Call Center Performance Simulation](#call-center-performance-simulation)
  
---
### Boiler Plant Simulation 

Project Overview:  Real-time simulation of a boiler plant using SQL Server to store boiler information per second.
The below query will create a blank table with all the columns of the Boiler table, use a loop to insert data from the main table into this blank table, simulating real-time monitoring.

```sql
insert into boiler select * from BoilerPlantSmall where time = 1; 
select * from boiler; 

delete from boiler; 
declare @i int = 0;

while (@i < 1999)
   begin 
       waitfor delay '00:00:01'
            set @i = @i + 1; 
            insert into boiler select * from BoilerPlantSmall where time = @1; 
            select * from boiler; 
End 
```
---
### Brokerage Dashboard

Project Overview: Interactive dashboard using data that includes seven clients from around the world, and brokerage data spanning four years.
Utilizing DAX Measurements on gauge visuals for minimum and maximum values. 

```dax
M0 - 0
M6 - .06
```
---
### Forecasting Global Temperatures 

Project Overview: Interactive dashboard using global temperature data to create a forecast.

---
### Call Center Performance Simulation

Project Overview: Real-Time performance monitoring of a call center using Python, Microsoft SQL Server, and Power BI. The simulation will generate random calls from customers and store the call center information in a Microsoft SQL server database for performance monitoring. Utilizing the insert command and connecting Python to the SQL server for automatic data entry.

```python
import datetime
import time
import random
import pyodbc

con = pyodbc.connect('Driver={SQL Server};'
                        'Server=Ljay\LJAY;'
                        'Database=Call_Center;'
                        'Trusted_Connection=yes;')
   cursor = com.cursor()

while 1==1:
    date = datetime.date.today()
    location = random.randint(111, 201) 
    company = random.randint(11,30)
    issue = random.randint(111, 130)
    csr = random.randint(111, 210)
    rtime = random.randint(1,300)
    ctime = random.randint(1,600)
    status = random.randint(1,4)
    if status == 1:
        rating = random.randint(5,10)
    elif status == 2:
        rating = random.randint(3,8)
    elif status == 3:
        rating = random.randint(1,3)
    elif status == 4: 
        rating = random.randint(1,5)
        
    print(date)
    cursor.execute('insert into calls values(GETDATE(),'
                 + str(location) + ','
                 + str(company) + ','
                 + str(issue) + ','
                 + str(rtime) + ','
                 + str(ctime) + ','
                 + str(status) + ','
                 + str(rating) + ')'
                 )
  
  
    cursor.commit()
    time.sleep(1)
```
Insert Command via SQL Server Example

```sql
insert into issues values (111,'Billing and payment issues')
insert into issues values (112,'Technical difficulties with a product or service')
insert into issues values (113,'Difficulty navigating a website or app')
insert into issues values (114,'Inquiries about product availability or delivery status')
insert into issues values (115,'Issues with account access or login credentials')
insert into issues values (116,'Product malfunctions or defects')
insert into issues values (117,'Problems with the quality or functionality of a product')
insert into issues values (118,'Returns and exchanges')
insert into issues values (119,'Difficulty understanding or using a product or service')
insert into issues values (120,'Customer service complaints or dissatisfaction with a previous experience')
insert into issues values (121,'Problems with shipping or receiving a product')
insert into issues values (122,'Difficulty cancelling or modifying an order')
insert into issues values (123,'Issues with refunds or billing discrepancies')
insert into issues values (124,'Trouble using a coupon or discount code')
insert into issues values (125,'Inquiries about product warranties or guarantees')
insert into issues values (126,'Technical support for a product or service')
```
Excel Function

```excel
="insert into companies values ("&A6&",'"&TRIM(B6)&"','"&TRIM(C6)&"',0)"
```
---
