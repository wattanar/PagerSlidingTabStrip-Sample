# Usage
#### Add the dependency in your build.gradle.
```java
dependencies {
    compile 'com.astuetz:pagerslidingtabstrip:1.0.1'
}
```
#### Add this code on your main layout
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <com.astuetz.PagerSlidingTabStrip
        android:id="@+id/tabs"
        app:pstsShouldExpand="true"
        app:pstsTextAllCaps="true"
        android:layout_width="match_parent"
        android:layout_height="48dp">
    </com.astuetz.PagerSlidingTabStrip>

    <android.support.v4.view.ViewPager
        android:id="@+id/viewpager"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="@android:color/white" />

</LinearLayout>
```
#### Create Fragment for display your content important ! don't forgot import  support.v4.app.Fragment 
```java
 import android.support.v4.app.Fragment; 
```
#### Create FragmentPageAdapter 
```java
public class SampleFragmentPagerAdapter extends FragmentPagerAdapter {
    final int PAGE_COUNT = 2;
    private String tabTitles[] = new String[] { "Tab1", "Tab2" };

    public SampleFragmentPagerAdapter(FragmentManager fm) {
        super(fm);
    }

    @Override
    public int getCount() {
        return PAGE_COUNT;
    }

    @Override
    public Fragment getItem(int position) {
        switch(position){
          case 0:
            return One.newInstance("","");
          case 1:
            return Two.newInstance("","");
        }
        return null;
    }

    @Override
    public CharSequence getPageTitle(int position) {
        // Generate title based on item position
        return tabTitles[position];
    }
}
```
#### Finally following code in your MainActivity
```java
public class MainActivity extends FragmentActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Get the ViewPager and set it's PagerAdapter so that it can display items
        ViewPager viewPager = (ViewPager) findViewById(R.id.viewpager);
        viewPager.setAdapter(new SampleFragmentPagerAdapter(getSupportFragmentManager()));

        // Give the PagerSlidingTabStrip the ViewPager
        PagerSlidingTabStrip tabsStrip = (PagerSlidingTabStrip) findViewById(R.id.tabs);
        // Attach the view pager to the tab strip
        tabsStrip.setViewPager(viewPager);
    }

}
```
- Output

![](http://www.wattanar.com/wp-content/uploads/2015/09/11181710_930612710307363_1494482766237451331_n.jpg)

- Source from : https://github.com/astuetz/PagerSlidingTabStrip
- Full guide : https://github.com/codepath/android_guides/wiki/Sliding-Tabs-with-PagerSlidingTabStrip
