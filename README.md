# MultiDex Offline
A [Context](https://developer.android.com/reference/android/content/Context.html)-less version of [MultiDex Suport library](https://developer.android.com/reference/android/support/multidex/MultiDex.html), this modified version for those cases where the context is unknown (like in a xposed module).

Modified version based on 2.0.1 from androidx (tree 652081201e50f0766dcfd7c650ef91d417f48597).

```java
    public class MultiDexOffline {
        public static void install(
            SharedPreferences prefs,
            ApplicationInfo applicationInfo,
            String filesDir,
            ClassLoader classLoader
        );
    }
```

## Summary:
Patches the application context class loader in the desired app by appending extra dex files
loaded from the application apk. This method should be called once.

## Parameters:
* **prefs**        where save preference and to get the current dex version
* **filesDir**     Application private storage path, normally obtained from Context.getFilesDir()
* **classLoader**  classloader to patch.
* _throws_ **RuntimeException** if an error occurred preventing the classloader extension.

## Notes:
* Please use `MultiDexExtractor.PREFS_FILE` for the prefences filename, inside of **shared_prefs** folder under private files app.
  Example `/data/data/com.example.app/shared_prefs/multidex.version`.
* If the target app already has the MultiDex support library, will be installed anyway (cannot be detected)
