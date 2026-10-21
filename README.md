# Mass Visual Studio

**IDE C# untuk Linux** dengan tampilan ala Visual Studio. Dibangun dengan Electron + Monaco,
dan benar-benar bisa build, run, test, serta mengelola project C# lewat `dotnet` CLI.

> **Milik pribadi Matthew (BmatthewT).** Copyright &copy; 2026 Matthew. All rights reserved.
> Aplikasi ini **bukan** produk Microsoft dan tidak memuat kode/aset Visual Studio.
> Dilarang mengedit, memodifikasi, atau mendistribusikan ulang tanpa izin tertulis.

---

## Download (Linux)

Ambil file terbaru dari halaman **[Releases](../../releases/latest)**:

| File | Cocok untuk |
|---|---|
| `MassVisualStudio-1.0.1-x86_64.AppImage` | Hampir semua distro Linux x86_64 (portable, tanpa install) |
| `MassVisualStudio-1.0.1-amd64.deb` | Debian / Ubuntu / Linux Mint |

### AppImage

```bash
chmod +x MassVisualStudio-1.0.1-x86_64.AppImage
./MassVisualStudio-1.0.1-x86_64.AppImage
```

Kalau muncul error `libfuse.so.2`:

```bash
# Arch / Manjaro
sudo pacman -S fuse2

# Debian / Ubuntu
sudo apt install libfuse2
```

Atau jalankan tanpa FUSE:

```bash
./MassVisualStudio-1.0.1-x86_64.AppImage --appimage-extract-and-run
```

### Debian / Ubuntu (.deb)

```bash
sudo dpkg -i MassVisualStudio-1.0.1-amd64.deb
sudo apt -f install
```

Lalu cari **Mass Visual Studio** di menu aplikasi.

---

## Kebutuhan

- **Linux x86_64** (diuji di Arch Linux, X11 dan Wayland)
- **.NET SDK 10** untuk build/run project C#
  - Cek: `dotnet --version`
  - Kalau belum ada: <https://dotnet.microsoft.com/download>
- Untuk fitur AI opsional: API key provider (GitHub Models / OpenAI-compatible / Ollama)

Aplikasi mendeteksi `.NET SDK` otomatis, termasuk yang terpasang di `~/.dotnet`
walaupun dibuka dari launcher (tidak perlu mengatur `PATH` manual).

---

## Fitur

- Solution Explorer, tab editor Monaco, syntax highlight C#
- Build / Rebuild / Clean lewat `dotnet`
- Run dan Debug dengan output + input interaktif di **terminal bawaan**
- Error List dari output MSBuild (klik untuk lompat ke baris)
- Test Explorer (`dotnet test`)
- NuGet: cari, install, dan hapus package
- Git Changes: status, stage, diff, commit, fetch/pull/push
- Find in Files (regex + filter ekstensi)
- Panel AI bergaya Copilot (opsional): chat, `/explain`, `/fix`, `/tests`, `/doc`
- Snippet C# (`cw`, `prop`, `ctor`, `foreach`, ...), format document
- Tema Mass Purple / Mass Blue / Mass Dark
- Watermark dan proteksi kepemilikan file aplikasi

---

## Cara pakai cepat

1. Buka **File → Open Folder** ke folder project C#.
2. **Ctrl+Shift+B** untuk build.
3. **F5** atau **Ctrl+F5** untuk run — output muncul di tab **Terminal**.
4. Saat program meminta input (`Console.ReadLine`), ketik di kolom terminal lalu Enter.
5. **Ctrl+Shift+N** untuk membuat console project baru.

---

## Proteksi & lisensi

- Aplikasi memeriksa integritas file inti saat startup. File yang dimodifikasi akan
  membuat aplikasi menolak berjalan.
- File aplikasi tidak dapat dibuka atau diubah dari dalam editor.
- Kode sumber tidak dipublikasikan. Repo ini hanya mendistribusikan build resmi.
- Ketentuan lengkap: lihat [LICENSE](LICENSE).

Tidak ada proteksi client-side yang benar-benar absolut—siapa pun yang menguasai
perangkatnya secara teknis tetap bisa melakukan reverse engineering. Build resmi
disediakan apa adanya untuk dipakai, bukan untuk dimodifikasi.

---

## Troubleshooting

| Gejala | Solusi |
|---|---|
| `libfuse.so.2` tidak ditemukan | Install `fuse2` / `libfuse2`, atau pakai `--appimage-extract-and-run` |
| Jendela hitam di Wayland | `./MassVisualStudio-1.0.1-x86_64.AppImage --ozone-platform-hint=auto` |
| `dotnet` tidak terdeteksi | Install .NET SDK 10; aplikasi mencari `~/.dotnet`, `/usr/share/dotnet`, dll. |
| `Console.ReadLine()` tidak menerima input | Pastikan program dijalankan lewat F5/Ctrl+F5 dan ketik di tab Terminal |
| Error sandbox di beberapa distro | Jalankan AppImage dengan `--no-sandbox` |

---

<div align="center">

**Mass Visual Studio** — dibuat dan dimiliki oleh **Matthew (BmatthewT)**.

`CREATED BY MATTHEW`

</div>
