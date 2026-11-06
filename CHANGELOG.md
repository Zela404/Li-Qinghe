# Changelog

All notable changes to **Li Qinghe** are listed here, newest first.

## [1.5.10-stable] - 2026-11-06

The biggest update since 1.4.6. The module has been rebuilt from a single
dashboard with an auto game profile into a full tuning suite: a new WebUI with
five pages, per-game controls, system and display tuning, a native watcher, and
a complete theming system.

### Highlights

- **All-new WebUI**: Home, Apps, Tweaks, Settings, plus System Monitor, UI
  Settings and Angle Texture pages.
- **Apps page** with User, Game, Preload and Whitelist tabs, and a game scan
  that finds installed games for you.
- **Angle Texture**: per-game texture style (Smooth, Retro, 8-bit, Custom) with
  a Before/After preview.
- **Tweaks page** with Recommended Profile (one-click), Idle Profile, system
  tuning groups, display tuning and logging controls.
- **Liziya**, a native watcher that protects the module and puts it to sleep
  when something else overrides the properties it controls.
- **Theming**: color palettes, corner radius, text and icon size, custom font,
  custom banner, four bottom-nav styles and Frosted / Liquid glass.
- **Backup and restore** for all UI settings.

### Added

#### Home and monitoring
- Home now shows the Idle Profile, Environment and a full Device Info card:
  Li Qinghe version, device name, Android, kernel, security patch, chipset,
  manufacturer, architecture, display, SELinux, build and fingerprint.
- New **System Monitor** page: CPU (usage and cores), RAM, swap, storage,
  battery and temperature.

#### Apps
- **User** tab to browse installed apps, **Game** tab for your game list,
  **Preload** tab for apps to warm up, and **Whitelist** tab for apps that
  must never be compacted, stopped or lowered.
- Game scan that detects installed games and keeps its own detected list.
- Per-game **GL Driver** choice.
- Native `ywhy` helper for app preloading.

#### Angle Texture
- Per-game ANGLE texture overrides, available when the game's GL Driver is
  ANGLE.
- Presets: **Smooth**, **Retro**, **8-bit** and **Custom**, built from
  *Texture detail* (Default, Light, Medium, Heavy, Extreme), *Pixelated* and
  *Distance blur*.
- **Auto** mode (the module switches the game's setting by itself) or
  **Manual** (the module never touches it).
- Before/After preview with a draggable split.
- Applies when the game comes to the front, so the setting is ready before the
  game's GL starts.

#### Tweaks
- **Recommended Profile**: detects the best tuning for your device, then lets
  you apply it with one tap.
- **Idle Profile**: *Normal* or *Battery Saver*. Battery Saver turns on system
  Battery Saver, app-standby and job-scheduler tuning, and applies your
  whitelist to DeviceIdle.
- **Apps & Memory** groups: Job Scheduler, Multitasking, App Standby Tuning,
  Doze (shorter idle timers, with the device's own telephony and messaging
  packages exempted), Low Swap Threshold and SQLite Tuning.
- **Display & Input**:
  - Refresh rate lock with support for AOSP, Transsion, Xiaomi and Samsung
    settings. Originals are saved first, and Default puts them back.
  - Renderer tile (Skia GL / Vulkan, threaded or not). The choice is restored
    early in boot, before SurfaceFlinger starts.
  - SurfaceFlinger frame timing slider (safe range 50 to 100%), with Apply and
    Reset Safe.
  - Long-Press Latency, Keyboard ART Speed and OEM Tuning for
    Xiaomi / Redmi / POCO and Samsung.
- **Logging & Trace**: Silent Persist Log Tags, Logging / Binder Diagnostics,
  Selected Diagnostics, Debug Property Cleanup and **Trace Guard** with 99
  individual system trace, logging and reporting options.
- **Helpers** (off by default):
  - **Fily** compacts memory and, under critical pressure, force-stops idle
    background apps. It never touches the foreground app or your whitelist.
  - **Tctl** reports a cooler value on a detected vendor thermal-throttle
    property to delay throttling, without disabling overheat protection.

#### Liziya (anti-tamper and conflict watcher)
- New native watcher that checks the module is the official build (module ID
  and author) and watches the properties the module sets.
- When another module or app changes them, the module goes to **Sleep** instead
  of fighting it, and Apps and Tweaks are locked until it is recovered.
- **Recovery** button in the WebUI to wake it up, plus a Check status dialog
  that explains what is going on.

#### Appearance and UI Settings
- **Colors**: Material 3 Mono palette or a Custom Color built from three tonal
  roles, with hex and RGB input.
- **Shape**: adjustable corner radius.
- **Size and font**: text size and icon size scaling, and your own font file
  (TTF, OTF, WOFF, WOFF2).
- **Home banner**: use your own photo with horizontal, vertical, zoom and
  rotate framing.
- **Bottom navigation**: four styles (Pill, Capsule, Indicator bar, Material
  bar), with alignment, distance from bottom and side, height, width, show
  names, shrink on scroll and gradient options.
- **Glassmorphism**: Frosted and Liquid glass for toasts and the bottom nav,
  with blur, frost, saturation and refraction controls.
- **Backup and restore**: UI settings are backed up automatically to
  `/sdcard/Download/LiQingheBackupUI`. Restore checks the file and shows what
  is inside before anything changes.

#### Settings
- New **About** card with module name, version, developer, build date and a
  live mini phone clock.
- **Force stop** to close every running app so changes like a new renderer
  apply to them.
- **Refresh WebUI** to reload the page without losing your settings.

#### Install and uninstall
- New `post-fs-data.sh` to restore the chosen renderer before SurfaceFlinger
  starts.
- Uninstall now restores SurfaceFlinger, display, Trace Guard and system
  settings to their original values.

### Changed

- Module ID is now `LQlzy` (was `QH46`). See the upgrade notes below.
- Version is now `1.5.10-stable` (versionCode `31`).
- Game and idle switching moved into a separate runtime (`zi.sh`) that reads the
  foreground app through the native `ven` helper, instead of polling inside
  `service.sh`.
- Game and idle behavior is now driven by the Recommended Profile and the
  individual Tweaks toggles, replacing the fixed LOW / MID / HIGH device tier
  scoring from 1.4.x.
- Code split from one large `service.sh` into `common.sh` and the `modules/`
  and `other/` folders, which makes the module easier to maintain.
- Module description now includes your device name, for example
  `Make your POCO F5 feel better`. It is written at boot, and only the
  description line of `module.prop` is touched.
- Refreshed module banner.

### Upgrade notes

- **The module ID changed from `QH46` to `LQlzy`**, so your manager will treat
  this as a new module and not as an in-place update. Remove 1.4.6 first, then
  flash 1.5.10, and reboot. Running both together would make them fight over
  the same properties.
- Start fresh on 1.5.10: tap *Detect profile* on Recommended Profile in the
  Tweaks page to begin from the best values for your device, then adjust
  anything you like.
- After flashing, reboot once so the renderer, display and tuning groups are
  applied from boot.
