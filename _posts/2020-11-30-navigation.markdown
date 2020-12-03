---
title:  "Jetpack Navigation with BottomNavigationView"
date:   2019-11-30 22:00:00
categories: [android]
tags: [android, layout, navigation, jetpack]
---

// under construction // 

Jetpack Navigation made screen transition easy to implement and Navigation Bottom View interacts very well with it. First of all we need to create a Navigation Bottom View as described bellow:

In a layout file:

```xml
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="wrap_content">
  ...
  <com.google.android.material.bottomnavigation.BottomNavigationView
      android:id="@+id/bottom_navigation"
      android:layout_width="match_parent"
      android:layout_height="wrap_content"
      app:menu="@menu/bottom_navigation_menu" />

</LinearLayout>
```

and then create a `bottom_navigation_menu.xml` under `menu` **res** structure:

```xml
<menu xmlns:android="http://schemas.android.com/apk/res/android">
  <item
      android:id="@+id/page_1"
      android:enabled="true"
      android:icon="@drawable/icon_1"
      android:title="@string/text_label_1"/>
  <item
      android:id="@+id/page_2"
      android:enabled="true"
      android:icon="@drawable/icon_2"
      android:title="@string/text_label_2"/>
</menu>
```

Now we need to create our Jetpack Navigation components:
