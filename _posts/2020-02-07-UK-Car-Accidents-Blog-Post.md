---
layout: post
title: UK Car Accidents Project

image: /img/1024px-Flag_of_the_Governor_of_Hong_Kong_(1959–1997).svg.png
---

![Car Accident Stock Illustration.jpg](/img/Car Accident Stock Illustration.jpg)

## Introduction
Traffic accidents are a risk that many of us encounter in our everyday lives. It is a sad reality that every time we step outside near a road, or commute to work there is a chance that we will be impacted by one. A person does not even have to be in a car to be affected.

But what is it that determines how severe a car accident will be? I decided to take a look at car accident reports in the United Kingdom to see if we can find anything interesting.


![UK Flag Car.jpg](/img/UK Flag Car.jpg)

## Predicting Car Accidents in the United Kingdom
The United Kingdom's Department for Transport does a pretty good job of keeping track of information regarding road safety. The official statistical publication on traffic casualties, fatalities, and related road safety data is called the Reported Road Casualties Great Britain. The data collection method is based primarily off of STATS19, an accident reporting form and format that has been in use since 1926. 

![car_insurance_2765235.jpg](/img/car_insurance_2765235.jpg)
## Our Data
The datasets that we are using are for the year of 2018. There are 3, one pertaining to accidents, casualties, and vehicles respectively. In order to develop a logistic regression model the accidents and vehicle datasets were joined. 

![Tis But a Scratch.jfif](/img/Tis But a Scratch.jfif)
## The Goal
My goal was to develop a model that could predict how severe a car accident would be based off of various criteria. the 3 levels of severity are 1 for a car accident with a fatality, 2 for a car accident with a serious injury, and 3 for a car accident with only slight injuries. 

The correlation table shows that accident severity does not strongly correlate with any particular feature
![Accidents and Vehicles Variables Correlation.png](/img/Accidents and Vehicles Variables Correlation.png)


The majority classifier baseline came up with level 3 car accidents at 81.3% of the time. 

Using a decision tree I was only able to ever get the accuracy as high as 71.31%. Even tuning it with hyperparameters it only got as high as 80.23%.

The logistic regression model did much better, reporting an accuracy of 81.15%. It was just barely beaten out by the random forest model, with an accuracy of 81.29%.

Unfortunately, as much as I tried, none of the models were able to beat the baseline. 

## Results
Despite not being able to beat the baseline, we were able to gleen quite a lot of information about what determines the severity of a car accident (at least within the United Kingdom)

It looks as though Thursday is the day of the week that has the most accidents. It is closely followed by Wednesday & Tuesday. It is interesting that the 3 days that are in the middle of the work week are the days that are most affected.
![Car Accident Count Day of the Week.png](/img/Car Accident Count Day of the Week.png)


For the hour of the day, 6:00pm GMT is the time that you want to avoid if you do not want to get into a car accident. 5:00, 4:00, and 7:00 pm are not very safe either.
![Car Accident Count Hour of the day.png](/img/Car Accident Count Hour of the day.png)


For the age range of the drivers, it is overwhelmingly 26 - 35 year olds that get into car accidents. The next closest group, 36 - 45 year olds, trails behind quite far.
![Age Range of People Car Accidents.png](/img/Age Range of People Car Accidents.png)


We can also see that surprisingly car accidents occur overwhelmingly in areas where the speed limit is 30 miles per hour, coming in at 65.1%. The next speed zone with the highest percentage of accidents was 40 miles per hour, and it only experiences 10.3% of the country's accidents.
![Car Accidents Speed Zones.png](/img/Car Accidents Speed Zones.png)


And of course, we have to look at feature importance.
![Feature Importance Car Accidents.png](/img/Feature Importance Car Accidents.png)


Unsurprisingly, the age of the driver and the age of the vehicle were in the top 5, as 3 & 4 respectively. It is easy to see how the experience and physical capabilities associated with a person's age can affect the outcome of a car accident. 

Interestingly Engine Capacity and Local Authority District came in as the number 1 & number 2 features that affect the severity of a car accident. 

Engine capacity in this case is most likely relating to the size of the car, with a larger capacity equating to a larger vehicle. 

The Local Authority is referring the to local government that is in charge of the roads and road safety of a given area. It would seem that a local government's ability to properly maintain roads, signage, and general road safety measure has a very large impact on the severity of an accident.

## Interpretations
The United Kingdom has a lot of car accidents. Thanksfully, a vast majority of them result in little to know injuries for the people involved. But if you want to avoid an accident, it looks like you will want to avoid driving on a 30 MPH road around 6:00pm GMT on a Thursday in that old VW Beetle in that dodgy part of town.

Instead, consider driving on a 70 mph road around 4:00am GMT on a Saturday in a relatively new, large engine capacity car in an area where the local government has done a good job maintaining the roads. 

Drive safe!
