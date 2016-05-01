Android Spec
============

#### Java Language Spec
 + data struction
 
#### Android Language Spec
 + folders
 ```
├── build
│   ├── generated
│   │   └── mockable-android-23.jar
│   └── intermediates
│       └── dex-cache
│           └── cache.xml
├── build.gradle
├── gradle
│   └── wrapper
│       ├── gradle-wrapper.jar
│       └── gradle-wrapper.properties
├── gradle.properties
├── gradlew
├── gradlew.bat
├── local.properties <- 環境設定 sdkのパスとか
├── mobile
│   ├── build <- build 関連ファイル
│   │   ├── generated
│   │   │   ├── res
│   │   │   └── source
│   │   ├── intermediates 
│   │   │   ├── assets
│   │   │   ├── blame
│   │   │   ├── builds
│   │   │   ├── bundles
│   │   │   ├── classes
│   │   │   ├── dependency-cache
│   │   │   ├── exploded-aar
│   │   │   ├── incremental
│   │   │   ├── incremental-classes
│   │   │   ├── incremental-runtime-classes
│   │   │   ├── incremental-verifier
│   │   │   ├── instant-run-support
│   │   │   ├── jniLibs
│   │   │   ├── manifest
│   │   │   ├── manifests
│   │   │   ├── pre-dexed
│   │   │   ├── reload-dex
│   │   │   ├── res
│   │   │   ├── restart-dex
│   │   │   ├── rs
│   │   │   ├── symbols
│   │   │   └── transforms
│   │   ├── outputs
│   │   │   ├── apk
│   │   │   └── logs
│   │   └── tmp
│   │       └── compileDebugJavaWithJavac
│   ├── build.gradle
│   ├── libs
│   ├── mobile.iml
│   ├── proguard-rules.pro
│   └── src <- ソースの場所
│       ├── androidTest
│       │   └── java
│       ├── main
│       │   ├── AndroidManifest.xml
│       │   ├── java
│       │   └── res <- resourceの場所
│       └── test
│           └── java
└── settings.gradle

 ```
 + files
 
 ◯ src/main/res/values/strings.xml
 ```

 $ tree -L 1 
 ├── drawable <- R.drawable
 ├── layout <- R.layout
 ├── menu <- R.menu
 ├── mipmap-hdpi
 ├── mipmap-mdpi
 ├── mipmap-xhdpi
 ├── mipmap-xxhdpi
 ├── mipmap-xxxhdpi
 ├── values <- R.array, R.integer, R.bool, R.dimen, R.string
 ├── values-v21
 ├── values-w820dp
 └── xml <- Resources.getXML()
 
 example in java: R.string.app_name
 example in xml: @string/app_name
 <resources>
    <string name="app_name">HelloWorld</string>
    <string name="hello_world">Hello world!</string>
    <string name="menu_settings">Settings</string>
    <string name="title_activity_main">MainActivity</string>
 </resources>
 ```
 ◯ src/main/res/layout/activity_main.xml
 ```
 <?xml version="1.0" encoding="utf-8"?>
 <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
     xmlns:tools="http://schemas.android.com/tools"
     android:layout_width="match_parent"
     android:layout_height="match_parent"
     android:paddingBottom="@dimen/activity_vertical_margin"
     android:paddingLeft="@dimen/activity_horizontal_margin"
     android:paddingRight="@dimen/activity_horizontal_margin"
     android:paddingTop="@dimen/activity_vertical_margin"
     tools:context="com.example.zhou.hellowold.MainActivity">
 
     <TextView
         android:layout_width="wrap_content"
         android:layout_height="wrap_content"
         android:text="Hello World!" />
 </RelativeLayout>
 ```
 ◯ src/main/AndroidManifest.xml
 ```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.zhou.hellowold">

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest> 
 ```
   + Processing Description
     + start at Activity::onCreate()
     + startProcess: onCreate >> onStart >> onResume >> ActivityRunning 
     + EndProcess: onPause >> onStop >> onDestroy >> ActivityShutDown
   ![android live cycle](http://www.tutorialspoint.com/android/images/activity.jpg "android live cycle")
   + content Provider (data getter)
        ![provider image](http://www.tutorialspoint.com/android/images/content.jpg "provider image")
   + Fragments < sub activity >
        ![fragment life cycle](http://www.tutorialspoint.com/android/images/fragment.jpg "fragment life cycle")
   + 
   + 
   + 
   + 


#### Android BuildIn Function

#### Android Library (buildIn)
  + android.app − Provides access to the application model and is the cornerstone of all Android applications.
  
  + android.content − Facilitates content access, publishing and messaging between applications and application components.
  
  + android.database − Used to access data published by content providers and includes SQLite database management classes.
  
  + android.opengl − A Java interface to the OpenGL ES 3D graphics rendering API.
  
  + android.os − Provides applications with access to standard operating system services including messages, system services and inter-process communication.
  
  + android.text − Used to render and manipulate text on a device display.
  
  + android.view − The fundamental building blocks of application user interfaces.
  
  + android.widget − A rich collection of pre-built user interface components such as buttons, labels, list views, layout managers, radio buttons etc.

#### Android Extend Library

#### Build & Envirment

 + [Emulator]genymotionをいれてみる
```
https://www.genymotion.com/download/
```

#### Samples

```

import android.app.Service;
import android.content.Intent;
import android.os.IBinder;

public class MyService extends Service {
    int mStartMode;
    IBinder mBinder;
    boolean mAllowRebind;

    // constructor
    public MyService() {
    }

    @Override
    public void onCreate() {

    }

    @Override
    public int onStartCommand( Intent intent , int flags, int startId) {
        return mStartMode;
    }

    @Override
    public IBinder onBind(Intent intent) {
        return mBinder;
    }


    /** Called when all clients have unbound with unbindService() */
    @Override
    public boolean onUnbind(Intent intent) {
        return mAllowRebind;
    }

    /** Called when a client is binding to the service with bindService()*/
    @Override
    public void onRebind(Intent intent) {

    }

    /** Called when The service is no longer used and is being destroyed */
    @Override
    public void onDestroy() {

    }
}
```
