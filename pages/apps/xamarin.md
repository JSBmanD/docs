---
title: Xamarin
---

## Integrate Branch

!!! warning "Inconsistent Universal links behavior on iOS 11.2"
    After updating a device to iOS 11.2, we found that the app's AASA file is no longer downloaded reliably onto your user’s device after an app install. As a result, clicking on Universal links will no longer open the app consistenly. You can set [forced uri redirect mode](/links/integrate/#forced-redirections) on your Branch links to open the app with URI schemes. View details of the issue on the [Apple Bug report](http://www.openradar.me/radar?id=4999496467480576).

!!! warning "Google Play Services version 17+"
    If you reference Google Play Services version 17 or higher, you <notranslate>**MUST**</notranslate> complete Google's update instructions [here](https://developers.google.com/android/guides/releases#june_17_2019).

    Due to a major Google Play Services change made in June 2019, not completing the update steps will cause Branch's Android SDK (and various other cross-platform SDKs, e.g. Unity) to stop collecting Android AID which we use to ensure accurate deep linking and attribution.

    If you are running Google Play Services versions below 17, no update is necessary.

- ### Configure Branch

    - Complete your [Branch Dashboard](https://dashboard.branch.io/settings/link)

        ![image](/images/pages/apps/cordova-configure.png)
        ![image](/images/pages/apps/cordova-link-domain.png)

- ### Install Branch

    - **NuGet**

        The Branch Xamarin SDK is available as a NuGet package. The [Branch NuGet package](https://www.nuget.org/packages/Branch-Xamarin-Linking-SDK) must be added to each of the Xamarin projects that will use Branch methods.

        To add the Branch NuGet package to a project:

        1. Right-click on each project and select <notranslate>**Add > Add NuGet Packages**</notranslate>
        1. If not already present, find the <notranslate>_Microsoft BCL Build Components_</notranslate> package version 1.0.21 and add it to the project
        1. Find the <notranslate>_Branch Xamarin SDK_</notranslate> package version 3.0 and add it to the project

    - **Manually**

        If, instead of using NuGet, you would rather build and reference the Branch assemblies directly:

        1. Clone this repository to the local machine: `https://github.com/BranchMetrics/xamarin-branch-deep-linking.git`
        1. Add the `Branch-Xamarin-SDK` project to the solution and reference it from the Android, iOS and Forms (if applicable) projects
        1. Add the `Branch-Xamarin-SDK.Droid` project to the solution and reference it from the Android project, if any
        1. Add the `Branch-Xamarin-SDK.iOS` project and reference it from the iOS project, if any

- ### Configure app

    - **iOS**

        - **Create an Apple device Provisioning Profile for the app**

            1. Open Xcode and create a new project with the same name as your Xamarin iOS project
            1. On the Xcode project's <notranslate>**General**</notranslate> tab, verify the app's case-sensitive Bundle Identifier is correct and select the appropriate Team (be sure to resolve any errors here)
            1. Select the <notranslate>**Capabilities**</notranslate> tab and enable the <notranslate>**Associated Domains**</notranslate> entitlement
            1. Create 'applinks:' entries for the Branch link domain and the alternate link domain (the link domain can be found at the bottom of the Branch dashboard's [Link Settings](https://dashboard.branch.io/#/settings/link) page). For example, the entries for an app with the default link domain 'testiosapp.app.link' would be:
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`applinks:testiosapp.app.link`
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`applinks:testiosapp-alternate.app.link`
            1. Use Xcode to run this newly-created app on an iOS device. This will create and install a Provisioning Profile with the proper entitlements on that device.
            1. Close Xcode

        - **Enter the app's settings on the Branch dashboard**

            1. On the [Link Settings](https://dashboard.branch.io/#/settings/link) page, check the <notranslate>**I have an iOS App**</notranslate> checkbox
            1. Enter the app's URI Scheme in the <notranslate>**iOS URI Scheme**</notranslate> field (for an app with the URI Scheme *testbed-xamarin*, for example, the entry would be: `testbed-xamarin://`)
            1. Enter the app's Apple Store name in the <notranslate>**Apple Store Search**</notranslate> field (if the app is not yet available on the App Store select <notranslate>**Custom URL**</notranslate> and enter as a placeholder the URL of an appropriate web site - the exact site does not matter)
            1. Check the <notranslate>**Enable Universal Links**</notranslate> checkbox
            1. Enter the app's case-sensitive Bundle Identifier and Apple App Prefix as shown on the [Apple Developer Portal](https://developer.apple.com/account/ios/identifier/bundle)

        - **Configure the Xamarin project's Info.plist file**

            1. Open the <notranslate>**Info.plist**</notranslate> file
            1. Enter the app's <notranslate>**Bundle Identifier**</notranslate> from the [Apple Developer Portal](https://developer.apple.com/account/ios/identifier/bundle) in the <notranslate>**Bundle Identifier**</notranslate> field. <notranslate>**IMPORTANT:**</notranslate> this field will automatically be populated with an all-lowercase value by Xamarin. The value is in fact case sensitive and must match the value in the [Apple Developer Portal](https://developer.apple.com/account/ios/identifier/bundle) precisely.
            1. Click on the <notranslate>**Advanced**</notranslate> tab
            1. In the <notranslate>**URL Types**</notranslate> section, click the <notranslate>**Add URL Type**</notranslate> button
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<notranslate>**Identifier:**</notranslate> Branch Scheme
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<notranslate>**URL Schemes:**</notranslate> {the app's URI Scheme - 'testiosapp', for example}
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<notranslate>**Role:**</notranslate> Editor

            ![image](/images/pages/apps/xamarin/ios_uri_scheme.png)

        - **Configure the Xamarin project's Associated Domains entitlement**

            1. Open the **Entitlements.plist** file and browse to **Associated Domains**
            1. Create entries for both the app's link domain and its alternate link domain. The entries for the TestBed-Xamarin app would be:
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`applinks:testiosapp.app.link`
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`applinks:testiosapp-alternate.app.link`

            ![image](/images/pages/apps/xamarin/ios_associated_domains.png)


        - **Update the project's Signing Identity and Provisioning Profile**

            1. Right-click on the iOS project and select <notranslate>**Options**</notranslate>
            1. Select <notranslate>**iOS Bundle Signing**</notranslate>
            1. Set the <notranslate>**Signing Identity**</notranslate> and <notranslate>**Provisioning Profile values**</notranslate> to the values used when deploying the Provisioning Profile to the device above

    - **Android**

        - **Ensure that the Android project is not using the Shared Mono Runtime**

            1. Right-click on the Android project and select: <notranslate>**Options**</notranslate>
            1. Select: <notranslate>**Android Build**</notranslate>
            1. On the <notranslate>**General**</notranslate> tab, un-check: <notranslate>**Use Shared Mono Runtime**</notranslate>

        - **Add app capabilities in the app's Manifest file**

            In the *Required permissions* section of <notranslate>**AndroidManifest.xml**</notranslate>, configure the following permissions:

            - <notranslate>*AccessNetworkState*</notranslate>
            - <notranslate>*Internet*</notranslate>

            Additional reading on the Android manifest:

            - [Working with android manifest.xml](https://developer.xamarin.com/guides/android/advanced_topics/working_with_androidmanifest.xml/)
            - [Add permissions to android manifest](https://developer.xamarin.com/recipes/android/general/projects/add_permissions_to_android_manifest/)

        - **Add the app's Branch key to the Strings.xml file**

            Add the Branch key to the Android project's <notranslate>**Resources/values/Strings.xml**</notranslate> file. This file contains values that can be accessed by the app's Application class.

            ```xml
            <?xml version="1.0" encoding="utf-8"?>
            <resources>
                <string name="app_name">TestXamarinFormsApp</string>
                <string name="branch_key">key_live_liAnF8k7gZUEZv76Rt9a4bffAzlC5zVW</string>
            </resources>
            ```

- ### Initialize Branch

    - **iOS**

        Branch initialization occurs within the `FinishedLaunching` method of the <notranslate>**AppDelegate.cs**</notranslate> file. Branch calls are also required in the `OpenUrl`, `ContinueUserActivity`, and `ReceiveRemoteNotification` methods to ensure that Branch link information is handled properly whenever the app becomes active.

        Whenever the app becomes active, the Branch SDK will reach out to the Branch back end to retrieve any available link parameters. If the app became active due to a click on a Branch link, the link data will be returned in the `InitSessionComplete method`. This is where any deep link routing logic should reside. Any error in retrieving Branch link data from the back end will returned in the `SessionRequestError` method.

        ```csharp
        // AppDelegate.cs

        using Foundation;
        using UIKit;
        using BranchXamarinSDK;
        using BranchXamarinSDK.iOS;
        using System;

        namespace TestiOSApp.iOS
        {
            [Register("AppDelegate")]
            public class AppDelegate : UIApplicationDelegate, IBranchBUOSessionInterface
            {
                public override UIWindow Window
                {
                    get;
                    set;
                }

                public override bool FinishedLaunching(UIApplication application, NSDictionary launchOptions)
                {
                    // Debug mode - set to 'false' before releasing to production
                    BranchIOS.Debug = true;
                    BranchIOS.Init("key_live_cgEguO4UiDJSL4HIyTu85dkkDAdz38ER", launchOptions, this);

                    return true;
                }

                // Called when the app is opened via URI scheme
                public override bool OpenUrl(UIApplication application, NSUrl url, string sourceApplication, NSObject annotation)
                {
                    return BranchIOS.getInstance().OpenUrl(url);
                }

                // Called when the app is opened from a Universal Link
                public override bool ContinueUserActivity(UIApplication application, NSUserActivity userActivity,
                              UIApplicationRestorationHandler completionHandler)
                {
                    return BranchIOS.getInstance().ContinueUserActivity(userActivity);
                }

                // Called when the app receives a push notification
                public override void ReceivedRemoteNotification(UIApplication application, NSDictionary userInfo)
                {
                    BranchIOS.getInstance().HandlePushNotification(userInfo);
                }

                // Called when the Branch initialization is completed
                // Put deep-linking logic in this method
                public void InitSessionComplete(BranchUniversalObject buo, BranchLinkProperties blp)
                {
                    NSObject[] keys = {
                        NSObject.FromObject("+is_first_session")
                    };

                    NSObject[] values = { NSObject.FromObject(0) };
                    if (buo.metadata.ContainsKey("+is_first_session"))
                    {
                        values[0] = NSObject.FromObject(buo.metadata["+is_first_session"]);
                    }

                    NSDictionary nsData = NSDictionary.FromObjectsAndKeys(values, keys);
                }

                // Called when there is an error initializing Branch
                public void SessionRequestError(BranchError error)
                {
                    Console.WriteLine("Branch error: " + error.ErrorCode);
                    Console.WriteLine(error.ErrorMessage);
                }

            }
        }
        ```

    - **Android**

        - **Create the project's <notranslate>*Application.cs*</notranslate> class**

            1. Right-click on the .Droid project and select **</notranslate>Add > New File...<notranslate>**
            1. Select: **</notranslate>General > Empty File<notranslate>**
            1. Name the file: **</notranslate>Application.cs**
            1. Enter the following code (replace 'TestAndroidApp' with the actual name of the app):

            ```csharp
            using System;
            using Android.App;
            using Android.Content;
            using Android.Runtime;
            using BranchXamarinSDK;

            namespace TestAndroidApp.Droid
            {
                [Application(AllowBackup = true, Icon = "@mipmap/icon", Label = "@string/app_name")]
                [MetaData("io.branch.sdk.auto_link_disable", Value = "false")]
                [MetaData("io.branch.sdk.TestMode", Value = "true")]
                [MetaData("io.branch.sdk.BranchKey", Value = "@string/branch_key")]

                public class TestAndroidApp : Application
                {
                    public TestAndroidApp(IntPtr javaReference, JniHandleOwnership transfer) : base(javaReference, transfer)
                    {
                    }

                    public override void OnCreate()
                    {
                        base.OnCreate();
                        BranchAndroid.GetAutoInstance(this.ApplicationContext);
                    }
                }
            }
            ```

            | Key | Value
            | --- | ---
            | `io.branch.sdk.TestMode` | Setting this parameter to *true* enables Debug Mode, which causes simple uninstall/reinstalls of the app to trigger *install* events. Be sure to disable this before deploying to production. Note that enabling Debug Mode on Android also forces the app to use the Branch *Test* key if this key has been added to the project. Apps running with a *Test* key will be unable to receive data from Branch links created with the *Live* key.
            | `io.branch.sdk.BranchKey` | The app's Branch key. Both a *Live* key and a *Test* key can be added to the Strings.xml file. When *Test* Mode is enabled the app will automatically use the *Test* key, if one has been specified.

        - **Create an activity to handle Branch events: BranchActivity**

            1. Right-click on the .Droid project and select <notranslate>**Add > New File...**</notranslate>
            1. Select: <notranslate>**Android > Activity**</notranslate>
            1. Rename the file: <notranslate>**BranchActivity.cs**</notranslate>
            1. Enter the following code (replace 'TestAndroidApp' with the actual name of the app):

            ```csharp
            using System;
            using System.Collections.Generic;
            using System.Linq;
            using System.Text;
            using Newtonsoft.Json;
            using BranchXamarinSDK;

            using Android.App;
            using Android.Content;
            using Android.OS;
            using Android.Runtime;
            using Android.Views;
            using Android.Widget;

            namespace TestAndroidApp.Droid
            {
                [Activity(Label = "BranchActivity")]
                public class BranchActivity : Activity

                {
                    private string logString = "";

                    protected override void OnCreate(Bundle savedInstanceState)
                    {
                        base.OnCreate(savedInstanceState);

                        LogMessage("Branch initialization completed: ");

                        Dictionary<string, object> data = JsonConvert.DeserializeObject<Dictionary<string, object>>(Intent.GetStringExtra("BranchData"));
                        foreach (var key in data.Keys)
                        {
                            LogMessage(key + " : " + data[key].ToString());
                        }
                    }

                    #region Utils

                    void LogMessage(string message)
                    {
                        Console.WriteLine(message);
                        logString += DateTime.Now.ToLongTimeString() + "> " + message + "\n";
                    }

                    #endregion
                }
            }
            ```

        - **Create an activity to handle Branch errors: BranchErrorActivity**

            1. Right-click on the .Droid project and select <notranslate>**Add > New File...**</notranslate>
            1. Select: <notranslate>**Android > Activity**</notranslate>
            1. Rename the file: <notranslate>**BranchErrorActivity.cs**</notranslate>
            1. Enter the following code (replace 'TestAndroidApp' with the actual name of the app):

            ```csharp
            using System;
            using System.Collections.Generic;
            using System.Linq;
            using System.Text;

            using Android.App;
            using Android.Content;
            using Android.OS;
            using Android.Runtime;
            using Android.Views;
            using Android.Widget;

            namespace TestAndroidApp.Droid
            {
                [Activity(Label = "BranchErrorActivity")]
                public class BranchErrorActivity : Activity
                {
                    private string logString = "";

                    protected override void OnCreate(Bundle savedInstanceState)
                    {
                        base.OnCreate(savedInstanceState);

                        LogMessage("Branch initialization failed");
                        LogMessage("Error code: " + Intent.Extras.GetInt("ErrorCode").ToString());
                        LogMessage(Intent.Extras.GetString("ErrorMessage"));
                    }

                    #region Utils

                    void LogMessage(string message)
                    {
                        Console.WriteLine(message);
                        logString += DateTime.Now.ToLongTimeString() + "> " + message + "\n";
                    }

                    #endregion
                }
            }
            ```

        - **Initialize Branch and configure Branch session management**

            Branch must be initilialized in the OnCreate method of either the Application class or the first Activity launched by the app. The OnNewIntent method must be added to retrieve the latest link identifier when the app becomes active due to a Branch link click.

            Branch initializes asynchronously, with Branch link parameters being returned following a network call to Branch. If initialization is successful, the InitSessionComplete method will be invoked. If initialization is unsuccessful, the SessionRequestError method will be invoked. Deep link routing logic should be located in the InitSessionComplete method.

            In the code example below the following Branch initialization and session management steps have been added to MainActivity.cs:

            - An Activity to respond to the app's URI Scheme
            - An Activity is launched in `singleTask` mode
            - Override the OnCreate method and initialize the Branch SDK
            - Override the OnNewIntent method
            - Add an InitSessionComplete method for processing Branch link information (this is where deep link routing code should be located)
            - Add a SessionRequestError method to handle situations where Branch fails to initialize

            ```csharp
            using Android.App;
            using Android.Widget;
            using Android.OS;
            using BranchXamarinSDK;
            using System;
            using System.Collections.Generic;
            using Android.Content;
            using Newtonsoft.Json;

            namespace TestAndroidApp.Droid
            {
                [Activity(Label = "TestAndroidApp", MainLauncher = true, Icon = "@mipmap/icon", LaunchMode = Android.Content.PM.LaunchMode.SingleTask)]

                [IntentFilter(new[] { "android.intent.action.VIEW" },
                Categories = new[] { "android.intent.category.DEFAULT", "android.intent.category.BROWSABLE" },
                DataScheme = "testandroidapp",
                DataHost = "open")]

                [IntentFilter(new[] { "android.intent.action.VIEW" },
                Categories = new[] { "android.intent.category.DEFAULT", "android.intent.category.BROWSABLE" },
                DataScheme = "https",
                DataHost = "testandroidapp.app.link")]

                [IntentFilter(new[] { "android.intent.action.VIEW" },
                Categories = new[] { "android.intent.category.DEFAULT", "android.intent.category.BROWSABLE" },
                DataScheme = "https",
                DataHost = "testandroidapp-alternate.app.link")]

                public class MainActivity : Activity, IBranchSessionInterface
                {

                    protected override void OnCreate(Bundle savedInstanceState)
                    {
                        base.OnCreate(savedInstanceState);

                        BranchAndroid.Init(this, Resources.GetString(Resource.String.branch_key), this);
                    }

                    // Ensure we get the updated link identifier when the app becomes active
                    // due to a Branch link click after having been in the background
                    protected override void OnNewIntent(Intent intent)
                    {
                        this.Intent = intent;
                    }

                    public void InitSessionComplete(Dictionary<string, object> data)
                    {
                        //Handle custom logic based on deep link data in InitSessionComplete

                        //View all the link data in the console
                        Console.WriteLine("My Link Data: " + JsonConvert.SerializeObject(data));

                        //Preferred method: use BranchActivity created previously to handle the link data
                        //Will need to update BranchActivity with desired custom logic, to open the correct page in the app
                        (this, typeof(BranchActivity));
                        intent.PutExtra("BranchData", JsonConvert.SerializeObject(data));

                        StartActivity(intent);var intent = new Intent
                    }

                    public void SessionRequestError(BranchError error)
                    {
                        Console.WriteLine("Branch session initialization error: " + error.ErrorCode);
                        Console.WriteLine(error.ErrorMessage);

                        var intent = new Intent(this, typeof(BranchErrorActivity));
                        intent.PutExtra("ErrorCode", error.ErrorCode);
                        intent.PutExtra("ErrorMessage", error.ErrorMessage);

                        StartActivity(intent);
                    }
                }
            }
            ```

- ### Configure Branch with Xamarin Forms

    - **Change the C# project's profile to PCL 4.5 - Profile78**

        1. Right-click on the project name and select: <notranslate>**Options**</notranslate>
        1. Browse the menu to <notranslate>**Build > General**</notranslate>
        1. Change the <notranslate>**Current Profile**</notranslate> to: <notranslate>**PCL 4.5 - Profile78**</notranslate>

    - **Add the Branch SDK with NuGet**

        The Branch Xamarin SDK is available as a NuGet package. The [Branch NuGet package](https://www.nuget.org/packages/Branch-Xamarin-Linking-SDK) must be added to each of the Xamarin projects that will use Branch methods.

        1. Right-click on each project and select <notranslate>**Add > Add NuGet Packages**</notranslate>
        1. If not already present, find the <notranslate>_Microsoft BCL Build Components_</notranslate> package version 1.0.21 and add it to the project
        1. Find the <notranslate>_Branch Xamarin SDK_</notranslate> package version 3.0 and add it to the project

    - **Create a class for Branch session handling**

        Branch initializes asynchronously, with Branch link parameters being returned following a network call to Branch. If initialization is successful, the InitSessionComplete method will be invoked. If initialization is unsuccessful, the SessionRequestError method will be invoked. Deep link routing logic should be located in the InitSessionComplete method.

        1. Right-click on the C# project and select <notranslate>**Add > New File...**</notranslate>
        1. Select: <notranslate>**General > Empty Class**</notranslate>
        1. Rename the file: <notranslate>**TestXamarinFormsApp.cs**</notranslate>
        1. Enter the following code (replacing 'TestXamarinFormsApp' with the actual name of the app):

        ```csharp
        using BranchXamarinSDK;
        using System.Collections.Generic;
        using System.ComponentModel;
        using Xamarin.Forms;

        namespace TestXamarinFormsApp
        {
            public class TestXamarinFormsApp : Application, IBranchSessionInterface
            {

                public TestXamarinFormsApp()
                {
                }

                #region IBranchSessionInterface implementation

                public void InitSessionComplete(Dictionary<string, object> data)
                {
                }

                public void CloseSessionComplete()
                {
                }

                public void SessionRequestError(BranchError error)
                {
                }

                #endregion
            }
        }
        ```

    - **Create a class for handling link data**

        Branch stores link data in an object referred to as the <notranslate>**Branch Universal Object**</notranslate>, or <notranslate>**BUO**</notranslate>.

        1. Right-click on the C# project and select <notranslate>**Add > New File...**</notranslate>
        1. Select: <notranslate>**General > Empty Class**</notranslate>
        1. Rename the file: <notranslate>**TestXamarinFormsAppBUO.cs**</notranslate>
        1. Enter the following code (replace 'TestXamarinFormsApp' with the actual name of the app):

        ```csharp
        using BranchXamarinSDK;
        using System.Collections.Generic;
        using System.ComponentModel;
        using Xamarin.Forms;

        namespace TestXamarinFormsApp
        {
            public class TestXamarinFormsAppBUO : Application, IBranchBUOSessionInterface
            {

                public TestXamarinFormsAppBUO()
                {
                }

                #region IBranchBUOSessionInterface implementation

                public void InitSessionComplete(BranchUniversalObject buo, BranchLinkProperties blp)
                {
                }

                public void SessionRequestError(BranchError error)
                {
                }

                #endregion
            }
        }
        ```

    - **iOS**

        - **Create an Apple device Provisioning Profile for the app**

            1. Open Xcode and create a new project with the same name as your Xamarin iOS project
            1. On the Xcode project's <notranslate>**General**</notranslate> tab, enter the app's Bundle Identifier and select the appropriate Team (be sure to resolve any errors here)
            1. Select the <notranslate>**Capabilities**</notranslate> tab and enable the <notranslate>**Associated Domains**</notranslate> entitlement
            1. Create 'applinks:' entries for the Branch link domain assigned to the app (the link domain can be found at the bottom of the Branch dashboard's [Link Settings](https://dashboard.branch.io/#/settings/link) page). For example, the entries for the app <notranslate>*TestXamarinFormsApp*</notranslate> would be:
            &nbsp;&nbsp;&nbsp;&nbsp;`applinks:testxamarinformsapp.app.link`
            &nbsp;&nbsp;&nbsp;&nbsp;`applinks:testxamarinformsapp-alternate.app.link`
            1. Use Xcode to run this newly-created app on an iOS device. This will create and install a Provisioning Profile with the proper entitlements on that device.
            1. Close Xcode

        - **Enter the app's settings on the Branch dashboard**

            1. On the [Link Settings](https://dashboard.branch.io/#/settings/link) page, check the <notranslate>**I have an iOS App**</notranslate> checkbox
            1. Enter the app's URI Scheme in the <notranslate>**iOS URI Scheme**</notranslate> field (for an app with the URI Scheme <notranslate>*testxamarinformsapp*</notranslate>, for example, the entry would be: `testxamarinformsapp://`)
            1. Enter the app's Apple Store name in the <notranslate>**Apple Store Search**</notranslate> field (if the app is not yet available on the App Store select <notranslate>**Custom URL**</notranslate> and enter as a placeholder the URL of an appropriate web site - the exact site does not matter)
            1. Check the <notranslate>**Enable Universal Links**</notranslate> checkbox
            1. Enter the app's Bundle Identifier and Apple App Prefix as shown on the [Apple Developer Portal](https://developer.apple.com/account/ios/identifier/bundle)

        - **Configure the Xamarin project's Info.plist file**

            1. Open the <notranslate>**Info.plist**</notranslate> file
            1. Enter the app's <notranslate>**Bundle Identifier**</notranslate> from the [Apple Developer Portal](https://developer.apple.com/account/ios/identifier/bundle) in the <notranslate>**Bundle Identifier**</notranslate> field. <notranslate>**IMPORTANT:**</notranslate> this field will automatically be populated with an all-lowercase value by Xamarin. The value is in fact case sensitive and must match the value in the [Apple Developer Portal](https://developer.apple.com/account/ios/identifier/bundle) precisely.
            1. Click on the <notranslate>**Advanced**</notranslate> tab
            1. In the <notranslate>**URL Types**</notranslate> section, click the <notranslate>**Add URL Type**</notranslate> button
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<notranslate>**Identifier:**</notranslate> Branch Scheme
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<notranslate>**URL Schemes:**</notranslate> {the app's URI Scheme - 'testxamarinformsapp', for example}
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<notranslate>**Role:**</notranslate> Editor

            ![image](/images/pages/apps/xamarin/ios_uri_scheme.png)

        - **Configure the Xamarin project's Associated Domains entitlement**

            1. Open the <notranslate>**Entitlements.plist**</notranslate> file and browse to <notranslate>**Associated Domains**</notranslate> (if this file does not already exist, create it)
            1. Create entries for both the app's link domain and its alternate link domain. The entries for the TestBed-Xamarin app would be:
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`applinks:testxamarinformsapp.app.link`
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`applinks:testxamarinformsapp-alternate.app.link`

            ![image](/images/pages/apps/xamarin/ios_associated_domains.png)

        - **Add Branch calls to the AppDelegate.cs file**

            To ensure that the Branch SDK initializes when the app starts and can retrieve link parameters whenever the app becomes active, Branch initialization occurs within the `FinishedLaunching` method of the AppDelegate.cs file. Branch calls are also required in the OpenUrl, ContinueUserActivity, and ReceiveRemoteNotification methods to ensure that Branch link information is handled properly whenever the app becomes active. The <notranslate>**AppDelegate.cs**</notranslate> file should look like this:

            ```csharp
            using System;
            using System.Collections.Generic;
            using System.Linq;

            using Foundation;
            using UIKit;
            using BranchXamarinSDK;
            using TestXamarinFormsApp;

            namespace TestXamarinFormsApp.iOS
            {
                [Register("AppDelegate")]
                public partial class AppDelegate : global::Xamarin.Forms.Platform.iOS.FormsApplicationDelegate
                {
                    public override bool FinishedLaunching(UIApplication app, NSDictionary options)
                    {
                        global::Xamarin.Forms.Forms.Init();

                        // Debug mode - set to 'false' before releasing to production
                        BranchIOS.Debug = true;

                        TestXamarinFormsAppBUO appBUO = new TestXamarinFormsAppBUO();
                        BranchIOS.Init("key_live_liAnF8k7gZUEZv76Rt9a4bffAzlC5zVW", options, appBUO);
                        LoadApplication(appBUO);

                        return base.FinishedLaunching(app, options);
                    }

                    // Called when the app is opened via URI scheme
                    public override bool OpenUrl(UIApplication application, NSUrl url, string sourceApplication, NSObject annotation)
                    {
                        return BranchIOS.getInstance().OpenUrl(url);
                    }

                    // Called when the app is opened from a Universal Link
                    public override bool ContinueUserActivity(UIApplication application, NSUserActivity userActivity, UIApplicationRestorationHandler completionHandler)
                    {
                        return BranchIOS.getInstance().ContinueUserActivity(userActivity);
                    }

                    // Called when the app receives a push notification
                    public override void ReceivedRemoteNotification(UIApplication application, NSDictionary userInfo)
                    {
                        BranchIOS.getInstance().HandlePushNotification(userInfo);
                    }
                }
            }
            ```

    - **Android**

        - **Ensure that the Android project is not using the Shared Mono Runtime**

            1. Right-click on the Android project and select: <notranslate>**Options**</notranslate>
            1. Select: <notranslate>**Android Build**</notranslate>
            1. On the <notranslate>**General**</notranslate> tab, un-check: <notranslate>**Use Shared Mono Runtime**</notranslate>

        - <notranslate>**Add app capabilities in the AndroidManifest.xml file**</notranslate>

            In the *Required permissions* section of <notranslate>**AndroidManifest.xml**</notranslate>, configure the following permissions:

            - *AccessNetworkState*
            - *Internet*

            Additional reading on the Android manifest

            - [Working with android manifest.xml](https://developer.xamarin.com/guides/android/advanced_topics/working_with_androidmanifest.xml/)
            - [Add permissions to android manifest](https://developer.xamarin.com/recipes/android/general/projects/add_permissions_to_android_manifest/)

        - **Add the app's Branch key to the Strings.xml file**

            Create a <notranslate>**Resources/values/Strings.xml**</notranslate> file that can be accessed by the app's Application class for the Android project and add the Branch key to this file.

            1. In the Android project, browse to <notranslate>**Resources/values**</notranslate>
            1. Right-click on the <notranslate>**values**</notranslate> folder and select: <notranslate>**Add > New File...**</notranslate>
            1. Select: <notranslate>**XML > Empty XML File**</notranslate>
            1. Name the file: <notranslate>**Strings**</notranslate>
            1. Enter the following values:

            ```xml
            <?xml version="1.0" encoding="utf-8"?>
            <resources>
                <string name="app_name">TestXamarinFormsApp</string>
                <string name="branch_key">key_live_liAnF8k7gZUEZv76Rt9a4bffAzlC5zVW</string>
            </resources>
            ```

        - **Configure the .Droid project's Application class**

            Within the .Droid project's Application class:

            - Set the Branch SDK's initialization parameters
            - Override the `OnCreate()` method to call `BranchAndroid.GetAutoInstance`

            If an Appplication class does not already exist for the project, create one:

            1. Right-click on the .Droid project and select: <notranslate>**Add > New File...**</notranslate>
            1. Select: <notranslate>**General > Empty Class**</notranslate>
            1. Name the file: _{app name}_ ('TestXamarinFormsApp', for example)

            The file should have the following contents:

            ```csharp
            using System;
            using Android.App;
            using Android.Content;
            using Android.Runtime;
            using BranchXamarinSDK;

            namespace TestXamarinFormsApp.Droid
            {

                [Application (AllowBackup = true, Icon = "@drawable/icon", Label = "@string/app_name")]
                [MetaData("io.branch.sdk.auto_link_disable", Value = "false")]
                [MetaData("io.branch.sdk.TestMode", Value = "true")]
                [MetaData("io.branch.sdk.BranchKey", Value = "@string/branch_key")]

                public class App : Application
                {
                    public App(IntPtr javaReference, JniHandleOwnership transfer) : base(javaReference, transfer)
                    {
                    }

                    public override void OnCreate()
                    {
                        base.OnCreate();
                        BranchAndroid.GetAutoInstance(this.ApplicationContext);
                    }
                }
            }
            ```

            | Key | Value
            | --- | ---
            | `io.branch.sdk.TestMode` | Setting this parameter to *true* enables Debug Mode, which causes simple uninstall/reinstalls of the app to trigger *install* events. Be sure to disable this before deploying to production. Note that enabling Debug Mode on Android also forces the app to use the Branch *Test* key if this key has been added to the project. Apps running with a *Test* key will be unable to receive data from Branch links created with the *Live* key.
            | `io.branch.sdk.BranchKey` | The app's Branch key. Both a *Live* key and a *Test* key can be added to the Strings.xml file. When *Test* Mode is enabled the app will automatically use the *Test* key, if one has been specified.

        - **Initialize Branch**

            Branch must be initilialized in the OnCreate method of either the Application class or the first Activity launched by the app. The OnNewIntent method must be added to retrieve the latest link identifier when the app becomes active due to a Branch link click.

            In the code example below the following Branch initialization and session management steps have been added to MainActivity.cs:

            - Register an Activity to respond to the app's URI Scheme
            - Ensure the Activity is launched in `singleTask` mode
            - Override the OnCreate method and initialize the Branch SDK
            - Override the OnNewIntent method

            ```csharp
            using System;

            using Android.App;
            using Android.Content;
            using Android.Content.PM;
            using Android.Runtime;
            using Android.Views;
            using Android.Widget;
            using Android.OS;

            using BranchXamarinSDK;
            using TestXamarinFormsApp;

            namespace TestXamarinFormsApp.Droid
            {
                [Activity(Label = "TestXamarinFormsApp.Droid", LaunchMode = LaunchMode.SingleTask, Icon = "@drawable/icon", Theme = "@style/MyTheme", MainLauncher = true, ConfigurationChanges = ConfigChanges.ScreenSize | ConfigChanges.Orientation)]

                [IntentFilter(new[] { "android.intent.action.VIEW" },
                    Categories = new[] { "android.intent.category.DEFAULT", "android.intent.category.BROWSABLE" },
                    DataScheme = "testxamarinformsapp",
                    DataHost = "open")]

                [IntentFilter(new[] { "android.intent.action.VIEW" },
                    Categories = new[] { "android.intent.category.DEFAULT", "android.intent.category.BROWSABLE" },
                    DataScheme = "https",
                    DataHost = "testxamarinformsapp.app.link")]

                public class MainActivity : global::Xamarin.Forms.Platform.Android.FormsApplicationActivity
                {
                    protected override void OnCreate(Bundle savedInstanceState)
                    {
                        base.OnCreate(savedInstanceState);

                        global::Xamarin.Forms.Forms.Init(this, savedInstanceState);

                        TestXamarinFormsAppBUO linkData = new TestXamarinFormsAppBUO();
                        BranchAndroid.Init(this, GetString(Resource.String.branch_key), linkData);
                        LoadApplication(linkData);
                    }

                    protected override void OnNewIntent(Intent intent)
                    {
                        this.Intent = intent;
                    }
                }
            }
            ```

- ### Test deep link iOS

    - Create a deep link from the [Branch Marketing Dashboard](https://dashboard.branch.io/marketing)

    - Delete your app from the device

    - Compile your app with Xcode

    - Paste deep link in <notranslate>**Apple Notes**</notranslate>
    - Long press on the deep link *(not 3D Touch)*

    - Click <notranslate>**Open in "APP_NAME"**</notranslate> to open your app *([example](/images/pages/apps/ios-notes.png))*

- ### Test deep link Android

    - Create a deep link from the [Branch Marketing Dashboard](https://dashboard.branch.io/marketing)

    - Delete your app from the device

    - Compile your app with Android Studio

    - Paste deep link in <notranslate>**Google Hangouts**</notranslate>

    - Click on the deep link to open your app

## Implement features

- ### Create content reference

    - The <notranslate>**Branch Universal Object**</notranslate> encapsulates the thing you want to share

    - Uses [Universal Object properties](/links/integrate/#universal-object)

    ```csharp
    BranchUniversalObject universalObject = new BranchUniversalObject();
    universalObject.canonicalIdentifier = "id12345";
    universalObject.title = "id12345 title";
    universalObject.contentDescription = "My awesome piece of content!";
    universalObject.imageUrl = "https://s3-us-west-1.amazonaws.com/branchhost/mosaic_og.png";
    universalObject.metadata.Add("foo", "bar");
    ```

- ### Create deep link

    - Generates a deep link within your app

    - Needs a [Create content reference](#create-content-reference)

    - Needs a [Create link reference](#create-link-reference)

    - Validate with the [Branch Dashboard](https://dashboard.branch.io/liveview/links)

    ```csharp
    BranchLinkProperties linkProperties = new BranchLinkProperties();
    linkProperties.tags.Add("tag1");
    linkProperties.tags.Add("tag2");
    linkProperties.feature = "sharing";
    linkProperties.channel = "facebook";
    linkProperties.controlParams.Add("$desktop_url", "http://example.com");

    Branch.GetInstance().GetShortURL(callback,
                                      universalObject,
                                      linkProperties);
    ```

- ### Share deep link

    -  Will generate a Branch deep link and tag it with the channel the user selects

    - Needs a [Create content reference](#create-content-reference)

    - Needs a [Create link reference](#create-link-reference)

    - Uses [Deep Link Properties](/links/integrate/)

    ```csharp
    ShareLink (IBranchLinkShareInterface callback,
               BranchUniversalObject universalObject,
               BranchLinkProperties linkProperties,
               string message)
    ```

- ### Read deep link

    - Retrieve Branch data from a deep link

    - Best practice to receive data from the `listener` (to prevent a race condition)

    - Returns [deep link properties](/links/integrate/#read-deep-links)

    ```csharp
    // latest
    Dictionary<string, object> sessionParams = Branch.GetInstance().GetLatestReferringParams();

    // first
    Dictionary<string, object> installParams = Branch.GetInstance().GetFirstReferringParams();

    ```

- ### Track users

    - Sets the identity of a user (email, ID, UUID, etc) for events, deep links, and referrals

    - Validate with the [Branch Dashboard](https://dashboard.branch.io/liveview/identities)

    ```csharp
    Branch branch = Branch.GetInstance ();
    branch.SetIdentity("the user id", this);  // Where this implements IBranchIdentityInterface
    branch.Logout(this); // Where this implements IBranchIdentityInterface
    ```

- ### Track events

    - Registers a custom event

    - Events named `open`, `close`, `install`, and `referred session` are Branch restricted

    - Best to [Track users](#track-users) before [Track events](#track-events) to associate a custom event to a user

    - Validate with the [Branch Dashboard](https://dashboard.branch.io/liveview/events)

    ```csharp
    Branch branch = Branch.GetInstance ();
    branch.LogEvent("the_custom_event");
    ```

- ### Track commerce

    - Registers a custom commerce event

    - Uses [Track commerce properties](#commerce-properties) for `Currency` and `Category`

    - Validate with the [Branch Dashboard](https://dashboard.branch.io/liveview/commerce)

    ```csharp
    Branch branch = Branch.GetInstance ();
    Dictionary<string, object> data = new Dictionary<string, object>();
    data.Add("sku", "123456789");
    branch.LogEvent("purchase_event", data);
    ```

- ### Handle referrals

    - Referral points are obtained from referral rules on the [Branch Dashboard](https://dashboard.branch.io/referrals/rules)

    - Validate on the [Branch Dashboard](https://dashboard.branch.io/referrals/analytics)

    - Reward credits

        -  [Referral guide](/dashboard/analytics/#referrals)

    - Redeem credits

        ```csharp
        Branch branch = Branch.GetInstance ();
        branch.RedeemRewards(this, amount, bucket);

        #region IBranchRewardsInterface implementation

                public void RewardsLoaded ()
                {
                    // Do something with the data...
                }

                public void RewardsRedeemed ()
                {
                    // Do something with the data...
                }

                public void CreditHistory (List<CreditHistoryEntry> history)
                {
                    // Do something with the data...
                }

                public void RewardsRequestError (BranchError error)
                {
                 // Do something with the data...
                }

                #endregion

        ```

    - Load credits

        ```csharp
        Branch branch = Branch.GetInstance ();
        branch.LoadRewards(this);

        #region IBranchRewardsInterface implementation

                public void RewardsLoaded ()
                {
                    // Do something with the data...
                }

                public void RewardsRedeemed ()
                {
                    // Do something with the data...
                }

                public void CreditHistory (List<CreditHistoryEntry> history)
                {
                    // Do something with the data...
                }

                public void RewardsRequestError (BranchError error)
                {
                    // Do something with the data...
                }

        #endregion
        ```

    - Load history

        ```csharp
        Branch branch = Branch.GetInstance ();
        branch.GetCreditHistory(this);

        ```

## Troubleshoot issues

- ### Unable to add Branch-required NuGet packages to the C# project

    Adding required NuGet packages to the C# project may fail if the project has not been configured to use <notranslate>**PCL 4.5 - Profile78**</notranslate>

    1. Right-click on the project name and select: <notranslate>**Options**</notranslate>
    1. Browse the menu to <notranslate>**Build > General**</notranslate>
    1. Change the <notranslate>**Current Profile**</notranslate> to: <notranslate>**PCL 4.5 - Profile78**</notranslate>

- ### Android app fails to build with linking errors

    The Newtonsoft JSON NuGet package is automatically added to a project when the Branch Xamarin SDK NuGet package is added. There is a known issue with this package that results in linking errors when building a project.

    error XA0009: Error while loading assembly: /Users/david/Projects/TestXamarinFormsApp/Droid/obj/Debug/android/assets/mscorlib.dll

    To resolve this issue with the Newtonsoft JSON NuGet package:

    1. Right-click on the project and select Options
    1. Go to <notranslate>**Android Build**</notranslate> and select the <notranslate>**Linker**</notranslate> tab
    1. Select: <notranslate>**Release**</notranslate>
    1. Go to the <notranslate>**Ignore assemblies**</notranslate> box
    1. Add: <notranslate>**System.Core**</notranslate>
    1. Rebuild the app

- ### Deploying iOS app to device fails with Provisioning Profile erros after changing entitlements

    Xamarin automatically populates the <notranslate>**Bundle Identifier**</notranslate> field in the <notranslate>**Info.plist**</notranslate> file with an all-lowercase value derived from the app's name. This value is in fact case sensitive and must match the value in the [Apple Developer Portal](https://developer.apple.com/account/ios/identifier/bundle) precisely. The default Xamarin configuration may work when there are no entitlements configured and then suddenly begin failing after entitlements have been added.

    This issue can be resolved by ensuring that the <notranslate>**Bundle Identifier**</notranslate> in the <notranslate>**Info.plist**</notranslate> matches the <notranslate>**Bundle Identifier**</notranslate> shown on the [Apple Developer Portal](https://developer.apple.com/account/ios/identifier/bundle).

    1. Open the <notranslate>**Info.plist**</notranslate> file
    1. Enter the app's <notranslate>**Bundle Identifier**</notranslate> from the [Apple Developer Portal](https://developer.apple.com/account/ios/identifier/bundle) in the <notranslate>**Bundle Identifier**</notranslate> field

- ### Sample apps

    There are four fully-functional demo apps included in this repository: a Xamarin Native and Xamarin Forms apps for both iOS and Android platforms. Use these apps as reference models for integrating the Branch SDK.

    - <notranslate>**Testbed-Xamarin (Native apps)**</notranslate>

        - [iOS](https://github.com/BranchMetrics/xamarin-branch-deep-linking/tree/master/Examples/ios_example)
        - [Android](https://github.com/BranchMetrics/xamarin-branch-deep-linking/tree/master/Examples/droid_example)

    - <notranslate>**Testbed-XamarinForms (Forms apps)**</notranslate>

        - [iOS](https://github.com/BranchMetrics/xamarin-branch-deep-linking/tree/master/Branch-Xamarin-Testbed.iOS)
        - [Android](https://github.com/BranchMetrics/xamarin-branch-deep-linking/tree/master/Branch-Xamarin-Testbed.Droid)
