---
title:  "Creating a cool list of categories with RecyclerView"
date:   2019-03-22 22:00:00
categories: [android, mobile]
tags: [xml, android, kotlin, mobile, material design]
---

I'm building a guessing game with eSports theme, so I decided to use a few free images to create a list of categories and the first result was this: 

// under construction //

and the XML file for the item on list:

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

{% endhightlight %}


// under construction //
