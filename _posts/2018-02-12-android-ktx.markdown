---
title:  "Android KTX"
date:   2018-02-12 15:04:23
categories: [android, kotlin]
tags: [android, kotlin, plugin, android-ktx]
---

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;"> Two weeks ago, Google announced a set of extensions designed to make writing kotlin code more concise, idiomatic and pleasant called Android KTX. The objective here seems to be help developers to write less code! You can check the repo of Android KTX <a href="https://github.com/android/android-ktx">here.</a></p> 

<img src="https://github.com/antoniosj/blog-examples/blob/master/Photos%20from%20blog/kotlin-android-learn.png?raw=true"/>


### Getting Started
<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;">To start using Android KTX you only need to put this on your <span style="background-color: #7CFC00">build.gradle</span>:</p>


{% highlight gradle %}
repositories {
    google()
}

dependencies {
    // Android KTX for framework API
    implementation 'androidx.core:core-ktx:0.1'
    ...
}
{% endhighlight %}


<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;">Now, lets start comparing kotlin with and without Android KTX:</p> 

**Shared Preferences**


{% highlight swift %}
sharedPreferences.edit()
           .putBoolean(key, value)
           .apply()
{% endhighlight %}     


**Shared Preferences with Android KTX**


{% highlight swift %}
sharedPreferences.edit { 
    putBoolean(key, value) 
}
{% endhighlight %}

**String to URI**

{% highlight swift %}
val uri = Uri.parse(myUriString)
{% endhighlight %}


**String to URI with Android KTX**


{% highlight swift %}
val uri = myUriString.toUri()
{% endhighlight %}


**Canvas**


{% highlight swift %}
val pathDifference = Path(myPath1).apply {
    op(myPath2, Path.Op.DIFFERENCE)
}
canvas.apply {
  val checkpoint = save()
  translate(0F, 100F)
  drawPath(pathDifference, myPaint)
  restoreToCount(checkpoint)
}
{% endhighlight %}


**Canvas with Android KTX**


{% highlight swift %}
val pathDifference = myPath1 - myPath2
canvas.withTranslation(y = 100F) {
    drawPath(pathDifference, myPaint)
}
{% endhighlight %}

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;">There's a lot of more places you can simplify your code. You can read the full documentation <a href="https://android.github.io/android-ktx/core-ktx/">here</a>. You can also <a href="https://github.com/android/android-ktx/blob/master/CONTRIBUTING.md">contribute</a> to Android KTX with new ideas, giving your feedback, reporting defects and requesting features.</p>



<iframe width="100%" height="315" align="middle" src="https://www.youtube.com/embed/kmvS3sZF_y0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>





### androidx


<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;">Google is now giving <span style="background-color: #7CFC00">androidx.</span> names to its prefix packages as you can see at Android KTX. It is because they have the intention to use it in their future versions of Android Support Library to differentiate which APIs are bundled with the platform and which are static libraries for app developers that work across differents versions of Android.</p>


	
