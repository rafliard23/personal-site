---
title: "Electronic Boiler with IoT Control"
date: 2024-05-28T07:45:41+07:00
lastmod:
tags: [Automation, Electrics, Mechanics, Embedded Systems]
categories: [Posts, Projects]
slug: e_boiler
thumbnailLink: "https://media.rafliard.net/content/projects/eBoiler/IoTBoiler-plant.webp"
summary: "Project based of very old client request. Electronic Boiler prototype equipped with Online and Offline control alongside data monitoring."
draft: false
excludeFromSearch: true
---

In December 2023, I completed this project to create IoT Control prototype for Boiler using Blynk IoT as middleware of control and status monitor. I designed the hardware/electrical system which combine several modules and smaller components. In short, the boiler was a cylindrical tank with heater element in it connected with solid state relay to control its heating using PID control and the main controller use ESP32 with proper isolation between low power and high power section of the device. We use type-K thermocouple for thermal reading of the tank and then this information feed into ESP32. 

## Background

This project was part of my freelance work that one of my client wanted a simple prototype of IoT control for oil boiler development in downsized scale. Here simplified system diagram.

{{< figure
    src="https://media.rafliard.net/content/projects/eBoiler/IoTBoiler-blockDiagramSystem.webp"
    alt="Simplified Diagram Block Scheme"
    caption="System Diagram"
    class="w-75 xl:grid-w50"
    >}}

## Role

This project is 2 man work, a friend interested with side project so I offered this one to assist me in few things. 70% of project effort done in my side, the rest is on my friend side. My role are following:
+ Project Management
+ Design and Build the system
+ Co-develop the PCB and controller program concept for ESP32

## PCB Design and System

System encased in panel box with every electronics (except the boiler part of course). Panel box door used as offline interface for operator.

### Parts within Panel Box

{{< figure
    src="https://media.rafliard.net/content/projects/eBoiler/IoTBoiler-mockUpPanel.webp"
    alt="Panel Mock Up"
    caption="Mock Up Panel Box"
    >}}

On the panel door, we have 4x4 keypad as input, 20x4 LCD as display, power switch, and pilot lamp for system status. Due to its internet-connected system, the system parameters are synced between Blynk component and offline setting, any changes will be reflected in offline and online.

{{< figure
    src="https://media.rafliard.net/content/projects/eBoiler/IoTBoiler-peletakanKomponen.webp"
    alt="Component Layout Box Panel"
    caption="Component within Box Panel"
    class="w-50"
    >}}

### Wiring Scheme and Controller

{{< figure
    src="https://media.rafliard.net/content/projects/eBoiler/IoTBoiler-schematic.webp"
    alt="Controller and overall Wiring Scheme"
    caption="Schematic Wiring"
    class="w-75 xl:grid-w50"
    >}}

For easier plug-n'-play application, PCB is hard requirement and luckily our application does not require precise sub 0.2mm trace PCB which we can easily create at home. We leverage JST connector and terminal to minimize user error from client side.

{{< figure
    src="https://media.rafliard.net/content/projects/eBoiler/IoTBoiler-PCB-3DView.webp"
    alt="PCB Design of Controller Portion"
    caption="PCB design and fabricated PCB"
    class="xl:grid-w50"
    >}}

### _Mini_ Boiler

{{< gallery >}}
  <img src="https://media.rafliard.net/content/projects/eBoiler/IoTBoiler-boiler.webp" class="grid-w25 md:grid-w25 xl:grid-w25" />
  <img src="https://media.rafliard.net/content/projects/eBoiler/IoTBoiler-heaterSensor.webp" class="grid-w50 xl:grid-w50" />
{{< /gallery >}}

For prototype and as client request, we use smaller tank for easier mobility and smaller space footprint. Tank equipped with thermocouple and 800W heater, heater connected into solid state relay to be controlled with ESP32 and thermocouple feed the thermal data.

### GUI

For GUI we use Blynk IoT due to client's hard requirement. Blynk used for status monitor and control.

{{< figure
    src="https://media.rafliard.net/content/projects/eBoiler/IoTBoiler-GUI.webp"
    alt="GUI Component"
    caption="GUI Blynk IoT"
    class="w-80"
    >}}