# Moonlight (Native Cursor Hotfix)

Moonlight PC client with native client-side cursor support for NVIDIA GameStream and Sunshine.

[![Build](https://img.shields.io/github/actions/workflow/status/imyuhan42-crypto/moonlight-hotfix/build.yml?branch=master)](https://github.com/imyuhan42-crypto/moonlight-hotfix/actions/workflows/build.yml?query=branch%3Amaster)

## Native Client-Side Cursor (Hotfix)

This build introduces native client-side mouse cursor rendering to eliminate perceived mouse pointer delay (similar to Parsec):
- **Zero-Latency Pointer**: The local client cursor is rendered natively on top of the stream at the client display refresh rate rather than waiting for round-trip host video encoding and transmission.
- **Settings Toggle**: Enable **"Show native local mouse cursor"** in Settings under **Input Settings**.
- **Interactive Shortcut**: Press **`Ctrl + Alt + Shift + C`** during an active session to toggle local cursor visibility and immediately switch to absolute mouse mode.
- **Command Line Option**: Launch with `--local-cursor` to enable native client cursor mode directly.

## Features
- Hardware accelerated video decoding on Windows, Mac, and Linux
- Native client-side cursor mode with zero latency
- H.264, HEVC, and AV1 codec support
- YUV 4:4:4 and HDR streaming support
- 7.1 surround sound audio support
- 10-point multitouch support
- Gamepad support with force feedback and motion controls for up to 16 players
- Support for both pointer capture (for games) and direct mouse control (for remote desktop)
- Support for passing system-wide keyboard shortcuts like Alt+Tab to the host

## Building

### Automated Build (GitHub Actions)
Builds are automated via GitHub Actions on every push or manual dispatch.
Compiled binaries and installers can be downloaded directly from the **Actions** tab artifacts.

### Windows Build Requirements
* Qt 6.11 SDK or later (select **MSVC** option during installation)
* Visual Studio (with C++ Build Tools)
* 7-Zip (only if building installers)

### Linux/Unix Build Requirements
* Qt 6 (or Qt 5.12+)
* GCC or Clang
* FFmpeg 4.0 or later
* Base dependencies: `libegl1-mesa-dev libgl1-mesa-dev libopus-dev libsdl2-dev libsdl2-ttf-dev libssl-dev libavcodec-dev libavformat-dev libswscale-dev libva-dev libvdpau-dev libxkbcommon-dev wayland-protocols libdrm-dev`

### macOS Build Requirements
* Qt 6.11 SDK or later
* Xcode 15 or later

### Build Setup Steps
1. Clone the repository with submodules:
   ```bash
   git clone --recursive git@github.com:imyuhan42-crypto/moonlight-hotfix.git
   ```
2. Download dependencies:
   * Windows: Run `powershell ./setup-deps.ps1`
   * macOS: Run `python3 ./setup-deps.py`
3. Build:
   * **Windows**: Run `scripts\build-arch.bat Release x64` from a Qt command prompt.
   * **Linux/macOS**: Run `qmake6 moonlight-qt.pro` followed by `make release`.
