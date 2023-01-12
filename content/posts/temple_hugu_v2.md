---
title: "Temple_hugu_v2"
description:
date: 2022-05-26T18:45:50+03:00
draft: false
tags: [hugo]
---


Date Format
Hugo's date format quirks and gotchas
Published: Saturday, 27 June 2020
By: Chelsie Woon
Incorrect dates appeared when we used Hugo’s date .Format function.

The example that was given on the Hugo website was

{{ .PublishDate.Format "January 2, 2006" }} => March 3, 2017
Where January 2, 2006 is the layout string, and PublishDate has value 2017-03-03 and will display as March 3, 2017. The layout string must use a specific reference time for date formatting.

The reference date time
Mon Jan 2 15:04:05 MST 2006
The valid inputs for formatting:

day of the week: Mon, Monday
day of the month: 2, _2, 02 (unpadded, space-padded, zero-padded)
month: Jan, January, 1, _1, 01
year: 06, 2006
For example, if we have date = 2020-06-27T08:55:23+01:00
We wish to display it as dd/MM/YYYY hh:mm:PM
We can use:

{{ .Date.Format "02/01/2006 15:04PM"}}
This gives us the output 27/06/2020 08:55AM

The reference date can be remembered as: