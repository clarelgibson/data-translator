---
date: '2025-04-03'
draft: true
title: 'Switching from Momento to Day One'
cover:
    image: img/momento-to-day-one.png
    alt: 'Momento logo links to Day One logo with an arrow'
tags: ['journal']
categories: ['blog']
---

For the past few years, I have been keeping a private, digital journal of photos and stories about what we have been up to as a family. Currently, I use an app called [Momento](https://momentoapp.com) for this, but I have been looking around for a better option. I have been trialling a product called [Day One](https://dayoneapp.com) for a few days now and I believe it offers several significant advantages over Momento:

| **Feature** | **{{< colour "#c26c2e" >}}Momento{{< /colour >}}** | **{{< colour "#6fbef7" >}}Day One{{< /colour >}}** |
|:------------|:-----------------------------------------------|:----------------------------------------------------|
| **Supported devices** | Phone only (iOS or Android) | Multiple platform support |
| **Syncing** | No sync | Syncs to Day One cloud |
| **Sharing** | Not supported | Share journals with people you choose |

Having seen the benefits that Day One can offer, my next step is to transfer all of my journal entries from Momento to Day One. Since there doesn't seem to be a help guide dedicated to this, I decided to document how I did this. Maybe this will be helpful to someone else.

## My setup

Since this whole process is device- and OS-specific, I'll provide details on my own setup. This article is written for an audience with a similar setup.

* iPhone 13 Pro running iOS 18.3.2
* MacBook Air M4 running macOS Sequoia 15.4
* **{{< colour "#c26c2e" >}}Momento{{< /colour >}}** Premium subscription (see [note on Momento](#some-notes-on-momento) below)
* **{{< colour "#6fbef7" >}}Day One{{< /colour >}}** Premium subscription

## Before you start

Transferring data from **{{< colour "#c26c2e" >}}Momento{{< /colour >}}** to **{{< colour "#6fbef7" >}}Day One{{< /colour >}}** is a multi-step process:

1. Export data out of **{{< colour "#c26c2e" >}}Momento{{< /colour >}}**
2. Process the data so that it is in the correct format for importing into **{{< colour "#6fbef7" >}}Day One{{< /colour >}}**
3. Import the data into **{{< colour "#6fbef7" >}}Day One{{< /colour >}}**

### Some notes on **{{< colour "#c26c2e" >}}Momento{{< /colour >}}**

**{{< colour "#c26c2e" >}}Momento{{< /colour >}}** only allows users to export data if they have a premium (paid-for) subscription. You can't export your data on a free subscription. If, like me, you have only ever used the free version, you might not like the idea of effectively having to pay to leave, but there is a small workaround: when you sign up for a subscription you get a month for free. I took advantage of the free trial month and used that time to export all of my data. If you do this, just don't forget to cancel the subscription before the free trial ends.

Furthermore, **{{< colour "#c26c2e" >}}Momento{{< /colour >}}** only provides export files in text format

### Some notes on **{{< colour "#6fbef7" >}}Day One{{< /colour >}}**

**{{< colour "#6fbef7" >}}Day One{{< /colour >}}** has a [helpful guide](https://dayoneapp.com/guides/settings/importing-data-to-day-one/#MacOS) to importing journal entries. It allows multiple formats for import but beware, not all formats can be used on all platforms. For example, [CSV import](https://dayoneapp.com/blog/help_guides/importing-data-from-csv/) can only be done through iOS. And not all import formats achieve the same results. For example, if you want to import your media (images and video clips) as well as your text you will need to use a [JSON format](https://dayoneapp.com/blog/help_guides/importing-data-from-json-files/) as this is not achievable with a CSV import.

## Exporting data from **{{< colour "#c26c2e" >}}Momento{{< /colour >}}**

The basic process of exporting data from **{{< colour "#c26c2e" >}}Momento{{< /colour >}}** is detailed [here](https://momento.zendesk.com/hc/en-us/articles/207965865-Export-FAQ) and also available within the app itself. However, I found the instructions unclear in some places, so here are a few additional tips from me:

* Exports seemed to work best when they were no more than 5GB in size. This might take a bit of trial and error but for me, this meant I needed to prepare my exports in batches of one year at a time. I was including media (images and videos) in my exports, which made the file sizes large. If you are only exporting the text, you will likely be able to do everything in one batch.
* When you tap on **Create Export** the export file is generated and a link appears within the app like this:

{{< figure
  src="/img/momento-export-created.png"
  alt="An export that has been created through the Momento app"
  caption="Export file created in Momento app"
  align=center
  width=350
>}}

* Tap on the export file and you will be asked if you want to share it. Tap on **Share**.
* Choose the option to **Save to Files** and choose a location in your iPhone files to save it.
* Once you have saved the export file to your phone, you can transfer it to a laptop for further processing using AirDrop or your preferred method.

## Processing the data

Once you have the export from **{{< colour "#c26c2e" >}}Momento{{< /colour >}}** you will need to manipulate it into a format that can be accepted for import by **{{< colour "#6fbef7" >}}Day One{{< /colour >}}**.

The **{{< colour "#c26c2e" >}}Momento{{< /colour >}}** export process produces a .txt file with the following structure:

```
20 July 2010
============

10:05
We had an awesome day at the theme park today!
Media: F6E39CC8-BCF8-4310-8E63-369C9B833FC2_original.jpg

10:30
The rides were wild and scary.

15 July 2010
============

09:04
Today it was time for a trip to the museum.
At: Natural History Museum, Cromwell Road, South Kensington (51.496727, -0.176484)
Media: 6EEB86F3-29C5-4D91-91F0-7CA5BA744230_original.jpg
```

This format is not one that can be accepted for import by **{{< colour "#6fbef7" >}}Day One{{< /colour >}}** so you will need to process this .txt file into either CSV ot JSON format. My recommendation would be to use CSV if you are not including media (and you have an iPhone) and JSON if you want to include media. There are, of course, many ways you can automate the transformation into the required format. I wrote a script in R to process my data. You can access it on [GitHub](https://github.com/clarelgibson/momento-to-day-one).

### Tips for converting to CSV

* The full list of accepted fields for CSV import can be found [here](https://forums.dayoneapp.com/forums/topic/csv-file-format/).
* `date` and `text` are the only required fields for the CSV import. All other fields are optional.
* `date` must be provided in ISO 8601 format, including 3 decimal places for milliseconds, like this: `2017-02-25T10:54:00.000Z`.

### Tips for converting to JSON

* I haven't done this yet. Check back soon.

## Importing data into **{{< colour "#6fbef7" >}}Day One{{< /colour >}}**

Be aware that when you import entries into **{{< colour "#6fbef7" >}}Day One{{< /colour >}}** they will be added to a new journal called **Export**. According to the **{{< colour "#6fbef7" >}}Day One{{< /colour >}}** help chatbot, "there isn't an option to directly specify an existing journal for the import. You would need to manually move the entries to your desired journal after the import is complete."

Manually moving the entries isn't so bad, since there is an option to select all and move all of the entries in one go.

### CSV

This can only be done through the iOS app.

### JSON

* I haven't done this yet. Check back soon.