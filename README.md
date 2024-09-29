# Mobile Development Flutter

## Daftar Isi
1. **Project Link** : [i_am_rich](https://github.com/KKSBY/i_am_rich) 
2. **Project Link** : [Name Card](https://github.com/KKSBY/NameCard)
3. Notes : [Dice](#dice) || **Project Link** : [Dice](https://github.com/KKSBY/Dice)
4. Notes : [Magic8Ball] || **Project Link** : [Magic8Ball](https://github.com/KKSBY/Magic8Ball)
5. Notes : [Xylophone](#xylophone) || **Project Link** : [Xylophone](https://github.com/KKSBY/xylophone)
6. Notes : [Quizzler](#quizzler) ||  **Project Link** : [Quizzler](https://github.com/KKSBY/Quizzler)
7. Notes : [Destini](#destini) ||  **Project Link** : [Destini](https://github.com/KKSBY/destini)
8. Notes : [BMI Calculator](#bmi-calculator) ||  **Project Link** : [BMI Calculator](https://github.com/KKSBY/mbi_Calculator)
9. Notes : [Clima Weather](#clima-weather) ||  **Project Link** : [Clima Weather](https://github.com/KKSBY/ClimaWeather)
10. Notes : [Bitcoin Ticker](#bitcoin-ticker) ||  **Project Link** : [Bitcoin Ticker](https://github.com/KKSBY/Bitcoin_Ticker)
11. **Project Link** : [Flash-Chat](https://github.com/KKSBY/Flash-Chat)
12. Notes : [Todo List](#todo-list) || **Project Link** : [Todo List](https://github.com/KKSBY/ToDoList)

## Dice

- **Link GitHub**: [Proyek Dice](https://github.com/londonappbrewery/dicee-flutter)
- Terdapat perbedaan penggunaan tombol. Untuk dokumentasinya, lihat di: [Tombol Flutter](https://docs.flutter.dev/release/breaking-changes/buttons)

## Xylophone

- **Link GitHub**: [Proyek Xylophone](https://github.com/londonappbrewery/xylophone-flutter)
- Kita menggunakan library `just_audio` bukan `audioplayers`.
- Penggunaannya kurang lebih sama dengan `audio_cache` yang digunakan dalam tutorial, mungkin ada sedikit perbedaan.
- Untuk dokumentasi `just_audio`, lihat di: [Paket just_audio](https://pub.dev/packages/just_audio)
- `FlatButton` digantikan dengan `TextButton`. Lihat dokumentasi: [Tombol Flutter](https://docs.flutter.dev/release/breaking-changes/buttons)
- Fungsi sekarang membutuhkan kata kunci `required` untuk setiap parameter.

## Quizzler

- **Link GitHub**: [Proyek Quizzler](https://github.com/londonappbrewery/quizzler-flutter)
- `FlatButton` digantikan dengan `TextButton`. Lihat dokumentasi: [Tombol Flutter](https://docs.flutter.dev/release/breaking-changes/buttons)
- Perubahan di `question.dart`:
  - Sekarang menggunakan constructor initializer list untuk menginisialisasi properti:

```dart
// Sebelum:
class Question {
  String questionText;
  bool questionAnswer;

  Question(String q, bool a) {
    questionText = q;
    questionAnswer = a;
  }
}

// Sesudah:
class Question {
  String questionText;
  bool questionAnswer;

  Question(String q, bool a) 
      : questionText = q,
        questionAnswer = a;
}
```

## Destini

- **Link GitHub**: [Proyek Destini](https://github.com/londonappbrewery/destini-challenge-starting)
- `FlatButton` digantikan dengan `TextButton`. Lihat dokumentasi: [Tombol Flutter](https://docs.flutter.dev/release/breaking-changes/buttons)
- `story.dart` membutuhkan kata kunci `required` untuk setiap parameter.

## BMI Calculator

- **Link GitHub**: [Proyek Kalkulator BMI](https://github.com/londonappbrewery/bmi-calculator-flutter)
- Parameter membutuhkan kata kunci `required` (tanpa `@` di awal).
- Di `calculator_brain.dart`, tambahkan `late` ke variabel `double _bmi`:
  ```dart
  late double _bmi;
  ```
- Di `input_page.dart`, tambahkan `?` ke variabel `Gender selectedGender`:
  ```dart
  Gender? selectedGender;
  ```
- Perbaiki parameter di `round_icon_button.dart`, `reusable_card.dart`, `icon_content.dart`, dan `bottom_button.dart`.
- Tambahkan `VoidCallback` ke variabel `onPressed` di `round_icon_button.dart`, `reusable_card.dart`, dan `bottom_button.dart`:
  ```dart
  final VoidCallback onPressed;
  ```

## Clima Weather

- **Link GitHub**: [Proyek Clima](https://github.com/londonappbrewery/Clima-Flutter)
- Di `networking.dart`, ubah penggunaan URL:
  ```dart
  http.Response response = await http.get(Uri.parse(url));
  ```
- Di `location.dart`, tambahkan `?` ke variabel `latitude` dan `longitude`:
  ```dart
  double? latitude;
  double? longitude;
  ```
- Perbarui fungsi `getCurrentLocation()`:
  ```dart
  Position position = await Geolocator.getCurrentPosition(desiredAccuracy: LocationAccuracy.low);
  ```
- Di `location_screen.dart`:
  - Tambahkan `?` ke semua variabel.
  - Tambahkan `!` untuk memastikan nilai tidak null jika diperlukan.
  - Perbaiki kesalahan penulisan tombol.
- Jika terjadi kesalahan akses lokasi:
  - Ubah API di `services/weather.dart`. Buat kunci API baru di [OpenWeatherMap](https://home.openweathermap.org/api_keys)
  - Periksa izin lokasi di `android/app/main/AndroidManifest.xml`:
    ```xml
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
    <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
    ```
  - Jika tidak ada, tambahkan baris ini, lalu jalankan `flutter clean` dan `flutter build apk`.

## Bitcoin Ticker

- **Link GitHub**: [Proyek Bitcoin Ticker](https://github.com/londonappbrewery/bitcoin-ticker-flutter)
- Gunakan `Uri.parse()` untuk membuat objek Uri dari `requestURL`:
  ```dart
  http.Response response = await http.get(Uri.parse(requestURL));
  ```
- Di `price_screen.dart`:
  - Perbarui `DropdownButton` `onChanged`:
    ```dart
    onChanged: (value) {
      setState(() {
        selectedCurrency = value!;
        getData();
      });
    },
    ```
  - Perbarui nilai `CryptoCard`:
    ```dart
    value: isWaiting ? '?' : (coinValues[crypto] ?? 'N/A')
    ```
  - Tambahkan `required` ke parameter `CryptoCard`.

## Todo List

- **Link GitHub**: [Proyek Todoey](https://github.com/londonappbrewery/todoey-flutter)
- Tambahkan `required` ke fungsi `TaskTile` di `task_tile.dart`.
- Perbarui variabel callback di `task_tile.dart`:
  ```dart
  final VoidCallback? longPressCallback;
  final ValueChanged<bool?> checkboxCallback;
  ```
- Gunakan `TextButton` di `add_task_screen.dart`.
- Inisialisasi `newTaskTitle` dengan string kosong:
  ```dart
  String newTaskTitle = '';
  ```
