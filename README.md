<p align="center">
  <img src="https://img.shields.io/badge/Python-3.8+-blue.svg" alt="Python">
  <img src="https://img.shields.io/badge/Platform-Windows-lightgrey.svg" alt="Platform">
  <img src="https://img.shields.io/badge/UI-PySide6%20%2B%20QFluentWidgets-green.svg" alt="UI Framework">
  <img src="https://img.shields.io/badge/License-MIT-orange.svg" alt="License">
</p>

<h1 align="center">SteamToolbox</h1>

<p align="center">
  <strong>by B-I-A-O</strong><br>
  An all-in-one Steam game toolbox — integrating depot management, Denuvo extraction, trainer downloads, manifest monitoring, and account management
</p>

---

## Feature Overview

SteamToolbox is a desktop toolbox built with PySide6 and QFluentWidgets, designed for Steam gamers and game maintenance scenarios. It consolidates multiple commonly used tools into a single modern interface. All modules support dark/light theme switching and custom wallpapers.

### Core Modules

| Module | Description |
|--------|-------------|
| **Home** | Game library overview, quick access, version update detection |
| **Local Library** | Scan and manage locally installed Steam games |
| **Account Management** | Multi-account switching and management |
| **Denuvo Extraction** | Extract Denuvo-encrypted authorization files in four modes |
| **Denuvo Authorization** | Generate GL authorization files, CW encrypted authorization files, etc. |
| **Resource Navigation** | Quick access to commonly used Steam-related websites |
| **Trainer Download** | Automatically search, download, and install trainers from FLiNG Trainer |
| **Manifest Monitor** | Real-time Steam log monitoring with automatic manifest file downloads |
| **VIP Membership** | Membership feature portal |
| **Settings** | Theme switching, wallpaper settings, key file path configuration, etc. |

---
<img width="1001" height="797" alt="屏幕截图 2026-06-18 025221" src="https://github.com/user-attachments/assets/d3bd0271-3890-4049-bee4-240e33928866" />
<img width="1003" height="798" alt="image" src="https://github.com/user-attachments/assets/f0770ae6-4a49-440e-a50e-83ef62e8e0ae" />
<img width="993" height="792" alt="image" src="https://github.com/user-attachments/assets/88058d11-d661-48fd-a174-fcfe8e99bd4d" />
<img width="991" height="795" alt="image" src="https://github.com/user-attachments/assets/c177ac77-7376-486f-92cb-3c34fd859b7a" />
<img width="996" height="794" alt="image" src="https://github.com/user-attachments/assets/64ba1ff4-cdc1-4cb4-91ab-733a4b3a4bab" />
<img width="1003" height="792" alt="image" src="https://github.com/user-attachments/assets/72610633-2e23-485c-945c-9964c694683f" />
<img width="993" height="795" alt="image" src="https://github.com/user-attachments/assets/43f0cc58-e4c9-4d71-be03-623df2ae9e7d" />
<img width="996" height="792" alt="屏幕截图 2026-06-18 025210" src="https://github.com/user-attachments/assets/99fa8d31-682f-475f-ae72-5d55d5ee5e65" />

## Feature Details

### Denuvo Extraction (Four Modes)

Obtains encrypted tickets via the Steam API, supporting four extraction modes:

- **Mode 1 — Traditional Extraction**: Generates a `configs.user.ini` configuration file containing SteamID, ticket, DLC list, and other information
- **Mode 2 — GL Authorization**: Generates the `EncryptedTicket` and `Ticket` files required for GL authorization
- **Mode 3 — Ticket to Auth Code**: Submits the encrypted ticket to a remote service, obtains a 30-minute auth code, and automatically copies it to the clipboard
- **Mode 4 — CW File Generation**: Uses AES-CBC encryption to generate `.cw` authorization files containing ticket data and DLC extension information

All modes run in isolated subprocesses to prevent DLL residue issues.

### One-Click DLC Depot Registration

Enter a game AppID to automatically complete the following workflow:

1. Retrieve the full DLC list from the Steam Store API and SteamCMD API
2. Concurrently query depot information for each DLC with up to 50 concurrent requests
3. Automatically match keys from local `depotkeys.json` and `appaccesstokens.json` files
4. Intelligently handle shared depots, fallback depots (AppID+1 through +9), depots without keys, and other edge cases
5. Auto-generate Lua configuration files and save them to the Steam directory (supports both Kernel 1 `stplug-in` and Kernel 2 `lua` paths)
6. Built-in special AppID rules (e.g., 275850, 1293830) to automatically handle known anomalies

### Trainer Download

Integrates the FLiNG Trainer library with support for:

- Dual-source crawling (Archive site + main site A-Z listing) with 24-hour local caching
- Bilingual search (Chinese/English) with built-in automatic keyword translation (Bing + MyMemory dual-engine)
- Fuzzy matching algorithm (fuzzywuzzy) with Roman numeral version number conversion
- Automatic download and extraction of ZIP/RAR/7z formats with multi-version directory management
- One-click trainer launch and deletion management

### Real-Time Manifest Monitoring

Monitors the Steam `content_log.txt` log file in real time, capturing manifest requests and downloading them automatically:

- Multi-source download strategy: prioritizes the free `gmrc.wudrm.com` API to obtain content values, then downloads manifest files via the Steam CDN
- Fallback support: ManifestHub API (requires API Key) as a secondary option
- Automatic handling of ZIP-compressed manifest files
- Thread pool management with graceful shutdown support
- Deduplication mechanism to prevent redundant downloads

### Steamless Unpacking

Integrates the Steamless.CLI tool for one-click SteamStub removal:

- Enter a store URL or AppID to automatically locate the game installation directory
- Batch-scan all exe files in the directory and unpack them one by one
- Automatic backup of original files (`.exe.bak`) with one-click restore
- Resolves common issues such as white screen error 65432, black screen errors 54/43/57, black screen on launch, and save file failures

---

## Tech Stack

| Category | Technology |
|----------|------------|
| **GUI Framework** | PySide6 + QFluentWidgets (Fluent Design) |
| **Networking** | requests (global Session connection pool), aiohttp (async concurrency), httpx |
| **Data Parsing** | BeautifulSoup4 (HTML parsing), json |
| **Encryption** | pycryptodome (AES-CBC encryption for CW files) |
| **Process Management** | multiprocessing (isolated subprocesses for extraction/monitoring tasks) |
| **Build** | Nuitka packaging support |

---

## UI Preview

- Fluent Design modern interface with one-click dark/light theme switching
- Left sidebar navigation for quick module switching
- Custom wallpaper background support
- All dialogs and popups fully adapted for dark mode

---

## Disclaimer

- This tool is intended for educational and research purposes only. Please comply with all applicable laws and regulations.
- The Denuvo extraction feature requires legitimate Steam authorization for the corresponding game.
- Trainer download data is sourced from the publicly available FLiNG Trainer site.
- Manifest downloads utilize public Steam CDN interfaces.

---

## Community

- QQ Group: [Join Now](https://qm.qq.com/q/IgSFee6ZgW)

---

<p align="center">
  <sub>Built with PySide6 + QFluentWidgets by B-I-A-O</sub>
</p>
