---
layout: post
title: "Launching an activity directly with adb"
date: 2020-01-26
---

# Launching an activity directly with adb

An android application can have many activities and sometimes navigating to the one you currently developing can be annoying if you have to do it over and over again. 

An activity can be started directly from adb provided it is ["exported"](https://developer.android.com/guide/topics/manifest/activity-element#exported). This can be done by setting `android:exported="true"` in the `AndroidManifest.xml`. You can do the same for a service or a broadcast. You should only do this for the debug version of your application for testing.

`app/src/debug/AndroidManifest.xml`
```xml
<application>
    <activity 
        android:name=".TestActivity"
        android:exported="true" />
    <receiver
        android:name=".TestReceiver"
        android:exported="true" />
    <service
        android:name=".TestService"
        android:exported="true" />
</application>
```

Now you can use adb to directly launch the activity without navigating through all other activities.

```sh
adb shell am start -n com.example.debug/.TestActivity \
--ei "EXTRA_INTEGER" 25  \
--es "EXTRA_STRING" "Tester" \
--el "EXTRA_LONG" 2313
```

You can also send a broadcast or start a service.

```sh
adb shell am broadcast -n com.example.debug/.TestReceiver \
--ei "EXTRA_INTEGER" 25  \
--es "EXTRA_STRING" "Tester" \
--el "EXTRA_LONG" 2313
```

```sh
adb shell am startservice -n com.example.debug/.TestService \
--ei "EXTRA_INTEGER" 25  \
--es "EXTRA_STRING" "Tester" \
--el "EXTRA_LONG" 2313
```

`--ei`, `--es` and `--el` are used to add integer extra, string extra or long extra respectively. You can get the details of all parameters from the official [android documentation.
](https://developer.android.com/studio/command-line/adb.html#IntentSpec)

Exported activities can also be launched directly from Android Studio. Just create a new run configuration and provide the intent extras as "Launch Flags"

![Run Configuration]({{ site.url }}/media/images/TGF1bmNoaW5nIGFuIGFjdGl2aXR5IGRpcmVjdGx5IHdpdGggYWRiIDEK.png){:height="50%" width="50%"}