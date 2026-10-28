# W/H Inspection

Aplikacja Android opakowująca formularz inspekcji magazynowej i załadunkowej w lokalnym WebView. Działa offline, korzysta z aparatu/galerii i zapisuje raporty HTML oraz PPTX do folderu **Pobrane**.

## Co robi aplikacja

- rejestruje uszkodzenia opakowań na magazynie (lokalizacja, typ, uwagi, zdjęcie),
- zbiera 9 wymaganych zdjęć inspekcji załadunku,
- pozwala dodawać opcjonalne uszkodzenia przy załadunku,
- pokazuje postęp kompletowania zdjęć,
- generuje raport HTML i 3-slajdowy raport PPTX,
- udostępnia raport PPTX przez systemowe menu Androida (np. Outlook, Teams, Dysk),
- uwzględnia paski systemowe i obszary gestów na telefonach Samsung,
- kompresuje zdjęcia lokalnie; nie wysyła danych na serwer.

Wpisy i zdjęcia są przechowywane tylko w pamięci bieżącej sesji. Zamknięcie aplikacji lub jej ubijanie przez system usuwa niezapisane dane, dlatego raport należy wygenerować przed zakończeniem pracy.

## Budowanie APK w GitHub

1. Utwórz puste repozytorium w GitHub.
2. Wgraj do niego **zawartość tego katalogu** (pliki `settings.gradle`, `build.gradle`, katalog `app`, `.github` itd.).
3. Otwórz zakładkę **Actions** i workflow **Build Android APK**.
4. Kliknij **Run workflow**. Workflow uruchomi się też automatycznie po `push` do `main` lub `master`.
5. Po zakończeniu pobierz artefakt **W-H-Inspection-APK**. W środku znajduje się `W-H-Inspection.apk`.

APK debug można instalować ręcznie po zezwoleniu Androidowi na instalowanie aplikacji z danego źródła. Do publicznej dystrybucji należy skonfigurować własny klucz podpisu i wariant release.

## Budowanie lokalne

Wymagane: JDK 17, Android SDK 35 i Gradle 8.9.

```bash
gradle assembleDebug
```

Gotowy plik: `app/build/outputs/apk/debug/app-debug.apk`.

## Najważniejsze pliki

- `app/src/main/assets/index.html` – interfejs i logika formularza,
- `app/src/main/assets/pptxgen.bundle.js` – lokalny generator PPTX,
- `app/src/main/java/pl/ibi/whinspection/MainActivity.java` – WebView, aparat/galeria i zapis raportów,
- `.github/workflows/build-apk.yml` – automatyczne budowanie APK.
