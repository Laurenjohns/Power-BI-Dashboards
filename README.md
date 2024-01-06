# Power BI Dashboards

## Table of Contents 

- [Boiler Plant Simulation](#boiler-plant-simulation)
- [Brokerage Dashboard](#brokerage-dashboard)
- [Forecasting Global Temperatures](#forecasting-global-temperatures)
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

### Brokerage Dashboard

Project Overview: Interactive dashboard using data that includes seven clients from around the world, and brokerage data spanning four years.
Utilizing DAX Measurements on gauge visuals for minimum and maximum values. 

```dax
M0 - 0
M6 - .06
```

### Forecasting Global Temperatures 

Project Overview: Interactive dashboard using global temperature data to create a forecast.
