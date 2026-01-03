---
title: "Cara Mematikan Windows Update dan Debloat Windows"
date: 2024-08-29T07:31:43+07:00
lastmod: 2025-12-16T09:23:43+07:00
tags: [Casual]
categories: [Posts]
slug: tweakWindows
thumbnailLink: "https://media.rafliard.net/content/posts/2024/08/09_disableWindowsUpdate/blockWindowsUpdate.webp"
draft: false
excludeFromSearch: false
summary: "Panduan simpel untuk mematikan/menyalakan Windows Update dengan mudah, serta cara debloat Windows secara mandiri"
---

{{< figure
    src="https://media.rafliard.net/content/posts/2024/08/09_disableWindowsUpdate/blockWindowsUpdate.webp"
    class="xl:grid-w50"
    >}}

**Update 16th Desember**

Saya rasa lebih baik mengupdate catatan ini karena ada semakin banyak tools yang bisa dipakai tanpa perlu meraba-raba secara langsung registry atau service dari Windows, kita bisa langsung menjalankan tools ini untuk melakukan perintah yang diinginkan.

Semakin hari semakin aneh perkembangan Windows 11. Dengan disuntik mati dukungan Windows 10 di bulan Oktober kemarin, kini banyak pengguna yang migrasi ke Windows 11 namun versi Windows ini jauh lebih banyak bermasalahnya dibandingkan reliabel secara penggunaan. Secara pribadi saya menemukan mematikan Windows Update agar tidak berjalan di background membuat komputer yang memakai Windows 11 membuat sistem jauh lebih stabil dibandingkan yang _terhubung_ 24/7 dengan channel update Windows. Kemudian user bisa melakukan _debloat_ sistem secara mandiri karena lebih aman secara sistem integrity dan cybersecurity (tidak mendownload secara bebas online)

## Cara Mematikan/Disable Windows Update (Bisa Dinyalakan Kembali)

Kita bisa menggunakan salah satu tool yang ada di Github, secara pribadi saya menggunakan repo ini karena cukup _straightforward_. Kita bisa membaca lewat panduan di Github repo tersebut

{{< github repo="tsgrgo/windows-update-disabler" showThumbnail=false >}}

### 1. Clone repo dengan `git` atau download sebagai Zip

[Klik untuk mendownload versi terbaru dari Zip file](https://github.com/tsgrgo/windows-update-disabler/archive/refs/heads/main.zip)

### 2. Extract `windows-update-disabler-main.zip`

### 3. Jalankan `disable updates.bat` untuk mematikan Windows Update

### 4. Jika ingin melakukan update, bisa jalankan `enable updates.bat`, lakukan proses update, lalu matikan kembali dengan `disable updates.bat`

<hr>

## Cara Debloat Windows

Beberapa tools utility seperti W4RH4WK/Debloat-Windows-10 dan LeDragoX/Win-Debloat-Tools telah diarsipkan karena sifatnya yang berfokus ke Windows 10 namun bisa juga digunakan di Windows 11, sehingga saya berpindah untuk menggunakan tools dari Chris Titus, repo bisa di akses di sini.

{{< github repo="ChrisTitusTech/winutil" showThumbnail=false >}}

### 1. Jalankan "Windows PowerShell (Admin)" (untuk Windows 10) atau "Terminal (Admin)" (untuk Windows 11).

### 2. Kemudian copypaste line dibawah ini ke PowerShell/Terminal

```bash
irm "https://christitus.com/win" | iex
```

### 3. Baca dokumentasi untuk apa saja yang bisa di uninstall

[Untuk info lebih lanjut bisa membaca dokumentasi di Repo/situs Chris Titus](https://github.com/ChrisTitusTech/winutil?tab=readme-ov-file#-documentation)

Gimana, sangat mudah kan? Kunci utama agar sukses adalah RTFM!🔥