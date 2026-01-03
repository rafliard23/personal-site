---
title: "Simple Universal Bluetooth Audio Receiver"
date: 2024-12-02T18:51:33+07:00
lastmod:
tags: [Electrics]
categories: [Posts, Projects]
slug:
thumbnailLink: "https://media.rafliard.net/content/projects/audioReceiver/ar-bts_asm_proto.webp"
summary: "Project originated simply as idea during my time as undergrad student. Finally realized universal wired-to-wireless audio utilizing off-the-shelf Bluetooth receiver module, battery pack and charge controller. Rechargeable module and long-lasting!"
draft: false
excludeFromSearch: true
---

This project actually conceived way back in my college time when I write undergraduate thesis yet I work it just recently. Due to the project nature, I just wrote it as archive as I don't think I would delve into audio (unless sudden urge to make custom one lol).

## Why use off-the-shelf module?
First off, If I want to make it fast I rather use off-the-shelf component not to mention here in Indonesia buying advanced Bluetooth reciever audio IC is hard and you have to import them to make custom board.

## Device concept
{{< figure
    src="https://media.rafliard.net/content/projects/audioReceiver/ar-wiring.webp"
    alt="Device wiring"
    caption="Wiring Device"
    class="w-50"
    >}}

I _designed_ this device with portability in mind while retain universal and functional aspect however as we later learn, we found roadblock for two-way communication (we could only use receive). I use 2.000 mAh Li-ion battery to power the device, and connect it with Li-ion battery charger module so I could charge it. Our module selection use 3.5mm port which makes it more lenient whether I want to connect it into speaker or to drive an IEM/headphone.

## Selecting wireless Bluetooth receiver

I did not-so-extensive research in this topic as I deem it is too rabbit hole for me if we also include these JieLi ICs modules (I will put on link at the end of this section). To put it simply we have several off-the-shelf module that available in Indonesia. Picked MH-M28 as it have exposed 3.5mm jack and based from personal test I found MH-M28 have better audio result in my IEM KZ ZS3.

Here the table that discuss each features of modules
| Feature | ![](https://media.rafliard.net/content/projects/audioReceiver/ar-mh_m18.webp "**MH-M18**") | ![](https://media.rafliard.net/content/projects/audioReceiver/ar-mh_m28.webp "**MH-M28**") | ![](https://media.rafliard.net/content/projects/audioReceiver/ar-mh_m38.webp "**MH-M38**") | ![](https://media.rafliard.net/content/projects/audioReceiver/ar-vhm314.webp "**VHM314**") |
| :---: | :---: | :---: |  :---: | :---: |
| Power Supply | 5V, Battery | USB, 5V, Battery | USB, 5V, Battery | USB, 3.3V, Battery |
| 3.5mm Jack | ❌ | ✔ | ❌ | ✔ |
| Built-in Amplifier | ❌ | ❌ | (5W + 5W) | ❌ |
| Bluetooth Ver. | 4.2 | 4.2 | 4.2 | 5.0 |
| Button Interface | ✔ | ❌ | ❌ | ❌ |

Personal note:  
Most of these cheap wireless receiver module use JieLi cloned IC. [This github user document his study of these controllers, I recommend to read them in case you are interested with these ICs.](https://github.com/christian-kramer/JieLi-AC690X-Familiarization) JieLi's module have variety of form factor ranging from SOIC-16 all the way to QFP. Personally I have hunch that these audio module use these JieLi [due to said github user remark that "MH-M18" module use JieLi IC that has not scrubbed its IC marking.](https://camo.githubusercontent.com/be9dba30b418bb6ed952c691872ee4996a7216ba95a456335a171ce45cd1eb6e/68747470733a2f2f692e696d6775722e636f6d2f61783252695a502e706e67)


## Behind the Scene

{{< gallery >}}
  <img src="https://media.rafliard.net/content/projects/audioReceiver/ar-bts_solder.webp" class="grid-w25 md:grid-w33" />
  <img src="https://media.rafliard.net/content/projects/audioReceiver/ar-bts_on.webp" class="grid-w25 md:grid-w33" />
  <img src="https://media.rafliard.net/content/projects/audioReceiver/ar-bts_asm_proto.webp" class="grid-w25 md:grid-w33" />
{{< /gallery >}}

## Further reading
https://avdweb.nl/tech-tips/electronics/mh-m18-m28-m38-bluetooth-audio-receiver-amplifier-tear-down  
https://oshwlab.com/hichm/bleutooth-5-audio  
https://www.reddit.com/r/AC690X/  
https://kagaimiq.github.io/jielie/chips/chip-marks.html