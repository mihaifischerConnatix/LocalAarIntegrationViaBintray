# Local .aar dependency in a framework distribuited ia Bintray
Local .aar integration into another .aar that is published on Bintray

## Problem:
- When we import our framwork into a test project, the local .aar dependency embeded in our framework is empty. 

- Error got in the test app when running the app and trying to instantiate a class from the OM SDK framework within our framework:
```
W/System.err: java.lang.NoClassDefFoundError: Failed resolution of: Lcom/iab/omid/library/connatix/Omid;
        at com.cnx.connatixplayersdk.ConnatixPlayerSDK.activateOMSDK$connatixplayersdk_release(ConnatixPlayerSDK.kt:415)
W/System.err:     at com.cnx.connatixplayersdk.WebPlayerInterface.playerIsRendered(WebPlayerInterface.kt:29)
        at android.os.MessageQueue.nativePollOnce(Native Method)
        at android.os.MessageQueue.next(MessageQueue.java:326)
W/System.err:     at android.os.Looper.loop(Looper.java:160)
        at android.os.HandlerThread.run(HandlerThread.java:65)
W/System.err: Caused by: java.lang.ClassNotFoundException: Didn't find class "com.iab.omid.library.connatix.Omid" on path: DexPathList[[zip file "/data/app/com.cnx.sdktest-lnQ9WEMPh1J8dr31lEixPA==/base.apk"],nativeLibraryDirectories=[/data/app/com.cnx.sdktest-lnQ9WEMPh1J8dr31lEixPA==/lib/x86, /system/lib]]
W/System.err:     at dalvik.system.BaseDexClassLoader.findClass(BaseDexClassLoader.java:134)
W/System.err:     at java.lang.ClassLoader.loadClass(ClassLoader.java:379)
W/System.err:     at java.lang.ClassLoader.loadClass(ClassLoader.java:312)
```
- When opening unziping our framework, you can find the OM .aar in the ```libs``` folder, but when trying to unzipit it, it's empty. 

## Background Setup 
### framework project
- Our setup is consisting of an android project written in __Kotlin__, that has a module as dependency. 
- This module is an Android framework we share with publishers through [Bintray](https://bintray.com/connatix/ConnatixPlayer/ConnatixPlayerSDK). 
- We need to integrate in this framework another framework that is kept in the ```libs``` folder 
- You can take it from here: [om sdk](https://github.com/mihaifischerConnatix/LocalAarIntegrationViaBintray/blob/master/omsdk-android-1.3.1-release.aar)

- here is our module [build.gradle file](https://github.com/mihaifischerConnatix/LocalAarIntegrationViaBintray/blob/master/build.gradle)
- it also contains the build and upload to Bintray script at the end


### test app project
- we import the framework like this ```implementation 'com.connatix.sdk:connatixplayersdk:1.4.2'``` in the build.gradle dependency section.

### using OM SDK in your dependency
- [some of their Android documentation](https://interactiveadvertisingbureau.github.io/Open-Measurement-SDKAndroid/)
- for testing purposes should be enough only to active it:
```
      Omid.activate(applicationContext)

      var partner = Partner.createPartner("Connatix", "1.2") 

      var adSessionContext = AdSessionContext.createJavascriptAdSessionContext(partner, myWebview, "", "")
      var adSessionConfig = AdSessionConfiguration.createAdSessionConfiguration(CreativeType.DEFINED_BY_JAVASCRIPT,
            ImpressionType.DEFINED_BY_JAVASCRIPT, Owner.JAVASCRIPT, Owner.JAVASCRIPT, false)
      var omAdSession = AdSession.createAdSession(adSessionConfig, adSessionContext)
      omAdSession.start()
      
