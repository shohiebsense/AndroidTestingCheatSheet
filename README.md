# AndroidTestingCheatSheet

0. Setup

```gradle
   android {
   testOptions {
        unitTests {
            includeAndroidResources = true
        }
      }
    }
    
    dependencies{
    androidTestImplementation 'androidx.test:core:1.3.0-alpha03'
    androidTestImplementation 'androidx.test.espresso:espresso-core:3.2.0'
    androidTestImplementation 'androidx.test:rules:1.2.0'
    androidTestImplementation 'androidx.test:runner:1.3.0-alpha03'
    
    //add ui automator if it's necessary
    }
```
use the latest version.


1. Make some delay during test
https://stackoverflow.com/questions/21417954/espresso-thread-sleep

```java
onView(isRoot()).perform(waitFor(5000));
```

2. Type Text
```java
onView(withId(R.id.edit_text)).perform(typeText("LOVE"));
```

3. Click
```java
onView(withId(R.id.button_next)).perform(click());
```

4. Click listview item
```java
onData(anything()).inAdapterView(withId(R.id.list_view)).atPosition(0).perform(click());
```
5. Get Current Device (UI Automator)
```kt
uiDevice = UiDevice.getInstance(getInstrumentation())
uiDevice.pressHome()
```
6. Get current Activity 
```kt
fun getActivityInstance() : Activity {
        var activity = arrayListOf<Activity>()
        getInstrumentation().runOnMainSync {
            val resumedActivity = ActivityLifecycleMonitorRegistry.getInstance().getActivitiesInStage(Stage.RESUMED)
            var it = resumedActivity.iterator()
            activity.add(it.next())
        }
        return activity[0]
    }
```

7. swipe viewpager
```kt
 onView(allOf(withId(R.id.view_pager_enrollment_attendance), isDisplayed())).perform(
            swipeLeft())
```

8. getViiew from ui automator
```kt

uiDevice.findObject(By.res(PACKAGE_NAME,"button_save"))
```

9. Get Recyclerview
```kt
 onView(allOf(ViewMatchers.withId(R.id.recycler_menu), isDisplayed())).perform(
            RecyclerViewActions.actionOnItemAtPosition<RecyclerView.ViewHolder>(2, click())
        )
```

10. getpackage name
```kt
  private fun getLauncherPackageName(): String {
        // Create launcher Intent
        val intent = Intent(Intent.ACTION_MAIN)
        intent.addCategory(Intent.CATEGORY_HOME)

        // Use PackageManager to get the launcher package name
        val pm = getApplicationContext<Context>().getPackageManager()
        val resolveInfo = pm.resolveActivity(intent, PackageManager.MATCH_DEFAULT_ONLY)
        return resolveInfo!!.activityInfo.packageName
    }
```


