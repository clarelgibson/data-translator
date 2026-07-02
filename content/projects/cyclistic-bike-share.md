---
date: '2025-02-04T22:35:47Z'
draft: false
title: 'Cyclistic bike-share: a case study'
cover:
    image: img/cyclistic-banner.jpg
    alt: 'Modern stationary bicycles in gym with the Cyclistic logo'
    caption: 'Photo by [Maarten van den Heuvel](https://www.pexels.com/photo/modern-stationary-bicycles-in-gym-4254902/)'
categories: ['portfolio']
tags: ['data analysis', 'case study', 'tableau', 'data visualisation', 'data cleansing']
---

While taking the [Google Data Analytics Professional Certificate](https://www.coursera.org/professional-certificates/google-data-analytics), I worked on this data analysis as a capstone project.

## Objective
Cyclistic is a fictional bike-share company operating in Chicago, US. To unlock growth, Cyclistic wants to launch a campaign to convert casual riders into subscribed members. This case study explores the different ways that casual riders and members use Cyclistic, and offers recommendations of actions that could be taken to encourage conversions.

## Data

- 2024 trip data from [Divvy Bikes](https://divvy-tripdata.s3.amazonaws.com/index.html)

## Data analysis

The dataset comprised almost 6 million trips that took place in 2024 in the Chicago area. The ratio of members to casual riders is roughly 2:1.

{{< figure
  src="/img/cyclistic-key-facts.png"
  alt="Donut chart showing total number of trips analysed and split between casual riders and members"
  caption="Key facts about the analysis"
  align=center
>}}

I chose to look at trip duration, bike type and seasonality differences between the two groups in order to offer recommendations to Cyclistic.

### Trip duration

I found that casual riders take longer trips than members, especially in the summer time. Members have a consistent ride duration throughout the year. One reason for this could be that members are using their trips for a specific, routine purpose (such as commuting), whereas casual riders are riding for pleasure or exercise.

{{< figure
  src="/img/cyclistic-trip-duration.png"
  alt="Line chart showing median trip duration by month for casual riders and members"
  caption="Median trip durations for members and casual riders"
  align=center
>}}

### Bike type

I found that electric bikes are the most popular rideable for both members and casual riders. Electric scooters are more popular with casual riders, though their usage represents just 4% of all casual trips.

{{< figure
  src="/img/cyclistic-bike-type.png"
  alt="Column chart showing number of trips by type of rideable for casual riders and members"
  caption="Trips by ride type for members and casual riders"
  align=center
>}}

### Seasonality

During the summer months, the number of trips made by each group is roughly the same. But in winter, members outnumber casual riders by almost 9 to 1. Casual riders tend to ride at weekends and in the evenings, whereas members ride on weekdays with peaks both in the morning and the evening, reflecting a commute pattern.

{{< figure
  src="/img/cyclistic-seasonality.png"
  alt="Charts showing number of trips by month, weekday/weekend and time of day for casual riders and members"
  caption="Seasonality and time of day metrics for members and casual riders"
  align=center
>}}

## Recommendations

Based on my analysis, I offer two recommendations to the Cyclistic marketing team:

1. Choose a summer launch for your marketing campaign. Casual riders are more likely to use Cyclistic during the summer months so launching a campaign in May will coincide with peak demand.
2. Offer flexible subscriptions. Casual members may be deterred from subscribing because they don't ride as frequently. Consider off-peak subscriptions for rides starting after 9am, or weekend or summer-only subscriptions.

## Resources

- [Tableau Dashboard](https://public.tableau.com/views/CyclisticBikeShare_17374793232980/CaseStudy?:language=en-GB&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)
- [Github repository](https://github.com/clarelgibson/cyclistic-bike-share)