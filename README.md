StyleNTheme
==============

There are two ways to set a style:
To an individual View, by adding the style attribute to a View element in the XML for your layout.
Or, to an entire Activity or application, by adding the android:theme attribute to the <activity> or<application> element in the Android manifest.
Style
Defining and Using Styles
res/values/styles.xml
<style name="LargeRedFont">
    <item name="android:textColor">#C80000</item>
    <item name="android:textSize">40sp</item>
</style>
<TextView
  android:id="@+id/tv_text"
  style="@style/LargeRedFont"
  android:layout_width="wrap_content"
  android:layout_height="wrap_content"
  android:text="@string/hello_world" />
Inheriting Styles :There are two ways of defining parents
Implicit:  Inherit from styles that you've defined yourself, you do not have to use the parent attribute.
  <style name="CodeFont.Red">
        <item name="android:textColor">#FF0000</item>
    </style>
Explicit: Inherit the Android platform's default text appearance and then modify it:
    <style name="GreenText" parent="@android:style/TextAppearance">
        <item name="android:textColor">#00FF00</item>
    </style>
Rule: DO NOT mix implicit and explicit parenting. This technique for inheritance by chaining together names only works for styles defined by your own resources. You can't inherit Android built-in styles this way. To reference a built-in style, such asTextAppearance, you must use the parent attribute.
Style Properties :
The best place to find properties that apply to a specific View is the corresponding class reference, which lists all of the supported XML attributes. For example, all of the attributes listed in the table of TextView XML attributes can be used in a style definition for a TextView element .
If you apply a style to a View that does not support all of the style properties, the View will apply only those properties that are supported and simply ignore the others.
For a reference of all available style properties, see the R.attr
You can find a reference of all available styles in the R.style
When to use style
Rule #1: Use styles when multiple Views are semantically identical.
You're creating a calculator. Each button should look the same, so it makes sense to create a CalculatorButton style.
You've got a couple screens with multiple text formats - say, headers, subheaders, and text. You can unify their look by creating Header, Subheader and Text styles.
You've got thumbnails all over your app. You want them all to look the same. The Thumbnail style is born.
Rule #2: Use references within styles when appropriate.
Theme
Apply a theme to an Activity or application: To apply a style definition as a theme, you must apply the style to an Activity or application in the Android manifest. When you do so, every View within the Activity or application will apply each property that it supports.
To set a theme for all the activities of your application,
<application android:theme="@style/CustomTheme">
If you want a theme applied to just one Activity in your application
<activity android:theme="@android:style/Theme.Dialog">
If you like a theme, but want to tweak it
<style name="CustomTheme" parent="android:Theme.Light">
    <item name="android:windowBackground">@color/custom_theme_color</item>
    <item name="android:colorBackground">@color/custom_theme_color</item>
</style>
Note that the color needs to supplied as a separate resource here because the android:windowBackgroundattribute only supports a reference to another resource; unlike android:colorBackground, it can not be given a color literal
<activity android:theme="@style/CustomTheme">
Select a theme based on platform version : To accomplish  additional themes available in newer versions of Android while still being compatible with older versions:
When and how to use the holo design : As of API 14 and before API 21 the holo design can be used.
@android:style/Theme.Holo
@android:style/Theme.Holo.Light
@android:style/Theme.Holo.Light.DarkActionBar

res/values/styles.xml
<style name="LightThemeSelector" parent="android:Theme.Light">
    ...
</style>
res/values-v11 : Thistheme use the newer holographic theme when the application is running on Android 3.0
<style name="LightThemeSelector" parent="android:Theme.Holo.Light">
    ...
</style>
Where to look for system style and theme
A list of the standard attributes that you can use in themes can be found at R.styleable.Theme.
You can find a reference of all available styles in the R.style class. To use the styles listed here, replace all underscores in the style name with a period. For example, you can apply the Theme_NoTitleBar theme with"@android:style/Theme.NoTitleBar".
For a better reference to the Android styles and themes, see the following source code:
Android Styles (styles.xml)
Android Themes (themes.xml)
Theme vs Style: TL;DR: Themes are global, styles are local.
Appcompat v21: material design for pre-Lollipop devices!
appcompat-v7:22.2.1 Hiraricy Structure:

Theme.AppCompat
<style name="Theme.AppCompat" parent="Base.Theme.AppCompat"/>
    values.xml
        <style name="Base.Theme.AppCompat" parent="Base.V7.Theme.AppCompat">
            <style name="Base.V7.Theme.AppCompat" parent="Platform.AppCompat">
    values-21.xml
        <style name="Base.Theme.AppCompat" parent="Base.V21.Theme.AppCompat"/>
            <style name="Base.V21.Theme.AppCompat"parent="Base.V7.Theme.AppCompat">
Platform.AppCompat
values.xml
    <style name="Platform.AppCompat" parent="android:Theme">
        <style name="Platform.AppCompat" parent="android:Theme">
            <style name="Theme">
values-11.xml
    <style name="Platform.AppCompat" parent="Platform.V11.AppCompat"/>
        <style name="Platform.V11.AppCompat" parent="android:Theme.Holo">
            <style name="Theme.Holo">
values-14.xml
    <style name="Platform.AppCompat" parent="Platform.V14.AppCompat"/>
        <style name="Platform.V14.AppCompat" parent="Platform.V11.AppCompat">
values-21.xml
    <style name="Platform.AppCompat" parent="android:Theme.Material">
        <style name="Theme.Material">
Reference
http://developer.android.com/guide/topics/ui/themes.html
https://guides.codepath.com/android/Styles-and-Themes
https://www.youtube.com/watch?v=NKLX5yPYWVo
http://blog.danlew.net/2014/11/19/styles-on-android/
GreenMatters app for themehttps://github.com/negusoft/greenmatter
http://chris.banes.xyz/2014/11/12/theme-vs-style/
http://chris.banes.xyz/2014/11/12/theme-vs-style/