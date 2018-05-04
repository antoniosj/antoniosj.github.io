---
title:  "Securing your API Key on Android Projects"
date:   2018-05-04 10:00:00
categories: [android, kotlin]
tags: [android, api-key, gradle, kotlin]
---

So, I was woking on a company's project, and the customer who was paying this project asked for some security consulting, and those consultants found a few things to adjust. One of theses things were API KEYS under constants, variables and even manifest tags. This think had my attention because I used to see `const val API_KEY = "YOUR_API_KEY_HERE"` in a lot of codes out there. Then I opened the Riot Developers page {link soon} to see how they treat this API_KEY question. Finally, this is what I found there (among other things):

`Please don't publish a project that doesn't properly secure your API key`

Yeah, a lot of projects don't worry about this, but it's a huge problem with people who uses third party APIs. So, I started to searching for solutions, and suddenly I found what I was looking for at Gradle's page. Basically you can put your API KEYs in `gradle.properties` file, or even create your own properties file. This is ONE of the solutions: 

{soon}

