---
date: '2023-11-03T21:40:24Z'
draft: false
title: 'The seven bins of St Helens'
cover:
    image: img/recycling.jpg
    alt: 'A group of household recyclable materials on a kitchen counter'
    caption: 'Photo by [SHVETS production](https://www.pexels.com/photo/woman-selecting-glass-into-plastic-container-7512859/)'
categories: ['portfolio']
tags: ['tableau', 'case-study', 'recycling']
---

*Are seven bins more effective than one? In this case study, I explore the answer to this question using public data on recycling rates by local authority in England.*

- [Tableau dashboard](https://public.tableau.com/views/BinBurdens/BinBurdens?:language=en-GB&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)
- [Github repository](https://github.com/clarelgibson/uk-recycling)

## Situation
Last week I took my son to visit my parents for the half-term break. They live in St Helens, a town in Merseyside, north-west England. One evening while I was there, the conversation turned to the new recycling bag that the council had just issued to every household in the borough. Despite our Prime Minister's recent promise that [he will never allow 'seven bins' per household](https://www.mrw.co.uk/news/government-will-never-allow-seven-bins-per-house-says-sunak-20-09-2023/), it seems that is exactly what [St Helens Borough Council is doing](https://www.sthelens.gov.uk/article/9028/Recycling-Service-Change). The new 70L green bag that my parents received brings their total household waste receptacle count to exactly seven:

- **Green bag** for cardboard
- **Blue bag** for paper
- **Black box** for glass
- **White bag** for plastic and cans
- **Grey caddy** for food waste
- **Green bin** for garden waste (a subscription service)
- **Brown bin** for general and non-recyclable waste

This system of recycling, called [kerbside sort or multi-stream](https://en.wikipedia.org/wiki/Kerbside_collection#United_Kingdom), puts the burden of sorting the recyclable material on the resident. As my mum can attest, it is pretty onerous and sometimes confusing to work out what belongs in each bin or box, and when they each have to be put out for collection. In other parts of the UK, including in Waverley, where I live, the local authority employs a [co-mingled recycling](https://en.wikipedia.org/wiki/Single-stream_recycling) system, where all of the non-organic recyclable material is put into a single bin and the sorting takes place at a [Materials Recovery Facility](https://en.wikipedia.org/wiki/Materials_recovery_facility).

## Question
> **Do councils who employ a kerbside sort system achieve higher recycling rates than those who employ the co-mingled system?**

Mum and I looked up the latest recycling rates for Waverley and St Helens and were surprised to discover that St Helens, with its [multi-stream system](https://en.wikipedia.org/wiki/Kerbside_collection#United_Kingdom), recycled just **36.8%** of household waste in FY2021/22, compared to Waverley, with its [co-mingled system](https://en.wikipedia.org/wiki/Single-stream_recycling) which achieved **58.9%** in the same period (source: [Defra](https://www.gov.uk/government/statistical-data-sets/env18-local-authority-collected-waste-annual-results-tables-202122)).

## Methodology
To answer the question, I collected data about recycling systems and rates for all 309 local authorities in England in 2021. Recycling rates for each local authority are published by [Defra](https://www/defra.gov.uk) using the [WasteDataFlow](https://www.wastedataflow.org/home.aspx) web-based reporting system. At the time of conducting this research, the most recent figures available were for the 2021-2022 financial year. Recycling rates were calculated by taking the volume of household waste sent for recycling, composting or reuse by the total volume of household waste collected. Non-household waste was not included in this research.

Details of the type of recycling system in place (co-mingled, two-stream or multi-stream) in each local authority were not easily available. I could not find a public data source for this information, so I took a two-pronged approach to obtain it. First, I launched a [Google Forms survey](https://docs.google.com/forms/d/e/1FAIpQLSeppOvUryPiswe9vXgp2kO-8jdZSwrUkCNC73NzOk0BkzmF7A/viewform?usp=sf_link), which asked respondents to provide the name of their local authority, whether they had household or communal waste collection and how many containers they had for recyclable materials. I launched the survey within my social networks and on [SurveyCircle](https://www.surveycircle.com). In parallel, I submitted a Freedom of Information (FOI) request to Defra to obtain the data. The survey collected 41 responses and provided some interesting insights into peoples' thoughts and concerns with their recycling collections. Ultimately, the FOI request provided me with a consistent and verified source of the data I needed. I have published the results and data from the FOI request [here](https://docs.google.com/spreadsheets/d/1M36p2m3Y59JvwW-a8sD-xXGADIkoe10N/edit?usp=share_link&ouid=110132729826719978887&rtpof=true&sd=true).

## Data overview
My dataset consists of recycling data from 309 local authorities in England. Of these, 157 use a co-mingled system, 112 use a two-stream system and 40 use a multi-stream system.

{{< figure
  src="/img/data-overview.png"
  alt="Bar chart showing that 157 local authorities use the co-mingled system, 112 use a two-stream system and 40 use a multi-stream system"
  caption="Data overview"
  align=center
>}}

## Key findings
Local authorities employing a co-mingled system achieved a median recycling rate of 40.3%, while those employing two-stream or multi-stream systems achieved higher rates of 44.3% and 44.5% respsectively. This indicates a difference in recycling rates in favour of one of the kerbside sort systems. It is interesting to note that the local authority with the highest recycling rate in 2021 was Three Rivers (63.5%), which uses a co-mingled system. The lowest performer overall was Barrow-in-Furness (17.7%), which uses a two-stream system.

Looking specifically at Waverley and St Helens, we see that Waverley is one of the top performers amongst co-minglers and St Helens is one of the bottom performers among multi-streamers.

{{< figure
  src="/img/key-findings.png"
  alt="Box plots showing the distribution of recycling rates for each local authority, grouped by the type of system that they use"
  caption="Key findings"
  align=center
>}}

## Discussion
The higher recycling rates in kerbside sort systems could be attributed to better sorting at source, leading to cleaner recyclables. Additionally, community awareness and engagement may play a role. However, as the data shows, local authorities using a co-mingled system can and do achieve high recycling rates, with less burden on the householder.

## Limitations
It is important to note that my research focussed only on data from a single financial year and is only applicable to local authorities in England. Furthermore, the analysis does not account for differences in the materials collected for recycling in different local authorities. For example, some local authorities provide a separate collection for food waste, meaning that food waste controbutes to the overall recycling rate. Others advise that food waste should be co-mingled with other non-recyclable household waste, meaning that food waste does not contribute to the recycling rate. Some authorities do not offer any kerbside collection of glass, instead asking householders to take their glass to a bottle bank. If householders do not have the means to access a bottle bank, they may choose to dispose of their glass waste with the general household waste. Since my analysis relies on available data, variations in local policies or population density might influence the results.

## Conclusions
In conclusion, my analysis suggests that local authorities with kerbside sort systems tend to achieve higher recycling rates than those with co-mingled systems. However, where employed well, co-mingled systems do have the potential to achieve high recycling rates. Further research is needed to understand the wide range of recycling rates among local authorities employing the co-mingled system, and to understand what factors are associated with higher recycling rates.