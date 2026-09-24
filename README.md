<p align="center">
  <a href="https://github.com/yashajagiya/NewPipe">
    <img src="assets/new_pipe_icon_5.png" width="150" alt="NewPipe Kotlin Alpha">
  </a>
</p>

<h1 align="center">NewPipe Kotlin Alpha</h1>

<p align="center">
  A Kotlin and Jetpack Compose migration of the NewPipe Android application, focused on modern Android architecture, declarative UI, and a maintainable Kotlin-based codebase.
</p>

<p align="center">
  <a href="https://github.com/yashajagiya/NewPipe">
    <img src="https://img.shields.io/github/license/yashajagiya/NewPipe" alt="License">
  </a>
  <img src="https://img.shields.io/badge/Kotlin-100%25-purple" alt="Kotlin">
  <img src="https://img.shields.io/badge/Jetpack%20Compose-UI-blue" alt="Jetpack Compose">
  <img src="https://img.shields.io/badge/Status-Alpha-orange" alt="Alpha">
</p>

---

## Overview

**NewPipe Kotlin Alpha** is a personal Android development project focused on migrating and modernizing the NewPipe application from its original Java-based implementation toward a Kotlin-first architecture with Jetpack Compose.

The project combines modern Android development practices with the existing NewPipe application ecosystem. The migration focuses on replacing legacy UI patterns with declarative Compose UI, introducing Kotlin-based application logic, and restructuring components around modern Android architecture and reactive state management.

The project is currently in **alpha development**. Some areas remain under active migration and may contain incomplete functionality, implementation differences, or instability.

The primary goals of the project are:

* Explore large-scale Java-to-Kotlin migration in an Android application.
* Replace legacy Android UI implementations with Jetpack Compose.
* Apply modern Material 3 design principles.
* Integrate Media3 for playback functionality.
* Use reactive application state with Kotlin Flow and StateFlow.
* Maintain local application data using Room.
* Improve separation between UI, application logic, playback, networking, and persistence layers.
* Establish a foundation that can be extended toward larger-screen and Android TV-oriented experiences.

## Project Status

**Current status: Alpha**

This repository is an experimental and actively developed migration project rather than a production release.

The migration process involves working across multiple parts of the application, including UI, playback, local data, streams, networking, settings, downloads, and supporting infrastructure.

Because the project is under active development:

* Some functionality may still be incomplete.
* APIs and internal architecture may change.
* UI and navigation behavior may differ from the original application.
* Performance and stability are still being evaluated.
* Documentation and code organization will continue to evolve.

The project also uses AI-assisted development tools as part of the migration and refactoring workflow. AI assistance is treated as a development aid; implementation decisions, integration, debugging, and validation remain part of the development process.

---

## Key Capabilities

### Modern Android UI

The application uses **Jetpack Compose** as the primary UI framework.

The Compose-based UI provides a declarative approach to building application screens and reusable components while reducing dependency on traditional XML-based view hierarchies.

The UI layer includes:

* Jetpack Compose
* Material 3 components
* Material You theming
* Dynamic color support
* Reusable Compose components
* Declarative screen rendering
* Compose-based state observation
* Animated UI transitions

The migration provides an opportunity to redesign parts of the application while preserving the underlying functionality and data flow.

### Media Playback

Playback is implemented using **AndroidX Media3 / ExoPlayer**.

The playback layer is responsible for handling audio and video playback and integrating playback state with the rest of the application.

The project includes infrastructure for:

* Audio and video playback
* Background playback
* Playback services
* Queue management
* Playback state management
* Media session integration
* Popup and floating playback experiences
* Integration between player state and application UI

Using Media3 provides a modern Android media stack while allowing playback functionality to remain separated from the Compose UI layer.

### Local Data Management

The project uses **Room** for local persistence.

The database layer contains entities, DAOs, database configuration, and migration-related components used to manage locally stored application data.

This supports functionality such as:

* Local subscriptions
* Local playlists
* Saved content
* Application preferences and state
* Persistent user data

Keeping persistent data locally allows application features to function without requiring a separate account-based backend for local organization.

### Stream and Content Processing

The project retains a dedicated stream-processing layer for handling content and stream information.

The `streams` package separates stream-related processing from UI and application-level components, making it easier to manage parsing, stream information, and playback preparation independently.

Networking and content extraction are integrated through the NewPipe ecosystem and supporting networking components.

### Reactive State Management

Application state is handled using Kotlin's reactive programming APIs, including:

* `StateFlow`
* `SharedFlow`
* Kotlin Coroutines
* Lifecycle-aware state collection

This allows UI components to react to state changes without tightly coupling the UI to the underlying implementation.

A simplified data flow can be represented as:

```text
Data / Network / Player
          │
          ▼
    Application Logic
          │
          ▼
     ViewModel / State
          │
          ▼
       StateFlow
          │
          ▼
   Jetpack Compose UI
```

---

## Architecture

The project follows a modular separation of responsibilities across major application areas.

```text
                    Application
                         │
        ┌────────────────┼────────────────┐
        │                │                │
        ▼                ▼                ▼
       UI             Player          Streams
        │                │                │
        ▼                ▼                ▼
   ViewModels       Media3/Player    Extraction
        │                │                │
        └────────────────┼────────────────┘
                         │
                         ▼
                    Local Data
                         │
                         ▼
                       Room
```

The codebase is organized into dedicated packages for application responsibilities rather than placing functionality inside a single UI layer.

Major areas include:

* `ui/` — Jetpack Compose screens, components, and UI infrastructure.
* `player/` — Media3 playback implementation and playback services.
* `streams/` — Stream and content processing.
* `database/` — Room database entities, DAOs, and persistence infrastructure.
* `local/` — Local application features and locally stored content.
* `download/` — Download-related functionality.
* `settings/` — Application settings and configuration.
* `util/` — Shared utilities and extension functions.
* `views/` — Supporting Android view components retained during the migration.
* `error/` — Error handling and error-related components.
* `ktx/` — Kotlin extension utilities.

This structure reflects the broader scope of the migration beyond simply replacing XML layouts with Compose.

---

## Technology Stack

| Category                | Technology                   |
| ----------------------- | ---------------------------- |
| Language                | Kotlin                       |
| UI Framework            | Jetpack Compose              |
| Design System           | Material 3                   |
| Theming                 | Material You / Dynamic Color |
| Media Playback          | AndroidX Media3 / ExoPlayer  |
| Architecture            | MVVM / Reactive Architecture |
| State Management        | StateFlow / SharedFlow       |
| Dependency Injection    | Koin                         |
| Database                | Room                         |
| Networking              | OkHttp                       |
| Content Extraction      | NewPipeExtractor             |
| Image Loading           | Coil                         |
| Asynchronous Processing | Kotlin Coroutines / Flow     |
| Build System            | Gradle                       |
| Development Environment | Android Studio               |
| Java Runtime            | JDK 21                       |

---

## Migration Approach

The main purpose of the project is not simply to rewrite source files from Java to Kotlin.

The migration also explores how an existing Android application can be progressively adapted to modern Android development practices.

### Java to Kotlin

Application components are being migrated to Kotlin while preserving the behavior and responsibilities of the original implementation where appropriate.

The migration provides practical experience with:

* Kotlin language features
* Null-safety
* Extension functions
* Coroutines
* Flow
* Sealed types
* Data classes
* Kotlin-based dependency management
* Kotlin-specific Android APIs

### XML to Jetpack Compose

Legacy UI implementations are being transitioned toward Jetpack Compose.

Instead of relying primarily on XML layouts and imperative view manipulation, Compose allows the UI to be represented as a function of application state.

This approach simplifies state-driven rendering and provides a foundation for reusable UI components.

### Architecture Modernization

The migration also focuses on improving separation of responsibilities between:

* UI
* ViewModels
* Application state
* Playback
* Networking
* Stream processing
* Local persistence
* Settings
* Downloads

This makes individual components easier to reason about and provides clearer boundaries for future development.

---

## Project Structure

The primary application source is located under:

```text
app/src/main/java/org/schabi/newpipe/
```

The major packages are organized as follows:

```text
org.schabi.newpipe/
│
├── database/
│   ├── Room entities
│   ├── DAOs
│   └── Database configuration
│
├── download/
│   └── Download-related functionality
│
├── error/
│   └── Error handling components
│
├── ktx/
│   └── Kotlin extension utilities
│
├── local/
│   └── Local application features
│
├── player/
│   └── Media3 playback implementation
│
├── settings/
│   └── Application settings
│
├── streams/
│   └── Stream processing and handling
│
├── ui/
│   └── Jetpack Compose UI
│
├── util/
│   └── Shared utilities
│
└── views/
    └── Supporting Android views
```

The project also contains application-level components such as `MainActivity`, routing infrastructure, database initialization, version handling, and other Android application services.

---

## Development Requirements

### Environment

* Android Studio Ladybug (2024.2.1) or newer
* Android SDK 30 or higher
* JDK 21
* Gradle-compatible development environment
* Physical Android device or Android Emulator

A physical device is recommended when testing playback, background services, media sessions, and device-specific Android behavior.

---

## Getting Started

### Clone the Repository

```bash
git clone https://github.com/yashajagiya/NewPipe.git
```

### Open the Project

Open the cloned repository in Android Studio.

### Configure the Development Environment

Ensure the following are available:

* Android SDK 30+
* JDK 21
* Required Android Studio SDK components

### Sync the Project

Allow Android Studio to synchronize the Gradle project and download the required dependencies.

### Build

Build the application from Android Studio or using Gradle:

```bash
./gradlew assembleDebug
```

On Windows:

```powershell
.\gradlew.bat assembleDebug
```

### Run

Connect an Android device or start an emulator and run the application through Android Studio.

---

## Engineering Focus

This project is primarily focused on practical Android engineering rather than creating a simple demonstration application.

The development work involves:

* Large-scale Java-to-Kotlin migration
* XML-to-Compose migration
* Reactive UI state management
* Media playback architecture
* Local database design
* Stream processing
* Coroutine-based asynchronous operations
* Dependency injection
* Application navigation
* Android lifecycle management
* Background services
* Performance and stability considerations
* Codebase organization and maintainability

The project therefore serves as a practical exploration of how an existing Android application can be progressively modernized while maintaining its broader feature architecture.

---

## Current Limitations

Because this is an alpha-stage migration, the project should not be considered a drop-in replacement for the original NewPipe application.

Known limitations may include:

* Incomplete migration of some components
* Temporary compatibility layers
* Inconsistent behavior between migrated and non-migrated components
* UI differences from the original application
* Areas requiring additional testing
* Ongoing architectural refactoring

These limitations are expected to change as the migration progresses.

---

## Development Roadmap

Planned development areas include:

* Continue migrating remaining Android components to Kotlin.
* Expand Jetpack Compose coverage.
* Improve separation between UI and application logic.
* Refine navigation and state management.
* Improve playback integration.
* Continue database and persistence modernization.
* Improve error handling and recovery.
* Refine code organization and documentation.
* Improve testing coverage.
* Investigate larger-screen and Android TV-oriented UI patterns.
* Reduce temporary migration and compatibility code.

---

## Project Scope

NewPipe Kotlin Alpha is primarily a **personal Android engineering and migration project**.

The project is intended to provide practical experience with modern Android development while exploring the challenges involved in modernizing a large existing application.

The project should be considered an independent development effort and not an official NewPipe release.

---

## Contributing

The repository is primarily maintained as a personal development project.

Bug reports, technical feedback, and improvement suggestions are welcome. If you identify an issue or have a proposal, open a GitHub Issue with enough information to reproduce or understand the problem.

For code changes, Pull Requests should include a clear description of:

* The problem being addressed
* The implementation approach
* Any architectural changes
* Testing performed
* Potential limitations or follow-up work

---

## License

This project is licensed under the **GNU General Public License v3.0 (GPLv3)**.

See the [`LICENSE`](LICENSE) file for the complete license text.

This project is an independent development effort and should not be interpreted as an official release of the upstream NewPipe project.

---

## Author

**Yash Ajagiya**

Android Developer focused on Kotlin, Jetpack Compose, modern Android architecture, and on-device technologies.

GitHub:
https://github.com/yashajagiya

Repository:
https://github.com/yashajagiya/NewPipe
