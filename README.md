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
    }
```
use the latest version.


1. Make some delay during test
https://stackoverflow.com/questions/21417954/espresso-thread-sleep

```java
onView(isRoot()).perform(waitFor(5000));
```

2. 
