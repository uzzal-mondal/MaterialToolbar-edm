# MaterialToolbar-edm

Material  Action Bar
Must have declare in  import

                       import android.support.v7.widget.Toolbar;


1.	First of all I create toolbar xml file with obliviously   

<?xml version="1.0" encoding="utf-8"?>
<android.support.v7.widget.Toolbar xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:background="@color/colorPrimary"
    android:elevation="4dp"

    >

</android.support.v7.widget.Toolbar>


2.	Then go to activitymain xml file.

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout

    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <!--including toolbar layout .. then selected layout with declare a id -->
    <include
        android:id="@+id/toolbar"
       layout="@layout/toolbar"/>



    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        android:layout_below="@id/toolbar"

         />

</RelativeLayout>

3.	Style’s almost lightNoActionBar

<resources>

    <!-- Base application theme. -->
    <style name="AppTheme" parent="Theme.AppCompat.Light.NoActionBar">
        <!-- Customize your theme here. -->
        <item name="colorPrimary">@color/colorPrimary</item>
        <item name="colorPrimaryDark">@color/colorPrimaryDark</item>
        <item name="colorAccent">@color/colorAccent</item>
    </style>

</resources>


4.	Crate a main menu and including 2 item actionSetting with actionSearch

<?xml version="1.0" encoding="utf-8"?>
<menu
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools">

    <item
        android:id="@+id/action_setting"
        android:orderInCategory="100"
        android:title="Settings"
        app:showAsAction="never"/>

    <item
        android:id="@+id/action_search"
        android:orderInCategory="200"
        android:title="Search"
        app:showAsAction="ifRoom"
        android:icon="@drawable/searchicon"/>





</menu>

5.	Create a mainActivity. All of find and set action bar. Wih onOptionMenu  OptionItemSelected..


package com.example.materialtoolbar;

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.support.v7.widget.Toolbar;
import android.view.Menu;
import android.view.MenuItem;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Toolbar toolbar = findViewById(R.id.toolbar);
        setSupportActionBar(toolbar);
        getSupportActionBar().setTitle("Material Action Bar");


    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu) {

        getMenuInflater().inflate(R.menu.main_menu,menu);

        return super.onCreateOptionsMenu(menu);
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        int id = item.getItemId();

        if (id==R.id.action_setting){
            Toast.makeText(this, "setting ok", Toast.LENGTH_SHORT).show();
        }

        if (id==R.id.action_search){
            Toast.makeText(this, "search ok now", Toast.LENGTH_SHORT).show();
        }

        return super.onOptionsItemSelected(item);
    }
}

