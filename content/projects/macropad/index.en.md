---
title: "Macropad RFR16E"
date: 2021-12-12T09:52:11+07:00
lastmod:
tags: [Mechanics, Electrics, Embedded System]
categories: [Projects]
slug: macropad_rfr16e
thumbnailLink: "https://drive.google.com/uc?export=view&id=1aU8lCN9cHqO3-I4rmVjUX_ktRh9ds7jH"
draft: false
---

For those who into Mechanical Keyboard hobby definitely know a Macropad. Macropad is a keyboard albeit mostly smaller in layout, that have a programmable keys function. These keys can hold a pre-programmed action that can be configured to act for example zooming in or out screen, saving or open specific files on a program, mute a mic, changing screen source for obs and such.

{{< figure
    src="https://onedrive.live.com/embed?resid=D52476BDF402A474%21184&authkey=%21AJTV91sxJNQqKsc&width=640&height=480"
    alt="Macropad Adafruit"
    caption="DIY kit Macropad made by [Adafruit](https://learn.adafruit.com/adafruit-macropad-rp2040/featured_products)"
    >}}

## Background

My reason to make this project is that I want to build my own programmable Macropad with open source firmware that can improve my workflow for certain task, also this project submitted as an assignment during my College Class on embedded system.

## System Design

Due to the macropad also used as assignment submission, I have time constraint to work on this piece and use whatever I have on that moment, this macropad use STM32 as its controller and this macropad had 16 keys layout with alternae layout 15 keys and 1 encoder.

### Controller Selection

Due to time constraint added from assignment submission, whatever USB HID capable controller that I had at that moment. So I used this WeAct Blackpill F401CCU6 board and this choice going to bring us trouble later on...


{{< figure
    src="https://onedrive.live.com/embed?resid=D52476BDF402A474%21186&authkey=%21AGUHliaIdTgNxXg&width=660"
    alt="WeAct F401 Blackpill"
    caption="WeAct \"Blackpill\" F401CCU6. [Sumber](https://stm32-base.org/boards/STM32F411CEU6-WeAct-Black-Pill-V2.0)"
    >}}

### Board Design

{{< figure
    src="https://raw.githubusercontent.com/rafliard23/rfr16e-hardware/main/img/schematic.jpg"
    alt="Skematik Rangkaian Macropad"
    caption="Schematics of RFR16E Macropad"
    >}}

{{< figure
    src="https://raw.githubusercontent.com/rafliard23/rfr16e-hardware/main/img/board.jpg"
    alt="Single Layer PCB"
    caption="PCB Design of RFR16E Macropad"
    >}}

PCB is a must to make this Macropad looks neater and to reduce messy cable if you're bad at cable management, I made a single layer PCB as I thought it was enough and does so cheap! This board can be configured either 16 Keys or 15 Keys with 1 Encoder (and working switch). Encoder addition helps for some stuff like adjusting volume, zoom level control. Zener diode (or simply you can just use any diodes) is a must to prevent ghosting effect

{{< figure
    src="https://onedrive.live.com/embed?resid=D52476BDF402A474%21185&authkey=%21AKQjwYAvmJfC7RU&width=660"
    alt="Dioda 1N4148"
    caption="This a cent component can improve your keyboard by mile! [Sumber](https://golem.hu/guide/diodes/)"
    >}}

No LEDs because at that time I have a doubt to drive LEDs circuit using QMK, so yeah no RGB party.

For further information regarding the hardware parts, you can check on this repo below:

{{< github repo="rafliard23/rfr16e-hardware" >}}

### Firmware Programming

{{< figure
    src="https://onedrive.live.com/embed?resid=D52476BDF402A474%21189&authkey=%21ALvkwRColdlGXjc&width=480"
    alt="QMK FM"
    caption="QMK firmware. [Sumber](https://qmk.fm/)"
    >}}

For firmware, we definitely use QMK as it is the most supported open source with wide range of hardware compatibility. I made 4 layers of keymap including Adobe Premiere keymap (to aid me when I use Premiere app), OBS for recording/online meet, generic Numpad, and debugging layer.

Remember a mention of trouble on previous section? This WeAct Blackpill board has a proprietary bootloader and if you're going to enter STM32 Bootloader by normal mean, you simply going to be greeted with WeAct bootloader instead of actual STM32 Bootloader. After some hours of searching on answer, you can bypass this proprietary bootloader by jumping some pins to ground. Unfortunately I didn't manage to document this step :/

{{< figure
    src="https://onedrive.live.com/embed?resid=D52476BDF402A474%21187&authkey=%21AMdtNCIpzNJF-F4&width=1024"
    alt="WeAct Bootloader"
    caption="It seems everyone annoyed by this bootloader too..."
    >}}

If you already got STM32 Bootloader popped on your device manager (Windows 10), or `lsusb`, you can then proceed to program your board with your own firmware.

You can also check the firmware that I've made for this macropad on this repository below:

{{< github repo="rafliard23/rfr16e" >}}

### Case Design

For case, I created mine on Inventor Pro and printed it using 3D Print with PLA filament. You can check my Case design on my [Grabcad](https://grabcad.com/library/macropad-rfr16e-1) post there.

{{< figure
    src="https://d2t1xqejof9utc.cloudfront.net/screenshots/pics/1cb96cf16ef20a944f6b2a06f5b082ee/original.jpg"
    alt="Case RFR16E"
    caption="The Case"
    >}}

## Summary

This project is fun to do although due to WeAct board some hours wasted just to seek an answer. Another personal note is that I want to build another macropad or maybe a full layout keyboard with other controller such as RP2040 because it is available on local market here and QMK supported them recently in 2023.