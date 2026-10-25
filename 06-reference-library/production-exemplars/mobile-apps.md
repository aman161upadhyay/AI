# Mobile study catalogue

Study shipped-client constraints and first-party integration examples separately. Approximate stars, licenses, and activity are as of 2026-10-25.

| Repository / stars | License / observed activity | First paths | What to study | Limit |
|---|---|---|---|---|
| [Now in Android](https://github.com/android/nowinandroid), 22.0k | Apache-2.0; 2026-10-20 | `core`, `feature`, `build-logic`, `docs/ArchitectureLearningJourney.md` | Kotlin/Compose modularity, unidirectional flow, repositories, build conventions, screenshot/UI testing | Google reference app, not a complete public production backend; README says backend is not public |
| [Wikipedia iOS](https://github.com/wikimedia/wikipedia-ios), 3.5k | MIT; 2026-10-23; assets need review | `WMFData`, `WMFComponents`, `WikipediaUITests`, `WikipediaUnitTests`, `fastlane` | Offline data, multilingual accessibility, mature test/release boundaries | Branding/content licenses differ from source |
| [Ice Cubes](https://github.com/Dimillian/IceCubesApp), 7.1k | AGPL-3.0; 2026-10-13; link/study | `Packages`, `IceCubesApp`, widget/share extensions | SwiftUI packages, MVVM, Mastodon client boundaries | Do not import copyleft code into a permissive pack |
| [Signal iOS](https://github.com/signalapp/Signal-iOS), 12.3k | AGPL-3.0; 2026-10-21; link/study | `SignalServiceKit`, `SignalUI`, `SignalNSE`, `BUILDING.md` | Lifecycle/security and notification-extension boundaries | Not permission or guidance to invent cryptographic protocols |
| [Kickstarter iOS](https://github.com/kickstarter/ios-oss), 8.7k | Apache-2.0; 2026-10-14; branding review | `Library`, `LibraryTests`, `KsApi`, `GraphAPI`, `KDS` | Testable state transformations, API/design-system separation | Recheck current build dependencies before adapting |
| [Expo examples](https://github.com/expo/examples), 3.8k | MIT; 2026-10-22 | `with-better-auth`, `with-clerk`, `with-app-integrity`, `with-maestro` | One first-party example per integration | Demo auth is not a full authorization design |
| [Immich mobile](https://github.com/immich-app/immich), 117.2k for whole repo | AGPL-3.0; 2026-10-24 | `mobile`, `open-api`, `server`, `e2e` | Flutter client/API/schema/jobs coordination; architecture docs describe Isar/Riverpod | Architecture migration is incomplete per first-party docs; source claims require version check |

All rows have observed recent activity and named first-party or adopted application evidence. No device builds, offline tests, or accessibility audits were executed for this catalogue.

Before adapting a pattern, test offline behavior, secure storage, release signing, permission denial, background interruption, device E2E, and account switching. Keep source reuse rights separate from app content and logos.
