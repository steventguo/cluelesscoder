---
layout: post
title: Creating an Android Button with Multiple Internal Components
categories: [snippets]
tags: [Android, XML, Java]
description: Android provides a nice pre-defined button for programmers to use, but it has its limitations - you can't really edit the internal content, outside of having label text. This is a quick snippet that allows for multiple internal elements - an Android button with two labels, a button with an ImageView, and anything else you'd want to stash inside.
---

Wanting to customize your Android buttons is a pretty common issue - but not exactly obvious to a beginner programmer. If you're familiar with onClick functions for HTML5 divs, then this snippet is a lot like that - we're simply defining our own layout and making it clickable.  
<br>

In the example below, I'm going to create a **button with two `TextViews`** inside it, but the solution can easily be adapted to suit needs.

***

* First, we're going to need an XML layout.

    - I defined mine as a `LinearLayout`, but you can use whatever layout would fit your button the best.  
    <br>
    
    - Inside of the `LinearLayout`, I defined two `TextView` elements.  
    <br>
    
    - The `LinearLayout` must be defined with the tag `android:clickable="true"`! If that property isn't present, your Layout
    will never click! Our final layout looks something like this...  

    {% highlight xml %} 
    <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
            android:id="@+id/cost"
            android:layout_width="80dp"
            android:orientation="vertical"
            android:layout_height="46dp"
            android:background="#f6b637"
            android:clickable="true" >

            <TextView
                android:id="@+id/text1"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:text="text1"
                android:layout_gravity="left"/>

            <TextView
                android:id="@+id/text2"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:text="text2"
                android:layout_gravity="left" />

        </LinearLayout>
    {% endhighlight %}  



<br>
    
    
![LinearLayout]({{ site.url }}/assets/media/button_two_view.png)  
    

<br>

* We now have a flat layout that resembles a button, so on to making it clickable!

    - In your activity (or fragment, wherever you have your item), we can define our `onClick` function like so:  
    
    {% highlight java %} 
        LinearLayout linearLayout = (LinearLayout) view.findViewById(R.id.linearLayout);
        linearLayout.setOnClickListener(new View.OnClickListener() {
            public void onClick(View v) {
                // whatever you want the button to do here    
            }
        });
    {% endhighlight %}  

* If you want to customize the text inside the button...  



    {% highlight java %} 
        TextView text1 = (TextView) view.findViewById(R.id.text1);
        text1.setText("yourdesiredtext");

        TextView text2 = (TextView) view.findViewById(R.id.text2);
        text2.setText("yourdesiredtext");
    {% endhighlight %}  



* Voila! We now have a clickable button that does what we want on touch, with two text views instead of the default one provided by the SDK. It's easily customizable, given that you don't want two `TextViews` or a `LinearLayout` - simply change the XML and typing of the Java snippets, and it's good to go. On the same vein, styling the XML so that it's not an ugly orange button with ugly text is probably a good idea too.



    
    


