# PS4 & PS5 PKG Sender 📦🚀

A modern, high-performance Android application designed to seamlessly transfer and install `.pkg` files on PlayStation 4 and PlayStation 5 consoles over your local network (Wi-Fi).

Built with **Jetpack Compose (Material 3)**, the app features full support for **GoldHEN FTP Direct Streaming** and the **Remote Package Installer (RPI)**.

---

## 🌟 Key Features

### 🔄 1. Dual Transfer Modes
* **Mode 1: GoldHEN (FTP Upload)**
  * Direct FTP upload to the console's internal storage (`hdd:/data/pkg/`).
  * Custom FTP port configuration (e.g., port `2121`).
  * **Direct Streaming:** Stream Homebrew apps directly from the online store to the console via FTP without consuming phone storage space.
  * Real-time progress bar with live transfer speeds (MB/s) and statistics.

* **Mode 2: Package Sender (Remote Package Installer / RPI)**
  * Embedded high-performance HTTP server (**NanoHTTPD**) with Byte-Range support for fast streaming.
  * Sends installation trigger payloads to the console's RPI service (default port `12800`).
  * **On-Screen TV Notifications:** Sends custom notifications directly to your PS4/PS5 TV screen.
  * Advanced error diagnostics with clear troubleshooting instructions for PS4 error codes (`0x80990015`, `0x8099000C`, `0x8099008B`, etc.).

---

### 📂 2. Built-in File Explorer & Archive Extractor
* Full-featured internal file manager to navigate phone storage, Downloads, and Documents.
* **Supported Archive Formats:** Extract `.zip`, `.rar`, `.7z`, `.tar`, `.gz`, `.tgz`, and `.tar.gz` directly on your smartphone.
* **Batch Extraction:** Extract multiple archives or split archive parts in a single pass.
* Automatic detection and selection of extracted `.pkg` files.
* In-app file management: Create folders, search, filter, and delete files.

---

### 🏪 3. Integrated Homebrew Store (PKG Zone)
* Browse hundreds of PS4 Homebrew apps directly in the app powered by the PKG Zone API.
* Search and filter by category, developer name, and application title.
* **Option A:** Download the PKG to your phone storage.
* **Option B:** Direct-stream/upload from URL to your console via GoldHEN FTP without saving locally first.

---

### ⚙️ 4. Background Reliability & Network Efficiency
* **Android Foreground Service:** Equipped with **WakeLock** and **WifiLock** to keep multi-gigabyte transfers running reliably even when the screen is locked or the app is minimized.
* **Auto IP Detection:** Automatically detects your smartphone's active IP address on the local Wi-Fi network.
* **Live Logging Terminal:** Displays real-time network transaction logs, HTTP headers, server responses, and console status payloads.

---

### 🌐 5. Multi-Language Support
* 🇩🇪 **German (Deutsch)**
* 🇬🇧 **English**
* 🇸🇦 **Arabic (العربية)**

---

## 🛠️ System Requirements & Setup

### 📱 Android Smartphone
* **Android Version:** Android 7.0 (API Level 24) or higher.
* **Permissions:** Storage Access (for file browsing & archive extraction) and Notification permission.

### 🎮 Console (PS4 / PS5)
* Smartphone and console must be connected to the **same Wi-Fi network**.
* **For GoldHEN (FTP Mode):**
  * GoldHEN must be running on the console.
  * Enable the FTP Server in GoldHEN settings (default port `2121` or custom).
* **For Package Sender (RPI Mode):**
  * The **Remote Package Installer** app must be running on the PS4.
  * Default port is `12800`.

---

## 📖 Step-by-Step Usage Guide

### Mode 1: GoldHEN (FTP Upload)
1. Connect your phone and console to the same Wi-Fi network.
2. Select **GoldHEN** mode at the top of the app.
3. Enter your console's IP address and FTP port (e.g., `2121`).
4. Tap **File Explorer / Extractor** and select a `.pkg` file (or extract a ZIP/RAR/7Z archive).
5. Tap **Send**. The file will be uploaded directly to `hdd:/data/pkg/` on the console.
6. On your PS4/PS5, install the uploaded PKG using the GoldHEN Package Installer menu.

---

### Mode 2: Package Sender (HTTP Streaming / RPI)
1. Launch the **Remote Package Installer** app on your PS4.
2. Select **Package Sender** mode in the app.
3. Select a `.pkg` file and tap **Start Server**.
4. Enter your PS4's IP address (RPI port is typically `12800`).
5. Tap **Start Installation on PS4/PS5**.
6. The installation trigger will be sent, and live progress will be displayed in the app and Android status notification.

---

## 🚨 PS4/PS5 Error Codes & Solutions

| Error Code | Meaning | Solution |
| :--- | :--- | :--- |
| **`0x80990015`** | PKG / Task already exists | On PS4, go to **Notifications** -> **Downloads**, press `Options` on the old entry and delete it, then try again. |
| **`0x80990004`** | Invalid PKG format | The PKG file is corrupted or has an invalid key/content ID. Ensure it is a valid Fake PKG (fPKG). |
| **`0x8099000C`** | Storage Full | Not enough free space on PS4. Free up storage in **Settings** -> **Storage**. |
| **`0x80990088`** | Already in Task List | The download task is already active on the PS4. Check progress under **Notifications** -> **Downloads**. |
| **`0x8099008B`** | Network connection failed | The PS4 cannot reach the phone's IP address. Ensure both are on the same Wi-Fi and verify the phone's IP. |
| **`0x80990014`** | Stream aborted | Failed to read PKG header. Check Wi-Fi connection stability and ensure the file was not moved/deleted. |
| **`0x80990095`** | Firmware too old | PKG requires a newer system firmware. Use a backported PKG or update system software. |

---

## 🏗️ Architecture & Libraries

* **Language:** Kotlin
* **UI Framework:** Jetpack Compose (Material Design 3)
* **HTTP Server:** [NanoHTTPD](https://github.com/NanoHttpd/nanohttpd) (2.3.1)
* **Networking:** [OkHttp](https://square.github.io/okhttp/) (4.12.0)
* **Image Loading:** [Coil Compose](https://coil-kt.github.io/coil/) (2.7.0)
* **Archive Extraction:**
  * [Apache Commons Compress](https://commons.apache.org/proper/commons-compress/) (1.28.0)
  * [Junrar](https://github.com/junrar/junrar) (8.1.1)
  * [XZ for Java](https://tukaani.org/xz/java.html) (1.12)

---

## 👤 Developer & Credits

* **Developer / Creator:** **311Budz**
* **App Name:** PS4 & PS5 PKG Sender
* **Version:** 0.9 beta
