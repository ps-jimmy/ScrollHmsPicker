[![Android Arsenal]( https://img.shields.io/badge/Android%20Arsenal-ScrollHmsPicker-green.svg?style=flat)]( https://android-arsenal.com/details/1/6805)
[![Newest version](https://jitpack.io/v/DeweyReed/ScrollHmsPicker.svg)](https://jitpack.io/#DeweyReed/ScrollHmsPicker)
[![Translation-ZH](https://img.shields.io/badge/Translation-%E4%B8%AD%E6%96%87-red.svg)](https://github.com/DeweyReed/ScrollHmsPicker/blob/master/README-ZH.md#scrollhmspicker)

# ScrollHmsPicker

A simple HMS time picker with scrolling.

## Screenshots

| Default Dialog | Theme It! | In the XML |
|:-:|:-:|:-:|
| ![Default Dialog](https://github.com/DeweyReed/ScrollHmsPicker/blob/master/art/default.png?raw=true) | ![Theme It!](https://github.com/DeweyReed/ScrollHmsPicker/blob/master/art/theme.png?raw=true) | ![In the XML](https://github.com/DeweyReed/ScrollHmsPicker/blob/master/art/xml.png?raw=true) |

## Install

Step 1. Add the JitPack repository to your build file

Add it in your root build.gradle at the end of repositories:

```Groovy
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}
```

Step 2. Add the dependency => [![Newest version](https://jitpack.io/v/DeweyReed/ScrollHmsPicker.svg)](https://jitpack.io/#DeweyReed/ScrollHmsPicker)

```Groovy
dependencies {
    implementation 'com.github.DeweyReed:ScrollHmsPicker:$version'
}
```

## Usage

### XML

```XML
<io.github.deweyreed.scrollhmspicker.ScrollHmsPicker
    android:id="@+id/scrollHmsPicker"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" />
```

Then, use `scrollHmsPicker.getHours()` to get users' input.

### Show a dialog fragment

Implement `ScrollHmsPickerDialog.HmsPickHandler` for your activity or whatever.

```Kotlin
class MainActivity : AppCompatActivity(), ScrollHmsPickerDialog.HmsPickHandler {
```

```Kotlin
override fun onHmsPick(reference: Int, hours: Int, minutes: Int, seconds: Int) {
    longToast("reference: $reference, hours: $hours, minutes: $minutes, seconds: $seconds")
}
```

Then, build it.

```Kotlin
ScrollHmsPickerBuilder(supportFragmentManager, this)
    .setReference(255)
    .setTime(1, 23, 45)
    .setAutoStep(true)
    .setColorNormal(android.R.color.holo_blue_light)
    .setColorSelected(android.R.color.black)
    .setColorBackground(android.R.color.holo_orange_light)
    .setDismissListener(DialogInterface.OnDismissListener {
        toast("Dismiss")
    })
    .show()
```

## Attributes

|attribute|xml|default|means|
|:-:|:-:|:-:|:-:|
|setHours|shp_hours|0(Int)|set picker's hours|
|setMinutes|shp_minutes|0(Int)|set picker's minutes|
|setSeconds|shp_seconds|0(Int)|set picker's seconds|
|setColorNormal|shp_normal_color|android.R.color.darker_gray(color resource)|set picker's not selected text color|
|setColorSelected|shp_selected_color|android.R.color.holo_red_light(color resource)|set picker's selected text color|
|setAutoStep|shp_auto_step|false(Boolean)|let picker automatically increment 1 minute if seconds move from 59 to 00 or increment 1 hour if minutes move from 59 to 00|

## License

[MIT License](https://github.com/DeweyReed/ScrollHmsPicker/blob/master/LICENSE)
