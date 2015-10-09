[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-PreferenceInjector-brightgreen.svg?style=flat)](https://android-arsenal.com/details/1/1569)


# PrefCompat

PrefCompat is a wrapper over the SharedPreference class in Android. It supports storing objects other than the standard primitives while decreasing the boiler plate code. It uses java annotations to bind listeners on SharedPreference changes.

 How to Use
-------

#### Basic Usage

First initialize the PrefCompat library in your Application class.

```java
public class Application extends android.app.Application {
    @Override
    public void onCreate() {
        super.onCreate();
        Pref.init(this);
    }
}
```

Then, use the Pref class to store and access data in SharedPreferences.

```java
public class MainActivity extends Activity {

    @Override public void onCreate(Bundle inState) {
        // Default SharedPreferences
        Pref.putString("name", "Tushar");
        Pref.putDouble("weight", 79.24);
        Pref.putObject("dependents", new Dependent("Radhika", 62.24));

        Double weight = Pref.getDouble("weight");
        Dependent mom = Pref.getObject("dependents", Dependent.class);

        // Named SharedPreferences can also be used
        Pref.from("Scores").putIntList("level_1", [60, 20, 80, 25, 30]);

        List<Integer> scores = Pref.from("Scores").getIntList("level_1");
    }
}
```
