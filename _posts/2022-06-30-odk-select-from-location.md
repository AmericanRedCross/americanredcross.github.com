---
layout: post
title: "Enhancing \"select from map\" data collection in ODK"
date: 2022-06-30
description:
image: /img/posts/20220630_odk-map.jpeg
caption: "A phone running a survey in ODK Collect showing the new \"select one from map\" widget."
author: [Dan Joseph]
tags:
  - open source
  - ODK
---

## Early explorations into collecting geographic data with mobile data collection tools

When the American Red Cross first explored how to use mobile data collection tools for creating and improving OpenStreetMap data we looked to ODK. At the time, the required technology underpinning such functionality was not widely established and the core ODK software didn’t have the right pieces for us to directly invest in it. So in 2015 we built OpenMapKit as a companion app to ODK that enabled structured surveys on OSM building features. We used it during mapping projects with other National Societies, and it was also utilized in the wider humanitarian mapping community including extensively by the Humanitarian OpenStreetMap Team (HOT). A lot in the mobile app and mapping technology landscape has changed in the last 7 years, and it is no longer viable to maintain OpenMapKit.

## Collecting data linked to places using ODK

ODK is still a global standard for data collection. It is the Land Cruiser of data collection: reliable, tough, easy to use, customizable, and proven. ODK is synonymous with mobile data collection for many people. Being open-source makes it widely accessible and increases its impact by allowing it to serve as the foundation for other tools such as the popular Kobo Toolbox.

A diverse group of users and developers make up the ODK community; part of what makes ODK so great is how readily they collaborate and cooperate. The roadmap charting the future of the ODK project is formed in large part from the conversations that occur on the community forum, as well as collaborative processes that help the core maintainers ensure the technical feasibility of ideas, check assumptions, and confirm compatibility with the larger ecosystem.

A key piece of the roadmap for ODK is the enablement of stronger entity-based data collection workflows - leveraging the information collected about a specific person, place, or thing through repeat surveys instead of having each survey exist in isolation of the others. It is planned that geo will be central to these workflows.

## Helping build the future of geographic data collection

The American Red Cross was able to support improving entity-based data collection workflows in ODK, specifically the "select from map" functionality. This functionality in ODK will replace, and surpass, what we designed OpenMapKit to do; it will do it without the complexities and costs of maintaining a separate app. The functionality will allow an enumerator to select an item from a map, with the mapped items being pre-defined by the survey managers. The survey can then include pre-populated data linked to the item, and link whatever answers are provided during the rest of the survey to that particular location.

We funded several items that complement other development work, advance the ODK roadmap, and align with our priorities around improving data collection workflows for humanitarian purposes. The work includes:

1. Improvements "under the hood" to the performance of the map component in ODK so that it continues to function smoothly even when a survey includes a large number of geographic features.
2. Upgrades which pave the way for enabling users to specify styling for individual features (expected for fall). This means for example that if you are collecting data on health infrastructure you could style pharmacies green and hospitals blue.
3. Improvements to the user experience when viewing the properties of a feature so that a user can more easily check a list of the existing attributes, even if it is a large number of attributes.

## Far-reaching impact

Improving geographic centered, entity-based data collection workflows in ODK has exciting implications for every humanitarian that uses ODK, including for programs across the Red Cross and Red Crescent global network.

- When monitoring vaccination campaigns and conducting education outreach it will be easier to link a survey to the specific building in which a family resides, and easier to direct enumerators to the right place for follow-up visits.
- Volunteers will be able to more accurately collect details about point-of-interest features during assessment, community mapping, or other data activities.
- We will be able to improve the level of spatial data detail available for at-risk communities so that we can leverage anticipatory action/ forecast-based action and other data-driven processes.
- We will be able to more effectively conduct base-line and end-line surveys that require visiting specific households.
- We will have an adaptable tool for monitoring recovery projects such as the reconstruction of houses or water infrastructure.

Improvements to ODK reach the global ODK community covering many sectors from public health to climate monitoring, and includes the IFRC Secretariat and a multitude of National Societies.

## Working with Get ODK

We worked with the folks at Get ODK Inc to implement the improvements. Get ODK is the company behind ODK and they have invested significant time and energy in developing and maintaining the various ODK components. All of their work is done under the project’s open-source license so that anyone can use the technology. Given their years of work on ODK and long-running support of the project, they made an ideal partner. If your organization wants trusted professional support to use ODK, they offer an official, managed hosting service called [ODK Cloud](https://getodk.org/).

## Learn more

Learn all about ODK using the comprehensive [documentation](https://docs.getodk.org/). Chat with others on the [community forum](https://forum.getodk.org/). Follow ODK on [Twitter](https://twitter.com/getodk) or [LinkedIn](https://www.linkedin.com/company/getodk/). We’d love to hear your thoughts about what to prioritize next for more powerful mobile data collection workflows!
