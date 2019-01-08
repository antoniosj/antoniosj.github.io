---
title:  "Securing your API Key on Android Projects"
date:   2018-05-04 10:00:00
categories: [android, kotlin]
tags: [android, api-key, gradle, kotlin]
---


<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;">So, I was woking on a company's project, and the customer who was paying this project asked for some security consulting, and those consultants found a few things to adjust. One of theses things were API KEYS under constants, variables and even manifest tags. This think had my attention because I used to see <span style="background-color: #DAE3FD">const val API_KEY = "YOUR_API_KEY_HERE"</span> in a lot of codes out there. Then I opened the Riot Developers <a href="https://developer.riotgames.com">page</a> to see how they treat this API_KEY question. Finally, this is what I found there (among other things):</p>

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;"><span style="background-color: #DAE3FD">Please don't publish a project that doesn't properly secure your API key</span></p>

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;">Yeah, a lot of projects don't worry about this, but it's a huge problem with people who uses third party APIs. So, I started to searching for solutions, and suddenly I found what I was looking for at Gradle's page. Basically you can put your API KEYs in <span style="background-color: #DAE3FD">gradle.properties</span> file, or even create your own properties file. This is ONE of the solutions:</p> 

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;">So, on your gradle.properties file, declare your key:</p> 

<img src="https://github.com/antoniosj/blog-examples/blob/master/Photos%20from%20blog/1_gradleproperties.png?raw=true"/>

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;">After that, go to your <span style="background-color: #DAE3FD">build.gradle (app)</span> and define a variable for your key:</p> 

<img src="https://github.com/antoniosj/blog-examples/blob/master/Photos%20from%20blog/2_gradle.png?raw=true"/>

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;">And that's it. Now you can put your variable in your manifest file:</p>

{% highlight swift %}

<meta-data
     android:name="io.fabric.ApiKey"
     android:value="${FABRIC_API_KEY}" />
     
{% endhighlight %}

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;">Or in your kotlin file:</p>

{% highlight swift %}
val retrofit = Retrofit.Builder()
                .client(client)
                .addCallAdapterFactory(RxJava2CallAdapterFactory.create())
                .addConverterFactory(EmptyBodyConverterFactory())
                .addConverterFactory(ScalarsConverterFactory.create())
                .addConverterFactory(GsonConverterFactory.create(GsonBuilder().create()))
                .baseUrl(BuildConfig.BASE_URL)
                .build()
{% endhighlight %}

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;">Basically is that. I changed all the API KEYs that I found on project's code and apparently solved my problem.</p>
