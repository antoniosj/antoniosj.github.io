---
title:  "Creating a cool list of categories with RecyclerView"
date:   2019-03-22 22:00:00
categories: [android, mobile]
tags: [xml, android, kotlin, mobile, material design]
---

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;" >I'm building a guessing game with eSports theme, so I decided to use a few free images to create a list of categories and the first result was this:</p> 

<div style="text-align:center"><img src="https://github.com/antoniosj/antoniosj.github.io/blob/master/images/posts/rv_1.png?raw=true" width="400px"/></div>
 
<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;" >and the XML file for the item on the list:</p>

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

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;" >The first problem in my point of view was the size of the images. I had big images and this was making my layout a bit slow for a Moto G5 device. Another issue was the colors of the images, so I decided to change to make it seems like a "game" app.</p>

<div style="text-align:center"><img src="https://github.com/antoniosj/antoniosj.github.io/blob/master/images/posts/rv_2.png?raw=true" width="400px"/></div>

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;" >In the end, I started to do some improves, first of all, I downloaded a nice font (.ftt) and then I changed my item layout. I also create an edge between images, and then I made a bottom overlay for each image. Finally, I used RippleEffect library to make an animation effect on touch and my RecyclerView become this:</p>   

<div style="text-align:center"><img src="https://github.com/antoniosj/antoniosj.github.io/blob/master/images/posts/rv_3.png?raw=true" width="400px"/></div>


### RippleEffect library:

{:refdef: style="text-align: center;"}
![RippleEffect GIF](https://github.com/antoniosj/antoniosj.github.io/blob/master/images/posts/rippleeffect.gif?raw=true)
{:refdef}

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;" >Well, as I wanted to make a black layout, I added some last touches:</p>  

<div style="text-align:center"><img src="https://github.com/antoniosj/antoniosj.github.io/blob/master/images/posts/rv_4.png?raw=true" width="400px"/></div>

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;" >And my layout:</p>


### Toolbar: 

{% highlight swift %}

<?xml version="1.0" encoding="utf-8"?>
<androidx.appcompat.widget.Toolbar
        xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:id="@+id/toolbar"
        android:layout_width="match_parent"
        android:layout_height="?attr/actionBarSize"
        android:background="?attr/colorPrimary"
        app:layout_scrollFlags="scroll|enterAlways"
        app:contentInsetStartWithNavigation="0dp"
        android:theme="@style/ThemeOverlay.AppCompat.Dark.ActionBar"
        app:popupTheme="@style/ThemeOverlay.AppCompat.Light">
</androidx.appcompat.widget.Toolbar>

{% endhighlight %}

### Category item:

{% highlight swift %}

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
              xmlns:app="http://schemas.android.com/apk/res-auto"
              android:orientation="vertical"
              android:layout_width="match_parent"
              android:layout_height="200dp">

   <androidx.cardview.widget.CardView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:clipToPadding="true"
            app:cardBackgroundColor="@color/colorPrimary"
            app:cardCornerRadius="8dp"
            app:cardElevation="6dp"
            app:cardPreventCornerOverlap="false"
           >

  <com.balysv.materialripple.MaterialRippleLayout
                android:id="@+id/lyt_parent"
                style="@style/RippleStyleBlack"
                android:layout_width="match_parent"
                android:layout_height="match_parent">

   <RelativeLayout
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content">

   <ImageView
                    android:id="@+id/item_category_background"
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:scaleType="centerCrop"
                    android:src="@drawable/misc"/>

   <LinearLayout
                    android:layout_width="match_parent"
                    android:layout_height="@dimen/spacing_xxlarge"
                    android:background="@color/overlay_dark_50"
                    android:gravity="center_vertical"
                    android:orientation="horizontal"
                    android:layout_alignParentBottom="true"
                    android:layout_alignParentLeft="true"
                    android:layout_alignParentStart="true">

   <View
               android:layout_width="@dimen/spacing_large"
               android:layout_height="0dp"/>

   <TextView
              android:layout_width="0dp"
              android:fontFamily="@font/garrison_sans"
              android:id="@+id/tv_category_title"
              android:layout_height="wrap_content"
              android:layout_weight="1"
              android:textSize="23dp"
              android:text="Category"
              android:textAppearance="@style/Base.TextAppearance.AppCompat.Medium"
   />

   </LinearLayout>

   </RelativeLayout>


   </com.balysv.materialripple.MaterialRippleLayout>
   </androidx.cardview.widget.CardView>
</LinearLayout>

{% endhighlight %}

### Category main

{% highlight swift %}

<?xml version="1.0" encoding="utf-8"?>
<androidx.coordinatorlayout.widget.CoordinatorLayout
        xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:tools="http://schemas.android.com/tools"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:background="@color/colorPrimary"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        tools:context=".ui.category.CategoryActivity">

   <com.google.android.material.appbar.AppBarLayout
            android:layout_height="wrap_content"
            android:layout_width="match_parent">

   <include layout="@layout/toolbar" />

   </com.google.android.material.appbar.AppBarLayout>

   <androidx.recyclerview.widget.RecyclerView
            android:id="@+id/rv_categories"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:clipToPadding="false"
            android:scrollbars="vertical"
            android:scrollingCache="true"
            app:layout_behavior="@string/appbar_scrolling_view_behavior"
    />

</androidx.coordinatorlayout.widget.CoordinatorLayout>

{% endhighlight %}

<p style="text-align: justify; font-family: -apple-system, BlinkMacSystemFont, sans-serif;" >There's a lot of improvements to make but I think this is a way to go.</p>  

