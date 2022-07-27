---
layout: post
title: "Creating a Viber bot in Poland with TextIt"
date: 2022-05-15
description:
image: /img/posts/20220515_intro.png
caption: ""
author: [Dan Joseph]
tags:
  - open source
  - TextIt
---

## A new channel for communications and engagement

I deployed for 10 weeks as the Information Management (IM) Coordinator to support the Polish Red Cross during the crisis in Ukraine and impacted countries. My colleagues designing a cash assistance program and figuring out how to ensure robust Community Engagement and Accountability (CEA) approached me about using technology to improve their information dissemination. To complement the pamphlets and other materials providing details about the program, they wanted an automated way to guide people through the FAQ and respond in-person to select individuals if warranted.

## A multitude of options

Advances in AI and natural language processing (NLP) have made it possible to build more intelligent chatbots that can respond to changes in language outside of a structured dialogue; however, setting one up that is helpful requires expertise, time, and effort. Improperly training an AI chatbot to understand context can result in a frustrating, or even harmful, user experience. We planned for a non-AI chatbot that would respond based on a set of rules we defined to route responses based on matching user responses to programmed answers. If a user asked a question we didn’t think of, the chatbot wouldn’t be able to provide an answer. It would be a more rigid and scripted experience, but one that I thought could still be positive for users while designed in less time with the resources and expertise we had readily available.

For a similar operational need in recent years, the IFRC Americas team created a WhatsApp business profile, opened the account on 2 laptops, and used human operators to respond to messages and log the interactions in a tracker spreadsheet. We expected that demand for our service might grow beyond the volume which that solution realistically supports. Their case study notes the possibility of integrating the WhatsAuto app to automate responses – however it does not appear this was tested and relies on a single phone serving as your "chatbot system" which I thought introduced an unacceptable failure risk for a program the size of ours.

I considered working with Surge Information Management Support (SIMS) - a global network of specialists in the Red Cross and Red Crescent that can provide remote support - to code something from scratch. However, I thought developing new software was not appropriate for the middle of a crisis response if not absolutely necessary and better tackled during ‘blue skies’ work. Additionally, the network has fewer software developers than GIS or data analysts, and having SIMS build something would introduce maintenance challenges, sustainability risks, and challenges in transferring the platform off between rapid response surge personnel deployments.

I asked around and tried a variety of search terms looking for existing platforms that might meet our needs. There were no shortage of ones to consider: Amazon Lex, B2Chat, Botkit, Botmother, Botpress, BotsForCharity, Botsify, Callbell, Collect.chat, Commbox, Dialogflow, Drift Bot, Flow XO, Gupshup, MessageBird, Microsoft Bot Framework, QnA Maker, Rasa, Respond.io, Rocket.chat, SAP Conversational AI, SendPulse, TextIt, Twilio Flex, WATI, Wit.ai, Xenioo, Yenasys, and Zendesk... just to name a few!

## Selecting TextIt

There was a lot to consider when evaluating platform options. Which messaging apps would the platform integrate with? We needed an integration with Viber, as it seemed to be the most commonly used messaging app among people from Ukraine. Flexibility in utilizing other messaging tools would be good. Would the platform provide analytics so that we could monitor how users were interacting with it? We would want to know how many people were using the service and what FAQ information was most popular. How accurately could we estimate the monthly cost for the platform? For planning purposes and to be good stewards of donor contributions we need to have known, predictable costs.

What would be the technical and financial implications of scaling on the platform? We would potentially have many thousands of users and needed to know if that would affect performance or cost. For example, some platforms charge based on the number of contacts, some charge based on the number of messages sent, and some charge based on a combination of the two. Would the process for updating or modifying the information delivered via the platform be challenging? We would need to update and adapt the information we were disseminating and it would be helpful to have that process be feasible for a wider range of staff and volunteers. Could we later integrate the platform with other tools? Some platforms make it easy to use third party tools if you want to expand functionalities or just use a tool you’re more familiar and comfortable with.

Some of the platform options were easy to rule out due to issues such as being prohibitively expensive, requiring a complicated and lengthy setup, or not integrating with Viber. From the others, I decided that [TextIt](https://textit.com/) was the best option. It stood out because of:

- Integration with a variety of communication tools including Telegram and Viber at no additional cost.
- A simple and reasonable billing structure. Each person interacting with your chatbot during a month is a "contact" and you are charged based on the number of contacts. We did not know it at the time, but TextIt was discounting plans for qualifying companies and organizations working on projects related to the humanitarian crisis in Ukraine which reduced our costs. Some services cost much more due to bundled features we had no plans to use.
- An understandable and accessible graphic interface for building the chatbot flow.
- A straight-forward interface for adding translations and offering a chatbot flow in multiple languages.
- An efficient, stand-alone setup process. Some platforms are intended to be heavily integrated within larger systems, such as a fully-fledged customer management system.
- Inclusion of basic analytics to monitor how and when people are interacting with the chatbot flow.
- Options for allowing users to open help tickets and a separate ticketing dashboard for our team to directly respond.
- Useful [video tutorials](https://textit.com/video/) and comprehensive [documentation](https://help.textit.com/).
- Software support. (TextIt support proved to be quick to respond and very helpful. During our early implementation we ran into a bug that they then fixed almost immediately after we flagged it! The bug prevented us copying and pasting messages from the ticketing dashboard; we sometimes needed to check messages in Google Translate before someone on the team with the right language skills could read and respond.)

![screen shot of a chat message from TextIt support about a software update](/img/posts/20220515_support.png)
<br><span class="post-caption">The TextIt team letting us know an issue we ran into had been fixed!</span>

I’ve written about our support for open source related to [our use of ODK](https://americanredcross.github.io/2021/04/14/embracing-open-source-survey-tools/). By using and sharing free and open source software within our global network, the costs of technology adoption can be lower. An added bonus of choosing TextIt is that it aligns with those values. In late 2014, The team behind TextIt partnered with UNICEF to expand on the capabilities of the proprietary TextIt software and release the source code as [RapidPro](https://github.com/rapidpro) under the [Affero GPL (AGPL) license](https://github.com/rapidpro/rapidpro/blob/main/LICENSE). TextIt remains the name of the paid hosting version of the open source RapidPro software - making it easy to support open source but get enterprise-level support so that you can focus on your program activities, not on running servers.

## Building the flow

In working with my colleagues to organize the information they wanted the chatbot to deliver, I ended up guiding them to use three levels of organization: category, topic, and question. Then each question had an informational message response. Information was organized so that an user was ideally presented with three to five options. We wanted to efficiently guide them to the information they needed, limiting the number of interactions needed and how much they needed to read. No one likes reading fifteen options and having the one you want be the fifteenth. We had a few questions that terminated with the option to open a ticket, which then let a human agent message with the user from a dashboard on the TextIt website.

I started the chatbot flow with a check to see if someone had interacted with it before and set a language preference. If they are a new user then they are asked to set a language. We authored the flow in English and translated it to Polish, Ukrainian, and Russian. After we know their preferred language, the user can choose one of three categories of information. Since a flow can easily get large enough that it is hard to manage within one layout, I split each category out into its own layout.

![screen shot from TextIt showing the opener flow for language preference and category selection](/img/posts/20220515_info-bot-flow.png)
<br><span class="post-caption">The opening flow that lets a user set their language preference and select a category of interest.</span>

![screen shot from TextIt showing the start of the "essential services" category flow](/img/posts/20220515_essential-services-flow.png)
<br><span class="post-caption">The start of the "essential services" category flow showing topics, questions, and information messages. </span>

Some pathways through the flow resulted in the option to open a ticket and then communicate with an agent. The agents included people who had fled Ukraine themselves and wanted to use their language skills volunteering with the Polish Red Cross to help others in the same situation.

![screen shot from TextIt of a flow just before triggering the flow to open a ticket](/img/posts/20220515_ticket-option.png)
<br><span class="post-caption">Giving the user an option to open a ticket at the end of a particular flow, in this case because they lost their PIN.</span>

Opening a ticket paused the automated flows and triggered an email alert to the volunteer agents.

![screen shot from TextIt of the flow to open a ticket](/img/posts/20220515_open-ticket.png)
<br><span class="post-caption">The TextIt flow that let a user open a ticket.</span>

To translate the messages, you can toggle the language in the top right of the flow build interface. Messages in the flow that still need to be translated are highlighted with a yellow fill and red text. However, if you change the main language wording after translations are finished you’ll need to manually track which translations need to be updated.  

![screen shots showing how a message in the flow is translated](/img/posts/20220515_translation.png)
<br><span class="post-caption">Messages (from left to right) in English, awaiting translation, and Ukrainian.</span>

The ticketing dashboard interface was simple but effective and met our immediate needs.

![screen shot of the basic ticketing GUI](/img/posts/20220515_ticketing-gui.png)
<br><span class="post-caption">The ticketing GUI available within TextIt.</span>

The built-in analytics dashboard let us analyze what time of day and day of the week had the most users, as well as track usage over time.

![screen shot of graphs and charts showing days and times users interacted with the bot](/img/posts/20220515_analytics-1.png)
<br><span class="post-caption">Analytics of the days and times when users were interacting with the bot.</span>

The dashboard also let us look at the distribution of responses in the flow. Here you can see that 12% of users requested the Russian version. Some 65% were not enrolled for cash assistance and interested in learning how to register.

![screen shot of graphs showing percentage responses for language and category selections](/img/posts/20220515_analytics-2.png)
<br><span class="post-caption">Analytics of the user choices for language and category selections.</span>

## Future thoughts

In addition to the FAQ and help ticketing, there were several other interesting workflows designed using TexIt. For one, we had a long list of people and phone numbers but wanted to connect with people on Viber, not SMS. To message someone from a Viber bot requires them to initiate the communication. We designed a way to upload the list of contacts to TextIt along with a unique code for each one. It was then possible to use Twilio to send a one-time SMS to each person with a unique link. The link opened a conversation in Viber prepopulated with the code. After the recipient hits send, the code can be used to match their Viber account to the record in TextIt of the account with that phone number. TexIt had a tutorial related to this [for Telegram](https://help.textit.com/en/article/bringing-your-sms-contacts-over-to-telegram-xy116a/). We found that Android devices will not open deep links (the kind of link that opens another app on the phone) from an SMS message, so we developed [a workaround](https://github.com/IFRCGo/pck-referral) where we could link them to a website to click the customized deep link. It was a bit convoluted but a fun deep-dive into several technologies trying to solve a series of challenges.

TextIt proved to be a success and what I set up in Poland was continued there, as well as replicated in other countries that were part of the overall response operation. Subsequent rounds of personnel deployed for IM support to the operation in Poland were able to expand the use of TextIt to survey people to check their eligibility for the cash support program, then invite eligible people to an in-person registration and distribution.

When exploring new processes, any new process, not just ones using TextIt, it is important to explore in a manner that does not turn people’s vulnerabilities during a crisis into a laboratory. We need to ensure that there are other ways for people to get the same information and services, or provide feedback. In trying to stay safe online, many people may (rightly) be wary of digital communications providing information or promising disaster relief. The use of technology in programs can inadvertently exclude vulnerable segments of the population that are important to reach. Marginalized groups may avoid certain technologies due the risks of government surveillance. Older people may have difficulties with newer technology. The cost of certain technologies, such as the cost of a smartphone or even just internet access, can be a barrier for people especially after a crisis in which they may have lost financial resources and belongings.

I think TextIt can add value to other operations. It can enable reaching people on an app that they are already using and comfortable with. That might be useful in a situation where you are reaching out to someone digitally and not training enumerators. I look forward to exploring TextIt and related technologies to improve our humanitarian programs.

![screen shots of a chat exchange with the Viber bot](/img/posts/20220515_chat-example.png)
<br><span class="post-caption">An example exchange with the Viber bot.</span>
