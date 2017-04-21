# Splash-Screen
Many popular Android Apps such as Skype, Facebook, Adobe Reader, 500px, Dropbox etc.,  uses splash screen to display their logo. Most Android Apps uses Android Splash Screen before launching application Activity. Android splash screen is used to display a logo or brand for an app. In this article we are going to discuss about implementing an Android Splash Screen in a simple manner.
First we will create a new default project using these simple steps:

* Click on File > New Project.
* Next, define Application Name and Minimum SDK and hit Next
* Select Blank Activity and Hit Next.
* Hit  Finish.

This creates a simple Hello world Project for which we will implement android Splash screen. We already discussed in detail about Creating New Android Project in our previous article.

**SplashScreen.java**
```
package com.sambhaji.splashscreen;

import android.content.Intent;
import android.os.Bundle;
import android.os.Handler;
import android.support.v7.app.AppCompatActivity;

public class SplashScreen extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_splash_screen);

        new Handler().postDelayed(new Runnable() {
            @Override
            public void run() {
                Intent i = new Intent(SplashScreen.this, MainActivity.class);
                startActivity(i);
                finish();
            }
        }, 3000);
    }

    @Override
    public void onBackPressed() {
        // Do nothing
    }
}
```
Make sure you have put an image in your drawable folder & image name should be ‘your_image’ as we mentioned in xml file.

In AndroidManifest.xml, we have to add both activities SplashScreen.java & splash.xml by which our splash screen would be appear before MainActivity (Home Screen). After adding some codes, AndroidManifest.xml will be,

**AndroidManifest.xml**
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.sambhaji.splashscreen">

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">
        <activity
            android:name=".SplashScreen"
            android:label="@string/app_name"
            android:theme="@style/AppTheme.NoActionBar">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
        <activity
            android:name=".MainActivity"
            android:label="@string/app_name"
            android:theme="@style/AppTheme"/>
    </application>

</manifest>
```

**MainActivity.java**
````
package com.sambhaji.splashscreen;

import android.os.Bundle;
import android.support.design.widget.FloatingActionButton;
import android.support.design.widget.Snackbar;
import android.support.v7.app.AppCompatActivity;
import android.support.v7.widget.Toolbar;
import android.view.View;
import android.view.Menu;
import android.view.MenuItem;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        // Inflate the menu; this adds items to the action bar if it is present.
        getMenuInflater().inflate(R.menu.menu_main, menu);
        return true;
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        // Handle action bar item clicks here. The action bar will
        // automatically handle clicks on the Home/Up button, so long
        // as you specify a parent activity in AndroidManifest.xml.
        int id = item.getItemId();

        //noinspection SimplifiableIfStatement
        if (id == R.id.action_settings) {
            return true;
        }

        return super.onOptionsItemSelected(item);
    }
}

````

That’s it, now run your app & Insha-Allah you will see a splash screen of few seconds showing an image before launching home screen. Your project about splash screen has been successfully completed once if you followed our above steps. 

<a href="url"><img src="https://github.com/sambhaji213/Splash-Screen/blob/master/screenshot/splash.png" align="left" height="480" width="250"></a>
