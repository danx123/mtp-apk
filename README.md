# 🐯 MTP — Macan Transfer Protocol

<p align="center">
  <img src="https://img.shields.io/badge/Release-v1.1.4-FF9E0B?style=for-the-badge" alt="Release Version" />
  <img src="https://img.shields.io/badge/Platform-Android-3DDC84?style=for-the-badge&logo=android&logoColor=white" alt="Platform" />
  <img src="https://img.shields.io/badge/Architecture-Jetpack%20Compose-4285F4?style=for-the-badge" alt="Jetpack Compose" />  
</p>

**Fast local file transfer for Android.** Send files between devices over Wi-Fi Direct with QR pairing, share your phone's storage with a PC over FTP, and verify every file with MD5 and SHA-256 integrity checks. No cloud, no accounts, no mobile data.

---
## Screenshot

<img width="1176" height="1280" alt="sc-mtp" src="https://github.com/user-attachments/assets/e20206b5-7425-4065-b4ea-c70be2f00cd8" />

---

## Features

### 📡 Wi-Fi Direct Transfer
- Peer-to-peer file transfer between two Android devices on the same local link (Wi-Fi Direct group or the same Wi-Fi network)
- **QR pairing:** the receiver shows a QR code, the sender scans it, picks a file, and sends
- Manual IP and port entry as a fallback (default port `8988`)
- Live progress and transfer speed
- The receiver automatically verifies the file against the hashes sent by the sender

### 🗂️ FTP Hub
**FTP Server** — turn your phone into an FTP server and browse it from a PC, browser, or any FTP client such as FileZilla:
- Browse **internal storage** and **external storage** (SD card / USB OTG) as separate drives
- Editable port, username, and password, **saved automatically** between app launches
- Instant connection QR code and one-tap copy of the FTP URL
- Live server activity log
- Supports download, upload, create folder, rename, and delete

**FTP Client** — connect to an FTP server (for example, one running on your PC):
- Browse remote folders, download files, and upload files from your phone
- Optional anonymous login
- Connection details are remembered

### 🛡️ Hash Verifier
- Compute **MD5** and **SHA-256** of any file in a single pass
- Paste an expected hash from a sender or website and get an instant match / mismatch result
- Quick text hash calculator

### 🕘 History
- Log of completed transfers with integrity status
- Filter by Wi-Fi Direct, FTP, or verified-only

### Other
- Keep-screen-on option so long transfers are not interrupted
- Dark interface
- Bilingual: **English** and **Bahasa Indonesia** (auto-detect or choose manually)

---

## Installation

1. Download the latest `mtp_v1.1.0.apk` from the **Releases** page.
2. Open the file on your Android device.
3. If prompted, allow installation from your browser or file manager ("Install unknown apps").
4. Install and open **MTP**.

> Android may show a warning because the app is not distributed through the Play Store. This is expected for APKs installed manually.

---

## Permissions

| Permission | Why it is needed |
|---|---|
| **Camera** | Scanning pairing QR codes |
| **All files access** | Letting the FTP server expose internal and external storage, and saving received files to `Downloads/MTP_Downloads` |
| **Nearby Wi-Fi devices / Location** | Required by Android for Wi-Fi Direct features |
| **Network / Wi-Fi state** | Detecting your local IP address and connection status |
| **Keep awake** | Preventing the screen from sleeping during transfers |

All transfers happen directly between devices on your local network. MTP does not upload your files to any server.

---

## Quick Start

### Send a file between two phones
1. On the receiving phone, open **Wi-Fi Direct** and turn on **Receiver Mode**. A QR code appears.
2. On the sending phone, tap **Scan QR** and scan the code (or use **Manual IP**).
3. Tap **Select File & Send Now** and choose a file.
4. When the transfer finishes, both devices show the integrity result. Received files are saved in `Downloads/MTP_Downloads`.

### Access your phone from a PC over FTP
1. Open the **FTP Hub** tab and, in **FTP Server (Host)**, set your port, username, and password, then tap **Save & Apply Changes**.
2. Grant **All files access** when asked, so internal and external storage are available.
3. Turn the server **on**.
4. On your PC, connect to the URL shown in the app, for example `ftp://username:password@192.168.1.10:2121`, or enter the host, port, username, and password in FileZilla.
5. You will see your drives as top-level folders: `Internal`, and `SDCard` if a card is installed.

> Both devices must be on the same network (or connected via Wi-Fi Direct).

---

## Security Notes

- **FTP is not encrypted.** Credentials and file contents travel in plain text, so only use the FTP server on networks you trust (your home Wi-Fi or your own hotspot), and turn it off when you are done.
- Choose a strong FTP password. The FTP server requires a login; anonymous access is disabled on the server.
- Without **All files access**, the FTP server only exposes the app's own folder (`/App`).

---

## Troubleshooting

**The PC cannot connect over FTP**
Check that both devices are on the same network, the server is running, and the port is not blocked by a firewall. Use the IP address shown in the app.

**I only see an `App` folder on the PC**
Grant **All files access** in the app's storage card, then turn the FTP server off and on again.

**The SD card does not appear**
Make sure the card is mounted and readable in your file manager, then restart the FTP server.

**The QR code will not scan**
Increase screen brightness on the receiving phone, or use **Manual IP** and enter the address shown on the receiver.

**Hash mismatch**
The file was probably corrupted or modified in transit. Send it again and compare the hashes.

---

## Feedback

Found a bug or have a suggestion? Please report it and include your Android version, device model, and the steps to reproduce.

---

© Macan Angkasa. All rights reserved.
