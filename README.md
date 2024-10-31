# Dependency List

Repository ini berfungsi sebagai daftar referensi link untuk menambahkan dependencies dalam proyek, terutama untuk Hilt, Compose, dan Material 3. Berikut adalah beberapa referensi dan konfigurasi terkait.
Repository update sampai 31 Oktober 2024.

## 1. Hilt
- **Documentation**: [Dagger Hilt Documentation](https://dagger.dev/hilt/gradle-setup)
- **Dependency Link**: Tambahkan berikut ini ke dalam `libs.version.toml` dan `build.gradle.kts` di proyekmu.

### `libs.version.toml` 
```toml
[versions]
hilt = "2.44"
hiltNavigationCompose = "1.2.0"

[libraries]
hilt-android = { module = "com.google.dagger:hilt-android", version.ref = "hilt" }
hilt-compiler = { module = "com.google.dagger:hilt-android-compiler", version.ref = "hilt" }
hilt-navigation-compose = { module = "androidx.hilt:hilt-navigation-compose", version.ref = "hiltNavigationCompose" }

[plugins]
dagger-hilt = { id = "com.google.dagger.hilt.android", version.ref = "hilt" }
```

### `build.gradle.kts project: root`
```kotlin
plugins {
  alias(libs.plugins.dagger.hilt) apply false
}
```

### `build.gradle.kts module: app`
```kotlin
plugins {
  id("kotlin-kapt")
  id("com.google.dagger.hilt.android")
}

dependencies {
  implementation(libs.hilt.android)
  kapt(libs.hilt.compiler)
  implementation(libs.hilt.navigation.compose)
}

kapt {
  correctErrorTypes true
}
```
