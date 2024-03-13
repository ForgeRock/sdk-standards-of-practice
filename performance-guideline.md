# Performance guideline

General performance guidelines for SDK & App Development

## Background Process
* Avoiding running the following operation in the Main Thread:
  * Network Operations
  * File IO
  * CPU intensive operation or Long running operation
  * Database operations
* For Kotlin, use suspend functions instead of thread.
* For iOS Utilize asynchronous APIs provided by iOS frameworks like Grand Central Dispatch (GCD), Operation Queues, Async/Await and Combine framework for reactive programming.
Asynchronous APIs allow tasks to be executed in the background, preventing the main thread from being blocked and ensuring a responsive user interface.

## Battery Consumption
* For Android
  * [Battery consumption for billions ](https://developer.android.com/docs/quality-guidelines/build-for-billions/battery-consumption)
  * [Optimize location for battery](https://developer.android.com/develop/sensors-and-location/location/battery)
* For iOS
  * [Analyze battery use](https://developer.apple.com/documentation/xcode/analyzing-your-app-s-battery-use)

## Memory Usage
* Avoid creating unnecessary objects, use object pool or cache for frequently use object.
* Avoid memory leak, for example:
  * Static or Singleton reference of Activity
  * Without unregistering listeners or receivers
* For Android
  * [Inspect your app's memory usage with Memory Profiler](https://developer.android.com/studio/profile/memory-profiler)
* For iOS
  * To inspect your app's memory usage in iOS Xcode, you can use several tools provided by Xcode like Debug Navigator, Instruments, Memory Graph Debugger
  * [Inspect your iOS app's memory usage](https://developer.apple.com/documentation/xcode/gathering-information-about-memory-use) 

## Caching
* Avoid creating unnecessary objects, use object pool or cache for frequently use object.
* Cache data that is expensive to compute and doesn't change frequently.
* Dispose un-use or expired cached data.
* Avoid caching sensitive data

## App Shrinking
* Reduce the size of the App by enabling shrinking in your release build.
* Obfuscation can help shortens names of app's classes and members.
* Enable Code and Resource shrinking to remove unused resources.

## Build performance
* For Android
  * [https://developer.android.com/build/optimize-your-build](https://developer.android.com/build/optimize-your-build)
* For iOS
  * Incremental Builds: Leverage Xcode incremental build feature, which rebuilds only the components that have changed since the last build. This can significantly reduce build times, especially for large projects.
  * Parallelize Builds: Enable parallel builds in Xcode to distribute compilation tasks across multiple CPU cores, speeding up the build process. Parallelize Builds

## Third party library
* Check the popularity of the library. A popular and well known library is more likely to be well design for mobile application.
* Evaluate library's dependencies. Library with a lot of dependencies may impact the Application's size.
* Evaluate Library's size, performance, memory, and battery usage.

## Modularize
* Design your SDK with modular architecture, allow Application only includes necessary module to minimize its size.


## Profiling and tracing
* Use tools to identify performance bottleneck and optimize the SDK. 
* [Profile tools Android](https://developer.android.com/studio/profile): CPU Profiler, Memory Profiler, Energy Profiler
* [Profile tools iOS]Use Xcode Instruments tool to profile iOS applications and identify performance bottlenecks.

## Testing
* Test with low-end device

### Reading list
- [Android App Performance Guide](https://developer.android.com/topic/performance/overview)
- [iOS App Performance Guide](https://developer.apple.com/documentation/xcode/improving-your-app-s-performance/)

