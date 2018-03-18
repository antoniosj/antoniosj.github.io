---
title:  "Android KTX"
date:   2018-02-12 15:04:23
categories: [Android, Kotlin]
tags: [android, kotlin, plugin, android-ktx]
---

<img src="https://github.com/antoniosj/blog-examples/blob/master/Photos%20from%20blog/kotlin-android-learn.png?raw=true"/>



Two weeks ago, Google announced a set of extensions designed to make writing kotlin code more concise, idiomatic and pleasant called Android KTX. The objective here seems to be help developers to write less code! You can check the repo of Android KTX [here](https://github.com/android/android-ktx). 
{: .text-justify}

### Getting Started
To start using Android KTX you only need to put this on your `build.gradle`:


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


Now, lets start comparing kotlin with and without Android KTX: 

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



There's a lot of more places you can simplify your code. You can read the full documentation [here](https://android.github.io/android-ktx/core-ktx/). You can also [contribute](https://github.com/android/android-ktx/blob/master/CONTRIBUTING.md) to Android KTX with new ideas, giving your feedback, reporting defects and requesting features. 
{: .text-justify}




<iframe width="100%" height="315" align="middle" src="https://www.youtube.com/embed/kmvS3sZF_y0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>




### androidx


Google is now giving `androidx.*` names to its prefix packages as you can see at Android KTX. It's because they have the intention to use it in their future versions of Android Support Library to differentiate which APIs are bundled with the platform and which are static libraries for app developers that work across differents versions of Android.
{: .text-justify}

	
