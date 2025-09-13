<!-- Badges (replace YOUR_USERNAME) -->
<h1 align="center">ESP-IDF Starter — Production Template</h1>
<p align="center">
Robust, batteries-included starter for ESP32/ESP32-S3/ESP32-C3 with FreeRTOS, OTA, MQTT, logging, tests, and CI artifacts.
</p>

<p align="center">
  <a href="https://github.com/YOUR_USERNAME/esp-idf-starter/actions">
    <img alt="CI" src="https://img.shields.io/github/actions/workflow/status/YOUR_USERNAME/esp-idf-starter/ci.yml?label=CI&logo=githubactions">
  </a>
  <img alt="ESP-IDF" src="https://img.shields.io/badge/ESP--IDF-5.x-EA3?logo=espressif">
  <img alt="License" src="https://img.shields.io/badge/License-MIT-2c2d84">
  <img alt="Conventional Commits" src="https://img.shields.io/badge/Conventional%20Commits-1.0.0-ff6f00.svg">
  <img alt="Made with C/C++" src="https://img.shields.io/badge/C/C++-✓-00599C">
</p>

---

## ✨ Why this template?
- **Production-oriented**: sane defaults, error handling, structured logging, release artifacts.
- **OTA-ready**: HTTP OTA with dual partitions and rollback.
- **Connectivity**: Wi-Fi + (optional) MQTT client with backoff/reconnect.
- **Configurable**: Kconfig options + `sdkconfig.defaults` + secrets header.
- **Testable**: Unity tests (`idf.py test`) for logic-level code.
- **Automated**: GitHub Actions builds artifacts on every push and for tagged releases.
- **Clean layout**: modular components (`app_core`, `app_net`, `app_ota`, `drivers`).

---

## 🧩 Supported targets
`esp32` · `esp32s3` · `esp32c3`  
> select with `idf.py set-target <chip>`

---

## 🗂 Project layout
```plaintext
esp-idf-starter/
├─ main/
│  ├─ app_main.c                  # Main application entry point
│  ├─ CMakeLists.txt              # CMake build configuration for the main app
├─ components/
│  ├─ app_core/                   # Core functionality like logging, versioning, checks
│  │  ├─ app_log.h                # Structured logging system
│  │  ├─ app_checks.h             # Error checks and handling
│  │  ├─ version.h                # Versioning macros
│  │  ├─ Kconfig                  # Configuration options
│  │  └─ CMakeLists.txt           # Build configurations for the core component
│  ├─ app_net/                    # Networking functionality like Wi-Fi & MQTT
│  │  ├─ wifi.c                   # Wi-Fi connection management
│  │  ├─ mqtt.c                   # MQTT client functionality
│  │  ├─ Kconfig                  # Network configuration options
│  │  └─ CMakeLists.txt           # Build configurations for networking component
│  └─ app_ota/                    # OTA update mechanism
│     ├─ app_ota.c                # HTTP OTA functionality
│     ├─ Kconfig                  # OTA-specific configurations
│     └─ CMakeLists.txt           # Build configurations for OTA component
├─ drivers/                       # Custom peripheral drivers (e.g., sensors, displays)
│  └─ (examples) shtxx.c, ssd1306.c
├─ tests/                         # Unit tests for the logic-level code (using Unity)
│  ├─ test_app_core/              # Unit tests for app_core module
│  └─ CMakeLists.txt              # Test build configurations
├─ partitions.csv                 # Partition table with dual OTA slots
├─ sdkconfig.defaults             # Default configurations for SDK
├─ .clang-format                  # Code formatting rules
├─ .gitignore                     # Git ignore file
└─ .github/workflows/ci.yml       # GitHub Actions CI configuration
```
---
##📊 Visualization of the Project Layout
```mermaid
graph LR
  A[app_core] -->|Contains| B[Logging System]
  A -->|Contains| C[Version Control]
  A -->|Contains| D[Error Checks]
  A -->|Links to| E[app_net]
  E[app_net] -->|Contains| F[Wi-Fi Connection]
  E -->|Contains| G[MQTT Client]
  E -->|Links to| H[app_ota]
  H[app_ota] -->|Contains| I[OTA Update]
  F -->|Handles| J[Wi-Fi Reconnection]
  G -->|Handles| K[MQTT Communication]
  I -->|Updates| L[OTA Mechanism]
  subgraph Test
    direction TB
    M[Test Unit 1]
    M --> N[Test Unit 2]
    M --> O[Test Unit 3]
  end

