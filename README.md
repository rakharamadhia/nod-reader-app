# Nod

Ebooks and comics on one shelf.

## What is Nod

On my iPad I read books in Yomu and comics in Tachimanga. I wanted the same on my phone (Samsung Galaxy S23), in one app: a calm ebook reader with highlights and notes, a comic reader that works with Tachiyomi-style extensions, and some light gamification to keep a daily reading habit.

Nod is a personal project. It is sideloaded as a debug APK. There is no Play Store listing and there are no official releases.

## Features

### Done

Nothing Nod-specific yet. What works today is what upstream Mihon already provides:

- Comic library with categories, scheduled update checks and downloads
- Tachiyomi-compatible extensions (you add extension repositories yourself)
- Comic reader with paged and webtoon modes
- Tracking (AniList, MyAnimeList and others)
- Local backups and restore

### Planned

| # | Milestone | Status |
|---|---|---|
| M0 | Rename to Nod (`app.nod.reader`), own icon, installs next to Mihon | In progress |
| M1 | App shell: floating 4-tab bar (Home, Books, Comics, Reading), design tokens, Inter + Literata fonts, dark mode default | Planned |
| M2 | Books library: EPUB import, real or generated covers, collections, Continue Reading | Planned |
| M3 | Book reader: Paper / Sepia / Night themes, font size, page or scroll layout, saved progress | Planned |
| M4 | Highlights (4 colors) and notes, Markdown export | Planned |
| M5 | Reading time tracking, daily rings, weekly chart, streaks with one freeze per week | Planned |
| M6 | Home dashboard with live data and daily highlight resurfacing | Planned |
| M7 | Onboarding with daily goal picker, awards | Planned |
| M8 | Comics tab, comic detail and comic reader restyled | Planned |
| M9 | OPDS catalogs, Tachimanga backup restore (if feasible), Year in Reading | Planned |

The full spec is in [NOD_SPEC.md](./NOD_SPEC.md).

## Design

Apple-inspired: large titles, cards, a floating tab bar, and dark mode by default with a light mode option. The interactive prototype is at https://claude.ai/artifact/CnKyPGLcuysfMgJNctEHKR (it may require access).

## Tech

- Fork of [Mihon](https://github.com/mihonapp/mihon): Kotlin, Jetpack Compose, SQLDelight
- [Readium Kotlin Toolkit](https://github.com/readium/kotlin-toolkit) planned for EPUB rendering and highlights
- Android 8.0 or higher (minSdk 26)

## Build and install

Requirements:

- JDK 21 to run Gradle (see `.github/.java-version`)
- Android SDK with the platform set as `android-sdk-compile` in `gradle/mihon.versions.toml`
- `adb`, with USB debugging turned on for the phone

Build a debug APK:

```sh
./gradlew assembleDebug
```

APKs are split by ABI and written to `app/build/outputs/apk/debug/`. The Galaxy S23 uses `arm64-v8a`:

```sh
adb install -r app/build/outputs/apk/debug/app-arm64-v8a-debug.apk
```

## Credits and license

Nod is based on [Mihon](https://github.com/mihonapp/mihon), which descends from [Tachiyomi](https://github.com/tachiyomiorg/tachiyomi). Thanks to everyone who has contributed to both projects.

<pre>
Copyright © 2026 Rakha Ramadhia
Copyright © 2015 Javier Tomás
Copyright © 2024 Mihon Open Source Project

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
</pre>

## Disclaimer

Nod is not affiliated with Mihon, Tachiyomi, Yomu or Tachimanga. The app hosts no content. Users are responsible for the sources they add.
