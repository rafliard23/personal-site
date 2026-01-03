---
title: "SSD SATA, Form Faktor yang Mulai Ditinggalkan?"
date: 2024-01-08T18:34:07+07:00
lastmod:
tags: [Computer]
categories: [Posts]
slug: SSD_Sata_Dead
thumbnailLink: "https://media.rafliard.net/content/posts/2024/01/08_SSDSATADead/SSDSATA_Upgrade.webp"
draft: false
summary: "Baru-baru ini saya memiliki rencana untuk merubah tipe penyimpanan laptop yang saat ini saya miliki untuk menjadi setup Full SSD (M.2 NVMe & SSD SATA). Naun SSD SATA sekarang lebih susah untuk dicari dengan kualitas komponen yang mumpuni misalkan kebutuhan DRAM untuk SSD SATA. Akhirnya saya memutuskan untuk mencari tahu referensi dahulu..."
excludeFromSearch: true
---
{{< figure
    src="https://www.online-tech-tips.com/wp-content/uploads/2018/08/ssd-drive-comparison.jpg"
    alt="SSD Drive by Online Tech Tips (2018)"
    class="md:grid-w50"
    >}}

Baru-baru ini saya memiliki rencana untuk merubah tipe penyimpanan laptop yang saat ini saya miliki untuk menjadi setup Full SSD (M.2 NVMe & SSD SATA). Tentunya saya juga senang karena sistem yang saat ini saya gunakan sebagai daily drive masih bertahan di tangan saya selama 5 tahun (meskipun sempat ada masalah karena EEPROM BIOS tiba-tiba corrupt), dengan maintenance yang rutin minimal 1 tahun sekali untuk penggantian thermal paste serta custom TDP limit agar CPU Intel yang saya pakai ini bisa berjalan dengan power yang lebih rendah dan dingin.

*Fast forward*, kesenangan ini hanya bertahan sebentar ketika saya mencari referensi SSD SATA dan menemukan di E-Commerce di Indonesia, beberapa dari model SSD ini ada yang tidak dijual di pasar Indonesia, memiliki firmware yang bermasalah, masalah performa, atau bahkan sulitnya menjamin kualitas produk (e.g komponen internal yang sering dirubah, sehingga menyulitkan untuk menjamin kualitas produk). Mungkin pembaca penasaran kok sebegitu lebay nya ini penulis atau bahkan memiliki *trust issue* dengan SSD SATA? Jika ingin saya jelaskan secara singkat, saya menginginkan untuk kriteria SSD yang memiliki penyimpanan minimal 1TB, memiliki DRAM atau Cache agar menunjang performa dari SSD untuk kebutuhan sehari-hari, serta SSD ini nantinya digunakan sebagai penyimpanan tetap sebagai pengganti HDD 2.5" yang aslinya tersematkan pada laptop saya.

{{< figure
    src="https://media.rafliard.net/content/posts/2024/01/08_SSDSATADead/SATASSD_PartOfNewmaxx.webp"
    alt="u/Newmaxx SSD Guide"
    href="https://ssd.borecraft.com/SSD_Buying_Guide.svg"
    caption="Cuplikan dari Newmaxx's SSD Buying Guide oleh [Newmaxx.](https://borecraft.com/) Klik untuk Gambar penuh dari SSD Guide."
    class="md:grid-w80"
    >}}

Opsi untuk memilih Entry Level SSD saya tinggalkan karena tujuan dari penggunaan saya yakni agar data-data yang tersimpan tersimpan setidaknya 6-7 Tahun dari pembelian SSD yang dipakai, hal tersebut membuat opsi menggunakan SSD Curah, dan merk *Aliexpress* saya blacklist dari pilihan :). Alasan saya tidak menggunakan ADATA SU650 karena saya khawatir dengan ketahanan dari Data NAND nya karena kontroler yang digunakan oleh SU650 sering berubah-ubah dan terakhir dengan casing yang baru juga memiliki perubahan pada kontroler dan flash NAND yang digunakan [dari laporan salah satu pengguna di forum Techpowerup](https://www.techpowerup.com/ssd-specs/adata-ultimate-su650-240-gb.d1678). Selain hal tersebut, saya juga memiliki *trust issue* dengan ADATA karena lini produk SSD NVMe mereka juga sering ganti komponen internal dengan <ins>[kualitas komponen yang lebih buruk dibandingkan yang digunakan sebagai tes benchmark oleh para jurnalis](https://www.tomshardware.com/news/adata-and-other-ssd-makers-swapping-parts)</ins> dan <ins>[hal tersebut telah dilakukan berkali-kali dengan model yang berbeda.](https://www.tomshardware.com/news/adata-switches-nand-on-sx8200-pro-ssd-performance-impacted)</ins>

Dari hal tersebut kita hanya dibatasi dengan pilihan dari Mid-Range: Addlink S20, High-End: Crucial MX500, Samsung 860 EVO/870 EVO, SanDisk Ultra 3D, dan WD Blue 3D NAND. Beberapa SSD di atas menggunakan kontroler SM2258/SM2259 yang baru-baru ini memiliki masalah kualitas seperti [MX500](https://www.reddit.com/r/sysadmin/comments/whr5ek/crucial_mx500_historically_good_recent_batches/) yang [memiliki masalah pada firmware](https://www.reddit.com/r/homelab/comments/110u5de/warning_crucial_mx500_ssd_firmware_bug_can/), [870 EVO](https://www.reddit.com/r/DataHoarder/comments/113uibg/samsung_ssd_870_evo_good_with_uncorrectable_error/) memiliki [masalah pada kualitas karena kebanyakan dari model yang bermasalah pada rentang Periode produksi 2021-2022 (Covid Chip Shortage).](https://www.techpowerup.com/forums/threads/samsung-870-evo-beware-certain-batches-prone-to-failure.291504/)

Sandisk Ultra 3D dan WD Blue 3D NAND sejatinya adalah produk yang sama dengan branding yang berbeda (Sandisk dimiliki oleh Western Digital) sehingga bisa dipilih salah satu dari kedua opsi itu. Namun hal menarik yang saya temui ketika mencari dengan kata kunci WD Blue 3D, saya menemukan beberapa toko yang mengiklankan produk dengan judul "Blue 3D" namun ketika kita masuki, ternyata barang yang dijual menjadi "Blue SA510" [dengan spesifikasi yang lebih setara dengan SSD SATA Entry-level dibandingkan kelas High-level.](https://www.techpowerup.com/ssd-specs/western-digital-blue-sa510-500-gb.d851)

{{< figure
    src="https://media.rafliard.net/content/posts/2024/01/08_SSDSATADead/SATASSD_WDBlue3DFake.webp"
    alt="SA510 Scam"
    caption="Salah satu toko yang mengiklankan \"Blue SA510\" dengan keyword \"Blue 3D NAND\""
    class="md:grid-w45"
    >}}

Karena budget saya sedikit "memaksa" untuk 1 Juta atau dibawah itu untuk ukuran 1TB. Akhirnya saya memutuskan untuk memilih Addlink S20 karena pertimbangan adanya DRAM agar memperpanjang umur dan performa dari SSD.

{{< figure
    src="https://media.rafliard.net/content/posts/2024/01/08_SSDSATADead/SATASSD_PCIeNVMeAdapter.webp"
    alt="PCIe NVMe Adapter"
    caption="Salah satu PCIe M.2 Adapter yang hadir mendukung hingga PCIe4 x4 M.2 NVMe"
    class="md:grid-w45"
    >}}

Dan untuk menjawab pertanyaan dari judul saya, bisa saya jawab **Ya**, dan **Tidak**. Jika pembaca berniat ingin membangun homelab server secara budget atau kecil-kecilan, menggunakan SSD Entry-level sebagai bootdrive adalah hal yang cukup tidak perlu terlalu overkill (secara ukuran dan kualitas) karena kebanyakan proses Read dan Writing berada pada Data drive/storage, pada kasus ini <ins>**Anda dapat menggunakan SSD SATA jika motherboard atau sistem yang anda miliki tidak memiliki slot M.2.**</ins> Jika pembaca ingin menggunakan SSD SATA sebagai **Storage drive atau Data drive**, maka saya secara kuat **tidak menyarankan** hal tersebut karena secara value menggunakan HDD dengan RAID setup bisa menghasilkan space penyimpanan yang lebih besar atau backup yang lebih aman. Selain itu anda juga dapat menggunakan PCIe to M.2 Adapter untuk merubah slot PCIe yang kosong di PC anda menjadi siap digunakan untuk menerima tambahan penyimpanan data dengan SSD NVMe.

