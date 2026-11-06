<div align="center">

# Li Qinghe

**Make your device feel better.**

An adaptive display & system tuner for Android, with a full WebUI.

![Version](https://img.shields.io/badge/version-1.5.10--stable-8a8a8a?style=flat-square)
![Platform](https://img.shields.io/badge/platform-Android-8a8a8a?style=flat-square)
![Manager](https://img.shields.io/badge/manager-AxManager-8a8a8a?style=flat-square)

<img src="assets/overview.jpg" alt="Li Qinghe WebUI overview" width="100%">

</div>

---

## What is Li Qinghe?

Li Qinghe is a tuning module for Android. It looks at what your phone is doing
and adjusts the system to match: when you open a game it switches to a gaming
setup, and when you go back to everyday use it goes back to a calm, battery
friendly one.

You control everything from a clean WebUI inside your module manager. There is
no command line and no config files to edit by hand. Pick a profile, flip a
toggle, tweak a slider, and the module takes care of the rest.

It is made for daily use, so it keeps a backup of the original values it
changes and puts them back when you turn a tweak off or uninstall the module.

## Features

**Games**
- Automatic game detection with a game scan, so you do not have to add games by
  hand.
- Per-game **GL Driver** choice and **Angle Texture** styles (Smooth, Retro,
  8-bit or your own mix) with a Before / After preview.

**Tuning**
- **Recommended Profile**: detects the best settings for your device and applies
  them in one tap, with a Revert button.
- **Idle Profile**: *Normal* or *Battery Saver*.
- App behavior (Job Scheduler, Multitasking, App Standby, Doze), memory and
  SQLite tuning.
- Display: refresh rate lock, renderer choice, SurfaceFlinger timing, plus
  long-press latency, keyboard speed and Xiaomi / Redmi / POCO / Samsung
  specific tuning.
- Logging and trace controls, including **Trace Guard** with 99 options.
- Optional helpers (off by default): **Fily** for memory compaction and
  **Tctl** for thermal behavior.

**Protection**
- **Liziya**, a native watcher that checks the module is the official build and
  notices when another module or app overrides its settings. If that happens,
  the module goes to sleep instead of fighting it, and you can wake it up with
  one tap from the Home page.

**Look and feel**
- Color palettes and your own custom colors, corner radius, text and icon size,
  custom font and custom banner.
- Four bottom navigation styles.
- Frosted and Liquid glass for toasts and the navigation bar.
- Automatic UI backup and restore.

## Screenshots

<table>
  <tr>
    <td align="center" width="33%">
      <img src="assets/screenshots/02-home.jpg" alt="Home" width="240"><br>
      <sub><b>Home</b><br>Status, official-build check, idle profile and device info</sub>
    </td>
    <td align="center" width="33%">
      <img src="assets/screenshots/03-system-monitor.jpg" alt="System Monitor" width="240"><br>
      <sub><b>System Monitor</b><br>CPU, RAM, swap, storage, battery and temperature</sub>
    </td>
    <td align="center" width="33%">
      <img src="assets/screenshots/07-tweaks.jpg" alt="Tweaks" width="240"><br>
      <sub><b>Tweaks</b><br>Recommended Profile, helpers, idle profile and system tuning</sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="33%">
      <img src="assets/screenshots/04-apps-user.jpg" alt="Apps, User tab" width="240"><br>
      <sub><b>Apps · User</b><br>Your installed apps, with Game and Whitelist labels</sub>
    </td>
    <td align="center" width="33%">
      <img src="assets/screenshots/05-apps-game.jpg" alt="Apps, Game tab" width="240"><br>
      <sub><b>Apps · Game</b><br>Your games, each with its own GL driver and graphics options</sub>
    </td>
    <td align="center" width="33%">
      <img src="assets/screenshots/06-angle-texture.jpg" alt="Angle Texture" width="240"><br>
      <sub><b>Angle Texture</b><br>Per-game texture style with a Before / After preview</sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="33%">
      <img src="assets/screenshots/08-settings.jpg" alt="Settings" width="240"><br>
      <sub><b>Settings</b><br>About, UI Settings, Force stop and Refresh WebUI</sub>
    </td>
    <td align="center" width="33%">
      <img src="assets/screenshots/09-ui-settings.jpg" alt="UI Settings" width="240"><br>
      <sub><b>UI Settings</b><br>Colors, shape, size, banner, navigation, backup</sub>
    </td>
    <td align="center" width="33%">
      <img src="assets/screenshots/01-splash.jpg" alt="Splash screen" width="240"><br>
      <sub><b>Splash</b><br>Loads your saved preferences on start</sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="33%">
      <img src="assets/screenshots/10-glass-frosted.jpg" alt="Glassmorphism, Frosted" width="240"><br>
      <sub><b>Glassmorphism · Frosted</b><br>Blur, frost and saturation for toasts and the nav bar</sub>
    </td>
    <td align="center" width="33%">
      <img src="assets/screenshots/11-glass-liquid.jpg" alt="Glassmorphism, Liquid" width="240"><br>
      <sub><b>Glassmorphism · Liquid</b><br>Refraction controls for a liquid glass look</sub>
    </td>
    <td width="33%"></td>
  </tr>
</table>

## Installation

1. Download [Li-Qinghe-v1.5.10-stable.zip](downloads/Li-Qinghe-v1.5.10-stable.zip)
   (open the file page and tap **Download**), or grab it from the
   [Releases](../../releases) page.
2. Open your module manager (**AxManager**) and install the zip.
3. Reboot your device.
4. Open **Li Qinghe** from the manager to launch the WebUI.
5. Go to **Tweaks** and tap **Detect profile** to start from the best values for
   your device.

> **Updating from 1.4.x?** The module ID changed from `QH46` to `LQlzy`, so it
> installs as a separate module. Remove 1.4.x first, then install 1.5.10, and
> reboot.

## Uninstalling

Remove the module from your manager and reboot. Li Qinghe puts SurfaceFlinger,
display, Trace Guard and system settings back to their original values when it
is removed.

## FAQ

**What does "Alive" on the Home page mean?**
Liziya is awake and watching. Nothing else has changed the properties Li Qinghe
controls, so the tweaks work normally.

**The module says "Sleep". What now?**
Another module or app changed a property Li Qinghe controls, so it stopped
instead of fighting over it. Open the status chip on Home, check what changed
and tap **Recovery**. If you have other tuning modules installed, try keeping
only one of them active.

**What is "Official made"?**
A check that the module ID and author match the official build. If they do not,
the anti-tamper protection puts the module to sleep.

**Do I need to add my games manually?**
No. Use the game scan on the **Apps → Game** tab. You can still add or remove
games by hand.

**Is it safe?**
Li Qinghe saves the original value of what it changes and restores it when you
turn the tweak off or remove the module. Even so, tuning always depends on your
device and ROM, so use it at your own risk.

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for everything that changed in each version.

## Credits

Made by **Li Ziya**. Questions, feedback and updates: [t.me/Li_Ziya1](https://t.me/Li_Ziya1)
