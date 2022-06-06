---
layout: post
title: "Mapping the knowledge-building of a global network"
date: 2021-04-19
description:
image: /img/posts/20210419_website.png
caption: Advancing the humanitarian mission through evidence and learning
author: [Nesrine Aouinti, Dan Joseph]
tags:
---

_<span class="cross-post">This was originally posted as a story on [Prepare Center](https://preparecenter.org/story/mapping-the-knowledge-building-of-a-global-network/).</span>_

## Why we’re mapping research

As a member of the [Red Cross Red Crescent Research Consortium (RC3)](https://media.ifrc.org/ifrc/rcrc-consortium/), the Global Disaster Preparedness Center (GDPC) developed a [mapping](http://research.preparecenter.org/) of past and current research activities, studies, and academic papers supported by consortium members. The supported research activities, when considered as a whole, would rival the bodies of work of many universities, academic and research institutions.

The inspiration behind this mapping came from the observation that the Red Cross Red Crescent global network generates a wealth of knowledge on a variety of subjects but there was no comprehensive understanding of that expertise. The mapping will help leverage the expertise and provide a better view of the big picture.

We are deeply committed to expanding an evidence base and investing in new knowledge. We hope that sharing learning across our networks, both internal and in the wider humanitarian community, is a valuable contribution towards our goal to achieve a greater humanitarian impact based on an evidence-based culture and optimized resources.

## Inspiration For Continued Sharing

Since maps are a representation of the real world on a much smaller scale, we were able to broaden our understanding of the variety and distribution of our network’s research around the world. We ask our partners and colleagues to share as much information as possible about a project including funding sources, type of research, research focus, lead organization, country or region of study, status, and language. Whenever possible we include links to the research findings. Nesrine Aouinti, Knowledge Management Fellow at the GDPC shares her insights:

> During the mapping process, we were both inspired and heartened by the receptiveness of our colleagues. The map resonated with their individual efforts to work in synergy with other humanitarians. They find the map to be a practical and simple tool to quickly find connections between their own work and the work of others. This demonstrates once again that easily accessible and shared knowledge is a powerful asset for the humanitarian sector, now and into the future.

## Visualizing the mapping

### Open source building blocks for websites

We needed a fast and inexpensive way to let people explore the data. Using open source tools we could quickly develop an interactive site and start gathering more feedback from users on what is useful for them. Github is a platform for software development that offers free hosting for basic website projects. [Github Pages](https://pages.github.com/) is a dependable and easy way to quickly get a website live. To build the website we used HTML/CSS and JavaScript and a number of open-source technologies: [Bootstrap](https://getbootstrap.com/) to help create the layout and style of our page; [Leaflet](https://leafletjs.com/) to display the map, and [dc.js](https://dc-js.github.io/dc.js/) to render the graphs (which utilizes [Crossfilter](https://crossfilter.github.io/crossfilter/) and [d3.js](https://d3js.org/) under the hood). The final step was to create a subdomain of the GDPC website so that our page is available at [research.preparecenter.org](https://research.preparecenter.org/) instead of the default Github Pages URL of americanredcross.github.io/research-mapping.

### Simple data storage and simple updates

A Google Spreadsheet can be a great place to collaborate on a dataset, and it used to be possible to pull data directly from Google Sheets into your webpage for visualizations using a nifty tool called [Tabletop.js](https://github.com/jsoma/tabletop). Unfortunately, Google discontinued the infrastructure that made that possible but we did find a [workaround](https://github.com/AmericanRedCross/google-sheets-workaround) of running a script to download the data and save it somewhere that is accessible to the wider web. With this hack we can continue using a Google Spreadsheet for the data behind the research mapping website, we just connect to a copy of the data stored on [Github](https://github.com/AmericanRedCross/google-sheets-workaround/blob/gh-pages/research-mapping.csv) that is updated every 24 hours. This process makes it easy to update the research map data; if someone can edit a Google Sheet they can add and update the research entries on the website - no code required!

![An automated build process pulls in any updates from the Google Sheet to the website every 24 hours.](/img/posts/20210419_build-process.png)
<br><span class="post-caption">An automated build process pulls in any updates from the Google Sheet to the website every 24 hours.</span>
