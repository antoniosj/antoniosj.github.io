---
title:  "Creating a cool list of categories with RecyclerView"
date:   2019-03-22 22:00:00
categories: [android, mobile]
tags: [xml, android, kotlin, mobile, material design]
---

I'm building a guessing game with eSports theme, so I decided to use a few free images to create a list of categories and the first result was this: 

 <img src="https://github.com/antoniosj/antoniosj.github.io/blob/master/images/posts/rv_1.png?raw=true" width="400px"/>
 

and the XML file for the item on the list:

{% highlight swift %}

<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
              android:orientation="vertical"
              android:background="@drawable/team"
              android:id="@+id/item_category_background"
              android:layout_width="match_parent"
              android:scaleType="centerCrop"
              android:adjustViewBounds="true"
              android:layout_height="200dp">

   <TextView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:textColor="@android:color/white"
            android:id="@+id/tv_category_title"
    />

</LinearLayout>

{% endhighlight %}

The first problem in my point of view was the size of the images. I had big images and this was making my layout a bit slow for a Moto G5 device. Another issue was the colors of the images, so I decided to change to make it seems like a "game" app.

// image here //

In the end, I started to do some improves, first of all, I downloaded a nice font (.ftt) and then I changed my item layout. I also create an edge between images, and then I made a bottom overlay for each image. Finally, I used ripple library to make an animation effect on touch and my RecyclerView become this:   

// image here ///

And my layout:

// src code here //

There's a lot of improvements to make but I think this is a way to go.  

// under construction //
