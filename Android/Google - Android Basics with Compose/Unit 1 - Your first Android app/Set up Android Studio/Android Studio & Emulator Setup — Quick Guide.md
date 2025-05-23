> **Purpose** – Give you the fastest path from zero to a working Android dev environment. Skim, follow the OS section you need, and you’re ready to build.
>
> • Full codelab reference: [https://developer.android.com/codelabs/basic-android-kotlin-compose-install-android-studio](https://developer.android.com/codelabs/basic-android-kotlin-compose-install-android-studio)
> • Video walk‑throughs (pick one):
>
> * **Linux** ▶️ [https://www.youtube.com/watch?v=tdkjCZ03Aj4](https://www.youtube.com/watch?v=tdkjCZ03Aj4)
> * **Windows** ▶️ [https://www.youtube.com/watch?v=8gc5z3aKc6k](https://www.youtube.com/watch?v=8gc5z3aKc6k)
> * **macOS** ▶️ [https://www.youtube.com/watch?v=8ILww0tUSxw](https://www.youtube.com/watch?v=8ILww0tUSxw)

---

## 1  Minimum Specs

| Requirement | Recommended                                                               |
| ----------- | ------------------------------------------------------------------------- |
| RAM         | 8 GB (min) • 16 GB (best)                                                 |
| Disk        | 10 GB free for IDE + SDK/AVDs                                             |
| CPU         | Modern x86\_64 with virtualization (Intel VT‑x / AMD‑V, Apple Silicon OK) |
| OS          | Windows 10/11 64‑bit, macOS 11+, Ubuntu 20.04+                            |

> **Tip** – Enable hardware virtualization in BIOS/UEFI **before** installing. Without it, the Emulator crawls.

---

## 2  Download Android Studio

1. Go to [https://developer.android.com/studio](https://developer.android.com/studio).
2. Click **Download Android Studio** (stable channel).
3. Accept license → the installer/tarball (\~1 GB) downloads.

---

## 3  Install & Launch

### Windows

```text
android-studio-*.exe → Next → Choose install path → Android Studio → Finish → Run
```

*Let the Wizard fetch SDK, Platform‑Tools, and a recommended emulator image.*

### macOS (Intel & Apple Silicon)

```text
.dmg → Drag “Android Studio” into /Applications → Open → Allow Gatekeeper
```

*First launch triggers “Setup Wizard”. Keep default components.*

### Linux (Deb/RPM‑based)

```bash
# 1. Extract
tar -xf android-studio-*.tar.gz -C /opt
# 2. Add to PATH (e.g., ~/.bashrc)
export PATH="$PATH:/opt/android-studio/bin"
# 3. Run
studio.sh
```

*On Ubuntu you may also `sudo snap install android-studio --classic`.*

> **USB Debugging on Linux** – Create `/etc/udev/rules.d/51-android.rules` with vendor IDs, then `sudo udevadm control --reload-rules && sudo service udev restart`.

---

## 4  SDK Manager Checklist (first run)

| Component                            | Why                                                        |
| ------------------------------------ | ---------------------------------------------------------- |
| **Android SDK Platform XX**          | Match the API level you’ll target (e.g., 34 / Android 14). |
| **Android SDK Platform‑Tools**       | `adb`, `fastboot`. Always update to latest.                |
| **Android Emulator**                 | Core engine for virtual devices.                           |
| **Intel x86 / ARM 64 System Images** | Needed for each AVD you create.                            |

> **Space‑Saver** – Un‑tick obsolete platforms and system images you won’t test.

---

## 5  Create Your First Emulator (AVD)

1. **Tools ▸ Device Manager ▸ Create Device**
2. Pick a **Phone** (Pixel 5 is a good baseline).
3. Select a system image (e.g., **API 34 x86\_64** or **Google Play ARM64** for M‑series Macs).
4. Finish → Play ▶️ to boot.
5. Verify: home screen appears; `adb devices` lists it as **emulator‑5554**.

> **Performance Tips**
>
> * Use **Cold boot** once; then switch to **Quick‑Boot**.
> * Allocate 4 GB RAM & 2 CPU cores for smooth Compose previews.

---

## 6  Connecting a Physical Device (Optional)

1. Enable **Developer Options** → **USB Debugging** on your Android phone.
2. Plug in via USB. Accept RSA prompt on device.
3. `adb devices` should show your device serial.
4. Click **Select Device** in Android Studio run dropdown.

---

## 7  First Run of a Sample App

```bash
# In Android Studio welcome screen
File ▸ New ▸ New Project ▸ Empty Compose Activity ▸ Finish
```

1. Press **Run ▶️**. Choose your AVD or phone.
2. Wait for Gradle build → “Hello Android” launches.

Congrats ✨ You’re ready to tackle the next Kotlin codelabs!

---

## 8  Troubleshooting Quick‑Ref

| Symptom                         | Fix                                                                           |
| ------------------------------- | ----------------------------------------------------------------------------- |
| *Emulator slow / black screen*  | Check virtualization enabled; switch to **Cold Boot** once; lower resolution. |
| *`adb` not found*               | Add `$HOME/Android/Sdk/platform-tools` to PATH.                               |
| *Device not detected (Windows)* | Install Google USB Driver via SDK Manager, then re‑plug.                      |
| *Studio freezes on first build* | Allocate more RAM to Gradle (Help ▸ Edit Custom VM Options).                  |

---

### Learn More

* Official docs – [https://developer.android.com/studio](https://developer.android.com/studio)
* JetBrains Toolbox (manages Studio updates) – [https://www.jetbrains.com/toolbox-app/](https://www.jetbrains.com/toolbox-app/)
