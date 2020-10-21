---
layout: collection_item
title:  "Android development Notes fundamental with kotlin"
category: kotlin
tags: kotlin
---

## Things to keep in res folder

* images
* text strings
* screen layouts
* styles
* values
* hexadecimal colors
* dimensions


## Android Manifest

* Keeps informations of the app (eg, Activity, launcher action, permissions)

## build.graddle(Module)
Contains configuration that are common for all modules

## build.graddle(app)
Contains configuration for app module <br>
eg. Changing sdk level, adding dependencies

## Import XML designing notes:
### Properties
#### `layout_width` or `layout_height`:
* `match_parent`: Matches with the size of its parent
* `wrap_content`: Fit the size to its content
* 10dp (xdp): Set a specific density independent pixel (adjusted to screen density)

## Gravity:
```kotlin
android:layout_graivity
```
* `center_horizontal`: Center itself horizontally
* `center_vertical`: Center itself vertically

## Important Text properties
`android:textSize`
* 10sp (xsp): set specific scalable pixel (adjusted to screen density and user text size preference)


## Enable Vector drawable for api level under 21
Go to your build.graddle(Module: app) file and add this line to your defaultConfig

```
vectorDrawables.useSupportLibrary = true
```

## Layout Design guideline:
### Margin left/start and Margin right/end
From android api 17 the `paddingLeft`, `layout_marginLeft` is changed to `paddingStart`, `layout_marginStart`<br>
but when we also want to make the style compitable with api level 16 or lower versions we need to use both attributes<br>
For example, use both `android:paddingLeft` and `android:paddingStart`.

## Scroll view help
Always give id to ScrollView.It gives the Android system a handle for the view so that when the user rotates the device, the system preserves the scroll position.

## String Resource note
* we can use \n to insert line break
* we can use <b>To make a text bold</b>
* we can use <i>to make a text italic</i>
* apostrophe has to be escaped with backslash

## Constraint Layout

* Allows to position and size childs in a flexible way
* Each view needs atleast on horizonatal and one vertical constraints
* Flatter in view hirerchy

### 
 * A group of views that are linked with one another
 * vertically or horizontally
 * packed, spread, weighted

### Baseline Constraints
* Set constraint for text base line
* Helpful when texts are of different sizes

### Data Binding
* to make code shorter, easier to read, easier to maintain
* the android system traverses the view hierarchy once to get each view at app startup not at runtime when user is interacting with the app
* to enable data binding add this into your build.gradle(Module: app) file:

	```gradle
	buildFeatures {
	    dataBinding true

	}
	```
* to work with databinding we need to wrap our xml layout with a `<layout>` tag. and also move the namespace declaration to layout tag
* create a variable name binding 
* relplace set content view with 
* I created a data class and link view to data by using variable tag inside data tag of xml file


## Fragment
* A Fragment has its own lifecycle and receives its own input events.
* You can add or remove a Fragment while the activity is running.
* A Fragment is defined in a Kotlin class.
* A Fragment's UI is defined in an XML layout file.

## Sensor Manager getting
Getting Sensor Manager
```kotlin
getSystemService(Context.SENSOR_SERVICE) as SensorManager
```
Getting All Type of Sensor List
```kotlin
val sensorList = mSensorManager.getSensorList(Sensor.TYPE_ALL)
```
To get a sensor name we can access getName() method or name property






