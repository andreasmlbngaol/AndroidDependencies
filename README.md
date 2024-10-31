# Dependency List

Repository ini berfungsi sebagai daftar referensi link untuk menambahkan dependencies dalam proyek, terutama untuk Hilt, Compose, dan Material 3. Berikut adalah beberapa referensi dan konfigurasi terkait.

## 1. Hilt
- **Documentation**: [Dagger Hilt Documentation](https://dagger.dev/hilt/)
- **Dependency Link**: Tambahkan berikut ini ke dalam `libs.version.toml` dan `build.gradle.kts` di proyekmu.

### `libs.version.toml`
```toml
[versions]
hilt = "2.44"

[libraries]
hilt-android = { module = "com.google.dagger:hilt-android", version.ref = "hilt" }
hilt-compiler = { module = "com.google.dagger:hilt-compiler", version.ref = "hilt" }
