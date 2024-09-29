# Flutter Projects Guide

This README provides information about various Flutter projects and common issues encountered during development.

## Table of Contents
1. [Dice](#dice)
2. [Xylophone](#xylophone)
3. [Quizzler](#quizzler)
4. [Destini](#destini)
5. [BMI Calculator](#bmi-calculator)
6. [Clima Weather](#clima-weather)
7. [Bitcoin Ticker](#bitcoin-ticker)
8. [Todo List](#todo-list)

## Dice

- There are differences in button usage. For documentation, refer to: [Flutter Buttons](https://docs.flutter.dev/release/breaking-changes/buttons)

## Xylophone

- We use the `just_audio` library instead of `audioplayers`.
- Usage is similar to `audio_cache` used in the tutorial, with slight differences.
- For `just_audio` documentation, visit: [just_audio package](https://pub.dev/packages/just_audio)
- `FlatButton` is replaced with `TextButton`. See documentation: [Flutter Buttons](https://docs.flutter.dev/release/breaking-changes/buttons)
- Functions now require the `required` keyword for each parameter.

## Quizzler

- `FlatButton` is replaced with `TextButton`. See documentation: [Flutter Buttons](https://docs.flutter.dev/release/breaking-changes/buttons)
- Changes in `question.dart`:
  - Now using constructor initializer list to initialize properties:

```dart
// Before:
class Question {
  String questionText;
  bool questionAnswer;

  Question(String q, bool a) {
    questionText = q;
    questionAnswer = a;
  }
}

// After:
class Question {
  String questionText;
  bool questionAnswer;

  Question(String q, bool a) 
      : questionText = q,
        questionAnswer = a;
}
```

## Destini

- `FlatButton` is replaced with `TextButton`. See documentation: [Flutter Buttons](https://docs.flutter.dev/release/breaking-changes/buttons)
- `story.dart` requires the `required` keyword for each parameter.

## BMI Calculator

- Parameters require the `required` keyword (without `@` at the beginning).
- In `calculator_brain.dart`, add `late` to `double _bmi` variable:
  ```dart
  late double _bmi;
  ```
- In `input_page.dart`, add `?` to `Gender selectedGender` variable:
  ```dart
  Gender? selectedGender;
  ```
- Fix parameters in `round_icon_button.dart`, `reusable_card.dart`, `icon_content.dart`, and `bottom_button.dart`.
- Add `VoidCallback` to `onPressed` variable in `round_icon_button.dart`, `reusable_card.dart`, and `bottom_button.dart`:
  ```dart
  final VoidCallback onPressed;
  ```

## Clima Weather

- In `networking.dart`, change URL usage:
  ```dart
  http.Response response = await http.get(Uri.parse(url));
  ```
- In `location.dart`, add `?` to `latitude` and `longitude` variables:
  ```dart
  double? latitude;
  double? longitude;
  ```
- Update `getCurrentLocation()` function:
  ```dart
  Position position = await Geolocator.getCurrentPosition(desiredAccuracy: LocationAccuracy.low);
  ```
- In `location_screen.dart`:
  - Add `?` to all variables.
  - Add `!` to ensure non-null values where necessary.
  - Fix button writing errors.
- If location access errors occur:
  - Change API in `services/weather.dart`. Generate new API keys at [OpenWeatherMap](https://home.openweathermap.org/api_keys)
  - Check location permissions in `android/app/main/AndroidManifest.xml`:
    ```xml
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
    <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
    ```
  - If missing, add these lines, then run `flutter clean` and `flutter build apk`.

## Bitcoin Ticker

- Use `Uri.parse()` to create Uri object from `requestURL`:
  ```dart
  http.Response response = await http.get(Uri.parse(requestURL));
  ```
- In `price_screen.dart`:
  - Update `DropdownButton` `onChanged`:
    ```dart
    onChanged: (value) {
      setState(() {
        selectedCurrency = value!;
        getData();
      });
    },
    ```
  - Update `CryptoCard` value:
    ```dart
    value: isWaiting ? '?' : (coinValues[crypto] ?? 'N/A')
    ```
  - Add `required` to `CryptoCard` parameters.

## Todo List

- Add `required` to `TaskTile` function in `task_tile.dart`.
- Update callback variables in `task_tile.dart`:
  ```dart
  final VoidCallback? longPressCallback;
  final ValueChanged<bool?> checkboxCallback;
  ```
- Use `TextButton` in `add_task_screen.dart`.
- Initialize `newTaskTitle` with an empty string:
  ```dart
  String newTaskTitle = '';
  ```
