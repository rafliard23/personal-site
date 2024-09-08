---
title: "Cara Disable Windows 10 Update (Reversible)"
date: 2024-08-29T07:31:43+07:00
lastmod:
tags: [Casual]
categories: [Posts]
slug: disable_Win_Update
thumbnailLink: "https://drive.google.com/uc?export=view&id=1DJV8OJ-S9XRSeJFOHzXXINjIjyc9NH1P"
draft: false
index: true
---

Postingan ini saya terbitkan sebagai backup untuk catatan pribadi dan barangkali berguna bagi pembaca blog ini karena kekhawatiran jika suatu ketika postingan asli nya akan terhapus. Metode yang digunakan bersifat _reversible_ sehingga pemblokiran bisa dibuka kembali dan proses Windows Update bisa berjalan normal. Untuk memblokir Windows Update kita perlu mematikan 3 service, "Update Orchestrator Service", "Windows Update", "Windows Update Medic Service".

Credits: [u/ikashanrat](https://www.reddit.com/user/ikashanrat/) sebagai pembuat post Reddit, dan [TechGeekEek](https://youtu.be/6atgKRQjsKA) sebagai pembuat video

{{< alert icon="triangle-exclamation" cardColor="yellow" iconColor="black" textColor="black" >}}
Ketika service Windows Update di blokir, Microsoft Store tidak bisa di akses hingga service dinyalakan kembali.
{{< /alert >}}

## Versi Text

1. Buka ``regedit`` / Registry Editor jika ada promot, klik OK
2. Buka ``HKEY_LOCAL_MACHINE/SYSTEM/CurrentControlSet/Services``
3. Kemudian cari ``UsoSvc``, klik kanan kemudian klik Permissions
4. Klik Advanced, kemudian klik change owner
5. Klik Advanced
6. Klik Find now
7. Pilih Administrator
8. Klik OK, kemudian klik OK lagi
9. Unceklis "Disable inheritance"
10. Klik "Remove all inherited permissions from this object"
11. Ceklis "Replace all child object permissions..."
12. Klik Apply
13. Klik Yes, lalu klik Yes
14. Lakukan langkah 3-13 dengan "WaaSMedicSvc" dan "wuauserv"

Untuk mengonfirmasi bahwa langkah-langkah di atas telah berhasil:

1. Klik Start kemudian ketik "Run" tekan Enter
2. Ketik "Services.msc", tekan Enter
3. Selanjutnya klik "Action", pilih "Refresh"
4. "Update Orchestrator Service", "Windows Update", "Windows Update Medic Service" akan memiliki error pada bagian deskripsi service masing-masing.
5. Restart Windows
6. Klik Start kemudian ketik "Check for Update"
7. Jika muncul "Something went wrong. Try to reopen settings later" maka proses berhasil.

## Versi Video

{{< youtubeLite id="6atgKRQjsKA" label="Windows 10 Update Disable" >}}