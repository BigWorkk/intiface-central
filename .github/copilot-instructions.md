# Intiface Central AI Coding Guidelines

## Architecture Overview
Intiface Central is a Flutter app with Rust backend for sex toy control using Buttplug. Uses flutter_rust_bridge (v2.11.1) for Dart-Rust FFI.

- **Frontend**: Dart/Flutter with Bloc pattern. UI in `lib/page/`, widgets in `lib/widget/`, state in `lib/bloc/`.
- **Backend**: Rust engine in `rust/`, core logic via intiface-engine.
- **Data Flow**: UI → Bloc → Rust bridge → Device control.

Key blocs: DeviceManagerBloc (`lib/bloc/device/`), EngineControlBloc (`lib/bloc/engine/`).

## Build and Run
Requires Flutter ≥3.27.1, Rust stable. Check out buttplug/buttplug_dart as sibling repos.

- **Dev**: `flutter run`
- **Release**: `flutter build [platform] --release --dart-define="SENTRY_DSN=..." --dart-define="DISCORD_CLIENT_ID=..."`
- **CI**: Builds Windows/Linux, uses Inno Setup for installer.

## Key Patterns
- **Bloc State**: Use cubits/blocs for state. Example: `IntifaceConfigurationCubit` for settings.
- **Bridge APIs**: Define in Rust, generate FFI. Match versions exactly (e.g., btleplug 0.11.8).
- **Logging**: loggy + Sentry. Errors via ErrorNotifierCubit.
- **Config**: shared_preferences via cubits.
- **Freezed Models**: For immutable data, e.g., in `lib/src/rust/mobile_init/error.dart`.

## Conventions
- Paths initialized in `IntifaceCentralApp.buildApp()`.
- Permissions: permission_handler for Bluetooth/etc.
- Foreground: flutter_foreground_task on Android.

Reference: `pubspec.yaml` for deps, `README.md` for setup.</content>
<parameter name="filePath">vscode-vfs://github/BigWorkk/intiface-central/.github/copilot-instructions.md