# 💬 AlgoCraft-ChatSystem

![Minecraft Version](https://img.shields.io/badge/Minecraft-1.21-brightgreen)
![PaperMC](https://img.shields.io/badge/Server-PaperMC%20%7C%20Purpur-blue)
![Java Version](https://img.shields.io/badge/Java-21-orange)
![License](https://img.shields.io/badge/License-MIT-yellow)

**AlgoCraft-ChatSystem** adalah plugin manajemen chat modern, ringan, dan sangat teroptimasi yang dirancang khusus untuk server Minecraft versi **1.21+** (Paper/Purpur). Didukung oleh Adventure API & MiniMessage, plugin ini memberikan kontrol penuh atas format obrolan server Anda dengan performa asinkron yang efisien.

---

## ✨ Fitur Utama

- 🚀 **High Performance Async Chat:** Memproses obrolan menggunakan `AsyncChatEvent` & `MessageRenderer` milik Paper API tanpa membebani *main server thread*.
- 🎨 **Modern Formatting Support:**
  - Full **MiniMessage** support (`<red>`, `<gradient:#00E5FF:#0073E6>Text</gradient>`, dll.).
  - Support Legacy Hex Color Code (`&#RRGGBB`).
  - Support Ampersand Color Code (`&a`, `&l`, `&r`).
- 🛡️ **Anti-Spam & Chat Filter:**
  - Sistem cooldown pesan berbasis detik dengan izin bypass.
  - Blacklist kata-kata terlarang otomatis.
- 🔌 **Seamless Soft Dependencies:**
  - **PlaceholderAPI:** Mendukung penggunaan placeholder di pesan maupun format chat.
  - **LuckPerms:** Integrasi prefix, suffix, dan hirarki group permission.
- 👑 **Permission-based Group Chat Format:**
  - Pengaturan format chat unik untuk tiap grup/rank (VIP, Donator, Staff, Default) via `config.yml`.

---

## 🛠️ Perintah & Izin (Permissions)

### Commands
| Command | Deskripsi | Permission |
| :--- | :--- | :--- |
| `/chatsystem reload` | Memuat ulang konfigurasi plugin (`config.yml`). | `chatsystem.admin` |

### Permissions
- `chatsystem.admin` – Akses perintah reload plugin (Default: OP).
- `chatsystem.bypass.cooldown` – Bypass sistem cooldown anti-spam (Default: OP).
- `chatsystem.bypass.filter` – Bypass sensor kata terlarang (Default: OP).
- `chatsystem.color` – Izin menggunakan format warna (`&` dan `&#hex`) di obrolan (Default: OP).
- `chatsystem.group.<nama_group>` – Izin untuk menggunakan format obrolan grup spesifik.

---

## ⚙️ Konfigurasi (`config.yml`)

```yaml
PREFIX: "<bold><gradient:#00E5FF:#0073E6>ALGOCRAFT</gradient></bold> <gray>»</gray> "

messages:
  reload-success: "<green>Konfigurasi berhasil diperbarui!</green>"
  no-permission: "<red>Anda tidak memiliki izin untuk menggunakan perintah ini.</red>"
  cooldown: "<red>Tunggu <yellow>{time}</yellow> detik sebelum mengirim pesan lagi.</red>"
  filtered-word: "<red>Pesan Anda mengandung kata yang tidak diperbolehkan!</red>"

antispam:
  cooldown: 3 # Dalam detik
  filter-chat:
    - "kata_terlarang1"
    - "kata_terlarang2"

chat-system:
  vip:
    permission: "chatsystem.group.vip"
    format: "%luckperms_prefix% <gold><bold>[VIP]</bold></gold> %player_name% <gray>»</gray> <white>%chatsystem_chat%</white>"
  default:
    permission: ""
    format: "%luckperms_prefix% <gray>%player_name% »</gray> <white>%chatsystem_chat%</white>"
