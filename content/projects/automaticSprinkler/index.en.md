---
title: "Automatic Sprinkler Sprayer (STM32)"
date: 2024-08-26T14:42:35+07:00
lastmod:
tags: [Automation, Electrics, Embedded Systems]
categories: [Posts, Projects]
slug: automatic_sprinkler
thumbnailLink: "https://media.rafliard.net/content/projects/automaticSprinkler/ASS-testing.webp"
summary: "Automated plant watering system utilizing controller, and Input/Outputs. Spraying determined by sensor input or set timer."
draft: false
excludeFromSearch: false
---

This project originally take place between October - December 2023, due to demand from my relative, I decided to continue the effort.

## Problem

This project was conceived due to my relative idea to automate watering plant process in his front yard and indoor garden. I proposed the idea and design the hardware right away with information from my relative.

## Planning

After I propose and discuss my design with relative, relative agreed with my plan and then we move to program, component selection, PCB layout design and test. Here I provide the diagram block of the system.

{{< figure
    src="https://media.rafliard.net/content/projects/automaticSprinkler/ASS-simpleTopology.webp"
    alt="Simplified Diagram Block Scheme"
    caption="Sistem Block Diagram "
    class="w-50"
    >}}

### System Concept

{{< figure
    src="https://media.rafliard.net/content/projects/automaticSprinkler/ASS-programFlowchart.webp"
    alt="Program's Flowchart"
    caption="Flowchart logic program"
    class="w-25"
    >}}

Program designed with automated operation without user intervention (user set alarm setpoint) however for the water pump actuation my relative want to retain manual activation as he deem he want to keep it simple at first. I use STElectronics' HAL to program the STM32

### Component Selection

Before we move further, I would like to address crucial component that determine the project viability

#### Moisture Sensor

Common Moisture sensor are suck, I don't think we would use _industrial_ grade sensor, and most available information online it is best to use capacitive based _sensor_ in which we read the capacitive value in the soil and we would process the sensor with 555 timer outputting frequency based data.

Moisture Sensor atau Sensor kelembapan tanah merupakan salah satu komponen terpenting dalam skema otomasi penyiraman karena untuk menentukan apakah tanah perlu disiram atau tidak kita menggunakan sensor kelembapan tanah ini. Masalah terbesar terutama untuk bekerja menggunakan sensor grade Hobbyist adalah keandalan sensor yang bervariasi baik yang sangat bagus dan akurat hingga sensor yang mudah rapuh sehingga bersifat _sekali pakai_. Hal tersebut kita temui pada jenis Sensor Kelembapan ini dengan banyak varian ditemukan di E-commerce Indonesia. Jika kita kelompokan, bisa kita bagi menjadi 4 jenis sensor kelembapan.

I recommend to check Andreas Spiess's video that discuss this moisture sensor topic to be able near-linear reading result.

{{< youtubeLite id="m0mcCtcViTY" label="[463] Why most Arduino Soil Moisture Sensors suck (incl. solution) - Andreas Spiess" >}}

### PCB design layout

{{< figure
    src="https://media.rafliard.net/content/projects/automaticSprinkler/ASS-schematicEletrics.webp"
    alt="Schematics and PCB Layout"
    caption="Schematics and PCB Layout"
    class="w-50"
    >}}

I designed both schematics and PCB layout using KiCAD. Most component connected using connector for easier plug n' play and minimize reversed connection. For module board power I use 5V adapter with DC barrel jack connector.

Design limited to single layer as I want to make it as fast as possible and replicable.

## Testing

<iframe class="max-w-prose mb-20" src="https://drive.google.com/file/d/1QeUXbqRyoAKniZ0qwAhQPWqXwc2yQIl5/preview" width="660" height="371" allow="autoplay" allowfullscreen></iframe>

## Gallery

{{< gallery >}}
  <img src="https://media.rafliard.net/content/projects/automaticSprinkler/gallery/ASS-Gallery7.webp" class="grid-w33 md:grid-w33 xl:grid-w25" />
  <img src="https://media.rafliard.net/content/projects/automaticSprinkler/gallery/ASS-Gallery1.webp" class="grid-w33 md:grid-w33 xl:grid-w25" />
  <img src="https://media.rafliard.net/content/projects/automaticSprinkler/gallery/ASS-Gallery2.webp" class="grid-w33 md:grid-w33 xl:grid-w25" />
  <img src="https://media.rafliard.net/content/projects/automaticSprinkler/gallery/ASS-Gallery3.webp" class="grid-w33 md:grid-w33 xl:grid-w25" />
  
  <img src="https://media.rafliard.net/content/projects/automaticSprinkler/gallery/ASS-Gallery4.webp" class="grid-w33 md:grid-w33 xl:grid-w33" />
  <img src="https://media.rafliard.net/content/projects/automaticSprinkler/gallery/ASS-Gallery6.webp" class="grid-w33 md:grid-w33 xl:grid-w33" />
  <img src="https://media.rafliard.net/content/projects/automaticSprinkler/gallery/ASS-Gallery5.webp" class="grid-w33 md:grid-w33 xl:grid-w33" />
{{< /gallery >}}