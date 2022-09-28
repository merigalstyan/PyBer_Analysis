# PyBer_Analysis

## Purpose

The purpose behind the PyBer Analysis is to retrieve information about a ride-sharing data by city type, create a summary and visualize the findings by plotting charts.

## The Analysis

In order to effectively explain the findings of this analysis it's essential to look at it step-by-step. We'll go over the analysis section by section. This will allow us to understand each outcome even better. But before we do that, it's important to import dependencies and read all the files provided for this analysis and to merge these files.

<img width="640" alt="Screen Shot 2022-09-27 at 4 35 10 PM" src="https://user-images.githubusercontent.com/111609994/192655791-264a881d-3a8d-4139-a831-662809f94698.png">

<img width="714" alt="Screen Shot 2022-09-27 at 4 35 20 PM" src="https://user-images.githubusercontent.com/111609994/192655805-4427e411-dd74-4e18-865e-d3472c94d6fd.png">

After importing **matplotlib** and **pandas**, the ***read_csv*** reads the files and ***pd.merge*** combines the datasets.


## Part 1

### The Averages

Perhapes the first part of this analysis is the most essential one. This section calculates the average fare per ride and average fare per driver for each city type. This information will show us the different fares between the city types. We first need to understand how many total rides was completed in each city type, how many drivers each city type has and what are the fares for each city type by using the **groupby()** and **count()** functions:

<img width="664" alt="Screen Shot 2022-09-27 at 4 40 48 PM" src="https://user-images.githubusercontent.com/111609994/192656394-006a36cd-8f2d-4322-8437-b484bc4c0eae.png">
<img width="640" alt="Screen Shot 2022-09-27 at 4 41 40 PM" src="https://user-images.githubusercontent.com/111609994/192656409-9052e39d-19f0-43d6-9ea5-1a13a44026ae.png">
<img width="627" alt="Screen Shot 2022-09-27 at 4 41 31 PM" src="https://user-images.githubusercontent.com/111609994/192656416-367c2b14-1721-4418-aeb9-08b27c58c888.png">

Let's look at the results:

* The first code shows us that the number of total rides depending on city type can vary enormously. While urban cities completed 1625 rides, suburban cities completed more than 2.5 times less rides totalling 625 and rural cities completed only 125 total rides. 
<img width="169" alt="Screen Shot 2022-09-27 at 4 46 46 PM" src="https://user-images.githubusercontent.com/111609994/192656850-00275966-2967-4a36-8b7e-ac9874a1376c.png">

* The same disparities occur when counting the number of total drivers per city type:
<img width="151" alt="Screen Shot 2022-09-27 at 4 48 39 PM" src="https://user-images.githubusercontent.com/111609994/192657010-b6b24139-ea77-4a86-a944-8e04502f6223.png">

* Accordingly, the average fares are higher in urban cities, less in suburban and rural areas:
<img width="196" alt="Screen Shot 2022-09-27 at 4 49 51 PM" src="https://user-images.githubusercontent.com/111609994/192657104-67795f3d-442c-446a-a9af-8a0324fbcc0a.png">

Even though urban cities completed a lot more rides than suburban and rural cities, they have considerably higher number of drivers and thus the average fares are higher in rural and suburban areas. Using the ***total fares per city type / total rides per city type*** we can see the average fare per ride in all areas.In addition, each driver earnes more in rural cities than suburban and urban cities. The average fare per driver is calculated by ***total fares per city type / total number of drivers per city type***. The results are as follows:

<img width="549" alt="Screen Shot 2022-09-27 at 5 05 58 PM" src="https://user-images.githubusercontent.com/111609994/192664843-86f061a5-583e-4d76-a95c-31ed49523723.png">

## Part 2

### Total Weekly Fares by City Type

The second part of the analysis includes finding the total weekly fares by city type and plotting it. This part requires to look at the sum of fares based not only on type, but on date as well. To find this we need to group our original merged data by ***date*** and ***type*** and compute the sum of ***fares***. 
**the sum of the fares for each date = df.groupby(["date","type"]).sum()["fare"].**

To simplify our data and have a better visual, we use the **pd.pivot_table()** function and since we want to look at the data from 2019, we use ***loc*** to filter the dates from ***2019-01-01*** to ***2019-04-29***. Let's have a look at the code:

<img width="902" alt="Screen Shot 2022-09-27 at 6 21 14 PM" src="https://user-images.githubusercontent.com/111609994/192665879-37bcc27a-a274-4573-97e9-8cd7d5d60d37.png">

**NOTE**: Before looking at the result, it's important to make sure that the datatype is ***DatetimeIndex*** in order to resample the data later.

To change the datatype we simply use **df.index = pd.to_datetime(df.index)**. This method converts all the NaN values in the pivot table. This will allow us to finally plot our data for weekly fares. 

<img width="424" alt="Screen Shot 2022-09-27 at 6 26 42 PM" src="https://user-images.githubusercontent.com/111609994/192666493-e91c17ef-6c33-4321-9fab-c3ef88f3fd9c.png">

Taking all these steps finally allows us to see the differences between the total fares by city types. 

![PyBer_fare_summary](https://user-images.githubusercontent.com/111609994/192666574-b3b31cef-3590-4203-8af4-91feba4e6132.png)

Even though individual drivers earned more in suburban and rural cities than drivers in urban cities, we can see from the graph that urban city type has the highest amount of fares weekly between the months of January and April in 2019. 

## Summary

Let's address the differences in the results. There are several disparities between city types and summarizing them could be of help:

* The number of total rides is highest in urban cities (1625), less in suburban cities (625) and least in rural cities(125).
* Average fare per ride is very high in rural area ($34.62), less in suburban($30.97) and urban($24.52) cities.
* Average fare per driver is different accordingly: $55.48, $39.50, $16.57
* Despite average fares being higher in rural and suburban areas, based on the ride number urban cities have the highest profit overtime.

Although these disparities can depend on many internal and external factors, some recommendations are:

**1.** Researching rural and suburban cities to understand demand. There is a need for more drivers in these cities. The company could recruit more drivers only if there is high demand. More research could help understand the service demand and fix the supply.

**2.** The fares are high in rural and suburban cities. Even though this can depend on the lack of drivers and lack of demand, there is a need of extensive research to understand whether or not the high fares could cause lack of demand and thus, lack of drivers. This matter is intertwined and research is required as mentioned above.

**3.** In this analysis we're looking at a couple of months in 2019. This can damage our analysis. The ride_share data is huge and only looking at this short timeframe could jeopardize the analysis. Maybe an additional analysis could be conducted using longer periods than Jan - Apr of 2019.



