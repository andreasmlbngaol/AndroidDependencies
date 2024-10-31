# Dependency List

Repository ini berfungsi sebagai daftar referensi link untuk menambahkan dependencies dalam proyek, terutama untuk Hilt, Compose, dan Material 3. Berikut adalah beberapa referensi dan konfigurasi terkait.

**Repository update sampai 31 Oktober 2024.**

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

## 2. Type Safe Navigation
- **Documentation**: [Type Safety Navigation in Jetpack Compose](https://developer.android.com/guide/navigation/design/type-safety)
- **Dependency Link**: Tambahkan berikut ini ke dalam `libs.version.toml` dan `build.gradle.kts` tingkat module dan project di proyekmu.

### `libs.version.toml` 
```toml
[versions]
navigationCompose = "2.8.3"
kotlinxSerializationCore = "1.7.3"

[libraries]
androidx-navigation-compose = { group = "androidx.navigation", name = "navigation-compose", version.ref = "navigationCompose" }
kotlinx-serialization-json = { module = "org.jetbrains.kotlinx:kotlinx-serialization-json", version.ref = "kotlinxSerializationCore" }

[plugins]
compose-compiler = { id = "org.jetbrains.kotlin.plugin.compose", version.ref = "kotlin" }
kotlin-plugin-serialization = { id = "org.jetbrains.kotlin.plugin.serialization", version.ref = "kotlin" }
```

### `build.gradle.kts project: root`
```kotlin
plugins {
    alias(libs.plugins.compose.compiler) apply false
}
```

### `build.gradle.kts module: app`
```kotlin
plugins {
    alias(libs.plugins.kotlin.plugin.serialization)
    alias(libs.plugins.compose.compiler)
}

dependencies {
    implementation(libs.kotlinx.serialization.json)
}
```

## 3. Extended Material3 Icon
- **Documentation**: [Material3 Icon](https://m3.material.io/)
- **Dependency Link**: Tambahkan berikut ini ke dalam `libs.version.toml` dan `build.gradle.kts` tingkat module di proyekmu.

### `libs.version.toml` 
```toml
[versions]
material3 = "1.3.0"
materialIconsCore = "1.7.4"

[libraries]
material3 = { module = "androidx.compose.material3:material3", version.ref = "material3" }
androidx-material-icons-core = { module = "androidx.compose.material:material-icons-core", version.ref = "materialIconsCore" }
androidx-material-icons-extended = { module = "androidx.compose.material:material-icons-extended", version.ref = "materialIconsCore" }
```

### `build.gradle.kts module: app`
```kotlin
dependencies {
    implementation(libs.material3)
    implementation(libs.androidx.material.icons.core)
    implementation(libs.androidx.material.icons.extended)
}
```
