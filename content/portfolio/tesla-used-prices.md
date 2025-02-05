---
date: '2023-05-25T12:23:12Z'
draft: false
title: 'Tesla used prices'
cover:
    image: img/tesla-16x4.png
    alt: 'Photo of a white Tesla Model 3 on the road'
    caption: 'Photo by [David Gari](https://www.pexels.com/photo/white-tesla-model-3-car-on-road-9300916/)'
tags: ['tesla', 'dashboard', 'tableau']
categories: ['portfolio']
---

*An interactive and dynamic dashboard that monitors UK Tesla inventory. The Tesla Model 3 dashboard allows users to monitor the current inventory of used Model 3 vehicles in the UK, view data on price, mileage and age, and create a shortlist of available vehicles matching specific criteria. Data is refreshed daily.*

- [Tableau dashboard](https://public.tableau.com/shared/KDN922ZCZ?:display_count=n&:origin=viz_share_link)
- [Github repository](https://github.com/clarelgibson/tesla-inventory)

## The story
The lease on my current car (a [Renault Zoe](https://www.renault.co.uk/electric-vehicles/zoe.html)) is set to end in January 2024. I have loved driving an electric car over the past two and a half years, and when my lease ends I know I want to continue driving electric. However, this time I want to buy rather than lease, and I want something different to a Zoe.

When I discovered that [used Tesla prices had taken a plunge recently](https://www.thisismoney.co.uk/money/electriccars/article-11619661/Used-Tesla-values-come-crash-Prices-18k.html), I decided to investigate the Model 3 as a possible contender for my next car. When I further discovered that the [entire Tesla inventory data is freely available via an API](https://realize.net/tesla-inventory-stock/), I immediately saw a new data project.

The dashboard shows all used Tesla Model 3 vehicles that in stock as of 19th June 2023 according to [Tesla.com](https://www.tesla.com/en_GB/inventory/used/m3). You can see the location of each vehicle on the map and the distribution of and relationship between price, mileage and age (which helps to spot outliers). Finally, I built in a shortlist feature, which allows you to specify the criteria of your ideal car and see how many matching vehicles are in stock.