# Performance guideline

General performance guidelines for SDK & App Development

## Background Process
* Avoiding running the following operations in the Main Thread:
  * Network Operations
  * File IO
  * CPU intensive operation or Long running operations
  * Database operations
* For Kotlin, use suspend functions instead of threads.

## Battery Consumption
* For Android
  * [Battery consumption for billions ](https://developer.android.com/docs/quality-guidelines/build-for-billions/battery-consumption)
  * [Optimize location for battery](https://developer.android.com/develop/sensors-and-location/location/battery)

## Memory Usage
* Avoid creating unnecessary objects, use object pool or cache for frequently use object.
* Avoid memory leaks, for example:
  * Static or Singleton reference to Activity
  * Without unregistering listeners or receivers
* [Inspect your app's memory usage with Memory Profiler](https://developer.android.com/studio/profile/memory-profiler)

## Caching
* Avoid creating unnecessary objects, use object pool or cache for frequently used objects.
* Cache data that is expensive to compute and doesn't change frequently.
* Dispose unused or expired cached data.
* Avoid caching sensitive data

## App Shrinking
* Reduce the size of the App by enabling shrinking in your release build.
* Obfuscation can help shorten names of app's classes and members.
* Enable Code and Resource shrinking to remove unused resources.

## Build performance
* For Android
  * [https://developer.android.com/build/optimize-your-build](https://developer.android.com/build/optimize-your-build)


## Third party library
* Check the popularity of the library. A popular and well known library is more likely to be well designed for mobile application.
* Evaluate library's dependencies. Library with a lot of dependencies may impact the Application's size.
* Evaluate Library's size, performance, memory, and battery usage.

## Modularize
* Design your SDK with modular architecture, allow applications to only includes necessary modules to minimize their size.


## Profiling and tracing
* Use tools to identify performance bottlenecks and optimize the SDK. 
* [Profile tools](https://developer.android.com/studio/profile): CPU Profiler, Memory Profiler, Energy Profiler

## Testing
* Test with low-end device

### Reading list

- [App Performance Guide](https://developer.android.com/topic/performance/overview)

