# Design Library

```
dependencies {
    compile fileTree(dir: 'libs', include: '*.jar')
    compile 'com.android.support:appcompat-v7:23.1.0'
    compile 'com.android.support:support-v4:23.1.0'
    compile 'com.android.support:design:23.1.0'
}
```

# Tab Layout

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context="com.phicdy.test.MainActivity">

    <android.support.design.widget.TabLayout
        android:id="@+id/tab_layout"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="?attr/colorPrimary"
        android:elevation="6dp"
        android:minHeight="?attr/actionBarSize"
        android:theme="@style/ThemeOverlay.AppCompat.Dark.ActionBar"/>

    <android.support.v4.view.ViewPager
        android:id="@+id/container"
        android:layout_width="match_parent"
        android:layout_height="match_parent"/>

</LinearLayout>

```

```java
public class TabMainActivity extends AppCompatActivity{
  private ViewPager viewPager;

	@Override
  public void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    initViews();
  }

  private void initViews(){
    setContentView(R.layout.main);

    SectionsPagerAdapter sectionsPagerAdapter = new SectionsPagerAdapter(getSupportFragmentManager());
    // Set up the ViewPager with the sections adapter.
    viewPager = (ViewPager) findViewById(R.id.container);
    viewPager.setAdapter(sectionsPagerAdapter);

    TabLayout tabLayout = (TabLayout)findViewById(R.id.tab_layout);
    tabLayout.setupWithViewPager(viewPager);
    for (int i = 0; i < tabLayout.getTabCount(); i++) {
      tabLayout.getTabAt(i).setIcon(mSectionsPagerAdapter.getImageResource(i));
    }
  }

  public class SectionsPagerAdapter extends FragmentPagerAdapter {

      public SectionsPagerAdapter(FragmentManager fm) {
          super(fm);
      }

      @Override
      public Fragment getItem(int position) {
          // getItem is called to instantiate the fragment for the given page.
          // Return a PlaceholderFragment (defined as a static inner class below).
          return TestFragment.newInstance("a", "b");
      }

      @Override
      public int getCount() {
          // Show 2 total pages.
          return 2;
      }

      @Override
      public CharSequence getPageTitle(int position) {
          switch (position) {
              case 0:
                  return "Section 1";
              case 1:
                  return "Section 2";
          }
          return null;
      }

      public int getImageResource(int position) {
          switch (position) {
              case 0:
                  return R.drawable.icon1;
              case 1:
                  return R.drawable.icon2;
          }
          return -1;
      }
  }
}
```

## Reference

* http://developer.android.com/intl/ja/reference/android/support/design/widget/TabLayout.html
* http://www.google.com/design/spec/components/tabs.html
* http://www.truiton.com/2015/06/android-tabs-example-fragments-viewpager/
* http://tech.recruit-mp.co.jp/design/post-5165/
