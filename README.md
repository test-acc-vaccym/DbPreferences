# DB Preferences

[![GitHub license](https://img.shields.io/badge/license-Apache%20Version%202.0-blue.svg)](https://github.com/sbrukhanda/fragmentviewpager/blob/master/LICENSE.txt)
[![](https://jitpack.io/v/hannesa2/DbPreferences.svg)](https://jitpack.io/#hannesa2/DbPreferences)


An encrypted alternative to SharedPreferences. It's based on SQlite and uses sqlcipher

### Usage

##### Create an instance of DBPrefs and use get() or put() methodes on it

You need an enum which implements ConfigKey to access values, eg.

###### Kotlin
```Kotlin
public enum MyConfigKeys implements ConfigKey {
    KEY_OBJECT_A, // your key A
    KEY_STRING_B; // your key B ... and so on
}
```

and init it with your secret
```Kotlin
class MyApplication : Application() {

    override fun onCreate() {
        super.onCreate()

        DBPrefs.init(this, "your secret")
    }
    ...
 }
 ```   

###### Java
```java
// get it
TestClass testClass = new DBPrefs().get(MyConfigKeys.KEY_OBJECT_A, TestClass.class);

// or save
new DBPrefs().put(MyConfigKeys.KEY_OBJECT_A, testClassToStore);
```
###### Kotlin
```kotlin
// get
val testClass = DBPrefs().get<TestClass>(MyConfigKeys.KEY_OBJECT_A, TestClass::class.java)
//or save
DBPrefs().put(MyConfigKeys.KEY_OBJECT_A, testClassToStore)
```

That's it !

## Download 
Repository available on https://jitpack.io

```Gradle
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}
```
```Gradle
dependencies {
    implementation 'com.github.hannesa2:DbPreferences:1.1'
}

```

## License 
```
Copyright 2018 Hannes Achleitner

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```


