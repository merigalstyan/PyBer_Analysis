# PyBer_Analysis

## Purpose

The purpose behind the PyBer Analysis is to retrieve information about a ride-sharing data by city type, create a summary and visualize the findings by plotting charts.

## The Analysis

In order to effectively explain the findings of this analysis it's essential to look at it step-by-step. We'll go over the analysis section by section. This will allow us to understand each outcome even better. But before we do that, it's important to import dependencies and read all the files provided for this analysis and to merge these files.

<img width="640" alt="Screen Shot 2022-09-27 at 4 35 10 PM" src="https://user-images.githubusercontent.com/111609994/192655791-264a881d-3a8d-4139-a831-662809f94698.png">

<img width="714" alt="Screen Shot 2022-09-27 at 4 35 20 PM" src="https://user-images.githubusercontent.com/111609994/192655805-4427e411-dd74-4e18-865e-d3472c94d6fd.png">

After importing **matplotlib** and **pandas**, the ***read_csv*** reads the files and ***pd.merge*** combines the datasets.


## Part 1: The Averages

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

<img width="559" alt="Screen Shot 2022-09-27 at 4 57 11 PM" src="https://user-images.githubusercontent.com/111609994/192657833-737cc448-c8fe-4f8b-add5-2eb6480ea383.png">






