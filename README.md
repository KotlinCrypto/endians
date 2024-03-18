# endians
[![badge-license]][url-license]
[![badge-latest-release]][url-latest-release]

[![badge-kotlin]][url-kotlin]

![badge-platform-android]
![badge-platform-jvm]
![badge-platform-js]
![badge-platform-js-node]
![badge-platform-wasm]
![badge-platform-linux]
![badge-platform-macos]
![badge-platform-ios]
![badge-platform-tvos]
![badge-platform-watchos]
![badge-platform-windows]
![badge-support-android-native]
![badge-support-apple-silicon]
![badge-support-js-ir]
![badge-support-linux-arm]

Big & Little Endian utils for Kotlin Multiplatform

Small library which adds 2 kotlin `value class`es, `BigEndian` and `LittleEndian`

### Usage

```kotlin
fun main() {
    // Extension functions for converting Short, Int, or
    // Long to LittleEndian or BigEndian
    // e.g. Long.toLittleEndian()
    val le = 5L.toLittleEndian()
    val be = 5L.toBigEndian()
    
    println(le)
    // LE[5,0,0,0,0,0,0,0]
    println(be)
    // BE[0,0,0,0,0,0,0,5]

    println(le[0])
    // 5
    println(be[7])
    // 5
    
    // Helper functions to convert bytes to Short, Int, or Long
    val leLong = LittleEndian.bytesToLong(0, 0, 0, 5, 0, 0, 0, 10)
    println(leLong)
    // 720575940463165440
    val beLong = BigEndian.bytesToLong(0, 0, 0, 5, 0, 0, 0, 10)
    println(beLong)
    // 21474836490

    val bytes = ByteArray(le.size + be.size)
    le.copyInto(bytes)
    be.copyInto(bytes, le.size)
    
    // Safely convert BigEndian or LittleEndian to the desired
    // primitives w/o worrying about the size of the underlying
    // ByteArray
    be.toByte()
    be.toShort()
    be.toInt()
    be.toLong()
    
    // APIs for both classes are the same, with only 1 difference
    be.toLittleEndian() // Convert a BigEndian to a LittleEndian
    le.toBigEndian()    // Convert a LittleEndian to a BigEndian
}
```

### Get Started

The best way to keep `KotlinCrypto` dependencies up to date is by using the 
[version-catalog][url-version-catalog]. Alternatively, see below.

<!-- TAG_VERSION -->

```kotlin
// build.gradle.kts
dependencies {
    implementation("org.kotlincrypto.endians:endians:0.2.0")
}
```

<!-- TAG_VERSION -->
[badge-latest-release]: https://img.shields.io/badge/latest--release-0.2.0-blue.svg?style=flat
[badge-license]: https://img.shields.io/badge/license-Apache%20License%202.0-blue.svg?style=flat

<!-- TAG_DEPENDENCIES -->
[badge-kotlin]: https://img.shields.io/badge/kotlin-1.9.23-blue.svg?logo=kotlin

<!-- TAG_PLATFORMS -->
[badge-platform-android]: http://img.shields.io/badge/-android-6EDB8D.svg?style=flat
[badge-platform-jvm]: http://img.shields.io/badge/-jvm-DB413D.svg?style=flat
[badge-platform-js]: http://img.shields.io/badge/-js-F8DB5D.svg?style=flat
[badge-platform-js-node]: https://img.shields.io/badge/-nodejs-68a063.svg?style=flat
[badge-platform-linux]: http://img.shields.io/badge/-linux-2D3F6C.svg?style=flat
[badge-platform-macos]: http://img.shields.io/badge/-macos-111111.svg?style=flat
[badge-platform-ios]: http://img.shields.io/badge/-ios-CDCDCD.svg?style=flat
[badge-platform-tvos]: http://img.shields.io/badge/-tvos-808080.svg?style=flat
[badge-platform-watchos]: http://img.shields.io/badge/-watchos-C0C0C0.svg?style=flat
[badge-platform-wasm]: https://img.shields.io/badge/-wasm-624FE8.svg?style=flat
[badge-platform-windows]: http://img.shields.io/badge/-windows-4D76CD.svg?style=flat
[badge-support-android-native]: http://img.shields.io/badge/support-[AndroidNative]-6EDB8D.svg?style=flat
[badge-support-apple-silicon]: http://img.shields.io/badge/support-[AppleSilicon]-43BBFF.svg?style=flat
[badge-support-js-ir]: https://img.shields.io/badge/support-[js--IR]-AAC4E0.svg?style=flat
[badge-support-linux-arm]: http://img.shields.io/badge/support-[LinuxArm]-2D3F6C.svg?style=flat

[url-latest-release]: https://github.com/KotlinCrypto/endians/releases/latest
[url-license]: https://www.apache.org/licenses/LICENSE-2.0.txt
[url-kotlin]: https://kotlinlang.org
[url-version-catalog]: https://github.com/KotlinCrypto/version-catalog
