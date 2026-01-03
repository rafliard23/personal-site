---
title: "EEPIS Versatile Cargo Aeroplane"
date: 2021-12-31T21:57:24+07:00
lastmod:
tags: [Electrics, Hardware]
categories: [Posts, Projects]
slug: evaro
thumbnailLink: "https://media.rafliard.net/content/projects/evaro/evaro_thumb.webp"
summary: "1st place awardee for Airframe Innovation - Techno Development in National Aeronautical Robot Competition (Kontes Robot Terbang Indonesia; KRTI) 2021. 3-motor Tilt rotor hybrid VTOL."
draft: false
excludeFromSearch: false
---

{{< figure
    src="https://media.rafliard.net/content/projects/evaro/evaro_thumb.webp"
    class="xl:grid-w66"
    >}}

This project took place when I was a student during my 2nd to 3rd year of college. It was UAV research to develop a Tri motor Hybrid UAV in detail with two of three motors capable tilting vertically and one motor fixed in vertical position, as result the UAV capable to take off and landing Vertically. The name of the developed prototype product is “EEPIS Versatile Cargo Aeroplane” (EVARO). This research development acts as internal research and entry for the National Aeronautical Robot Competition (Kontes Robot Terbang Indonesia abbreviated as KRTI) for the year 2021.

As a team, we are Dirgantara PENS team under EEPIS Flying Robot for Indonesia (EFRISA) flag, EFRISA compete in Techno Development category with sub team that each participates on each sub division competition. In Airframe Innovation sub team, we are five-person team with three being handler for several tasks and two person as a crew helping to complete the tasks. In this team, I am handled electrics and hardwares of UAV, for some occasion I also help mechanical maintenance and manufacture.


## Overview

{{< figure
    src="https://media.rafliard.net/content/projects/evaro/evaro_packaging.webp"
    alt="Packaging Kit"
    caption="Assembled UAV and its Packaging"
    class="xl:grid-w66"
    >}}

EEPIS Versatile Cargo Aeroplane (EVARO) is UAV that developed with logistic background. This UAV submission in the National Aeronautical Robot Competition 2021 on Techno Development category with Airframe Innovation sub division. In this category, scoring was determined by development that conducted on developed UAV for each entrant, for this sub division airplane configuration, system, and airframe component are the main inspected parts for scoring.

{{< figure
    src="https://media.rafliard.net/content/projects/evaro/evaro_summary_drawing.webp"
    alt=""
    caption="Blueprint of EVARO UAV"
    class="grid-w66 xl:grid-w66"
    >}}

Specification detail of UAV EVARO:
+ Configuration: Skyhunter Hybrid Tilt Rotor Hybrid
  + Classification: Hybrid VTOL
  + Tail: V-Tail
  + Propulsion: 3 Motor; 2 Motor Hybrid, dan 1 Fixed Vertical
+ Wingspan: 1400mm
+ Length: 970mm
+ Maximum Take off Weight (MTOW): 3200g
+ Maximum payload Weight: 500g
+ Material: Composite and PET

## Electrics Hardwares

Aside of usual UAV electrical hardwares, this development add a "Tilt rotor" which mount a motor into a servo motor arm so the motor orientation can be controlled in order to achieve hybrid configuration (Fixed Wing Aircraft and VTOL plane). During VTOL stage, all three motors used to propel the UAV into higher altitude, and as the UAV achieve enough altitude to transition into Cruise mode (Fixed Wing aircraft), the tilt rotor will rotates from facing upward to face forward to act as twin motor UAV with the fixed vertical motor shutdown during Cruise mode to save more energy during flight. Compared to Quad Plane configuration, this configuration save better energy as the motor count lower and most of flight going to have maximum of two motor turned on.

{{< figure
    src="https://media.rafliard.net/content/projects/evaro/evaro_tiltRotor.webp"
    alt="EVARO Tilt Rotor"
    caption="Utilization of Servo motor for Tilt rotor"
    >}}

To achieve this hybrid configuration, we use Gearboxed Servo in order to control motor during flight. We have tested 15kg gearbox is enough but for competition and research, we opted to use 35kg for safety factor. Tilt rotors mounted on each servo motor arm with motor heading facing same orientation as servo arm.

## Tilt Rotor Servo Drive

{{< figure
    src="https://media.rafliard.net/content/projects/evaro/evaro_wing_Drawing.webp"
    alt="EVARO Tilt Rotor"
    caption="Servo motor for tilting the motor"
    class="grid-w66 xl:grid-w66"
    >}}

With the way tilt steering works, the servo motor also controls the yaw movement during VTOL phase, the servos react accordingly based on gyroscope input and then balances the UAV. The servos during VTOL phase has angle travel limits for its up facing orientation with 15° limit tilting forward. During Cruise mode, the servos hold on the 0° angle to ensure maximum forward force. The mode selection controlled by Ground Control Station or if UAV is within Remote radius, can be switched using Remote Switch (according to assigned channels on Remote PPM/Transceiver).

Here's our publication as poster which is mandatory as part of Competition submission.

{{< figure
    src="https://media.rafliard.net/content/projects/evaro/evaro_poster.webp"
    alt="Poster Riset"
    caption="Research Poster for KRTI 2021 TDA"
    class="xl:grid-w66"
    >}}