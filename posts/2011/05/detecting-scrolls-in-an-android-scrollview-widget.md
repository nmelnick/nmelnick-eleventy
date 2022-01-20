---
title: "Detecting scrolls in an Android ScrollView widget"
date: "2011-05-31"
categories: 
  - "code"
  - "off-topic"
tags: 
  - "android"
  - "detect"
  - "onscroll"
  - "scroll"
  - "scrollview"
---

So, Android.

You would think that Google would have an event available for when someone scrolls a ScrollView widget. After all, it's the basic way to make some view scroll. Even better, there is an event for the AbsListView and other scrollable widgets. Turns out, there is an event that gets fired in a ScrollView, but you have to subclass the widget to get at it. Then, you have to figure out how to get that message back to your controller.

Lame.

So, for those of you who want to see if a scroll changed on a ScrollView, do the following:

1) Create a class, call it whatever you'd like, but subclass ScrollView. You'll probably need to override the three existing constructors to be able to instantiate from your controller or XML layout.

```
public class ExampleScrollView extends ScrollView {
    public ExampleScrollView(Context context) {
        super(context);
    }
    public ExampleScrollView(Context context, AttributeSet attrs) {
        super(context, attrs);
    }    public ExampleScrollView(Context context, AttributeSet attrs, int defStyle) {
        super(context, attrs, defStyle);
    }
}
```

2) Add an interface within our new class to be able to set a listener. We'll call it something different so we don't override any existing OnScrollListeners.

```
public interface OnScrollViewListener {    void onScrollChanged( ExampleScrollView v, int l, int t, int oldl, int oldt );}
```

3) Let's add a private attribute and a way to set that listener in the class.

```
private OnScrollViewListener mOnScrollViewListener;
public void setOnScrollViewListener(OnScrollViewListener l) {
    this.mOnScrollViewListener = l;
}
```

4) Now, set onScrollChanged to fire the event we provide.

```
protected void onScrollChanged(int l, int t, int oldl, int oldt) {    mOnScrollViewListener.onScrollChanged( this, l, t, oldl, oldt );    super.onScrollChanged( l, t, oldl, oldt );}
```

You're done! You can now set up one of these in your XML layout, or built on the fly. Set your new listener like this, provided you have one in your layout with an id of 'example\_scroll\_view':

```
ExampleScrollView exampleScrollView = (ExampleScrollView) findViewById( R.id.example_scroll_view);exampleScrollView.setOnScrollViewListener( new OnScrollViewListener() {    public void onScrollChanged( ExampleScrollView v, int l, int t, int oldl, int oldt ) {        Log.d( "Scroller", "I changed!" );    }} );
```
