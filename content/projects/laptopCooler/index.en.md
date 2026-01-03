---
title: "Laptop Cooler"
date: 2023-01-28T12:40:11+07:00
lastmod:
tags: [Electrics, Mechanics, Analog System]
categories: [Posts, Projects]
slug: laptop_cooler
thumbnailLink: "https://media.rafliard.net/content/projects/laptopCooler/img-inv2.webp"
summary: "Custom cooling solution for 13\" - 15.6\" Laptops utilizing 3D printed parts, PC case fans, and custom analog fan speed controller utilizing 555 timer."
draft: false
excludeFromSearch: true
---

If we want to squeeze every drops of performance out of your laptop device, you will need to cool them. As proven by a lot of testing, better cooling can improve thermal performance (lessen chance of thermal throttling) and definitely will improve your laptop performance! Although on this case we need to reality check some stuff like our laptop internal cooling performance (e.g thermal paste age, heatsink design and such) and external factor not limited but including ambience thermal, how much of vent within your laptop case, how do you place your laptop when you using it. As much to discuss, we can categorise them as Internal and External factors that affect our laptop thermal performance.

## Internal Factor of Thermal Performance

In this category are contained within the laptop model itself, like laptop design, how much of vent holes on our laptop case, cooling system configuration (heatsink), boosting algorithm (Intel PL, and AMD PBO) of CPU, the age of applied thermal paste, and the age of the laptop itself.

Some of these internal factors can be tweaked by user, such as dremeling (cut some holes) on your laptop (Don't do this unless you're out of Warranty or being older ASUS TUF FX504/505 User), limiting Boost TDP using throttlestop, undervolting, regularly change thermal paste (annual change is enough for intense use atleast for me), and some extreme measure sometime is to disable CPU boosting altogether.

## External Factor of Thermal Performance

External factors are those outside of our own laptop condition, like your work environment temperature, laptop placement, and external cooling device.

For such external cooling device, I'd say two most eficient method is either using Laptop Stand that lifts your laptop underside so it can get better airflow, and then forced cooling device like adding some fans or cooling pad on your laptop.

As Jarrod's Tech video suggest that a simple laptop stand should be sufficient to provide airflow into a laptop

{{< youtubeLite id="tXvKiy65pwg" >}}

## Laptop Stand

{{< figure
    src="https://media.rafliard.net/content/projects/laptopCooler/laptopStand-mediatech.webp"
    alt="Laptop Stand Mediatech"
    caption="One of Laptop Stand model that sold in Indonesia"
    class="grid-w60 xl:grid-w40"
    >}}

Laptop Stand is one of those device that mostly used to "lift" your laptop to provide better viewing and ergonomic. Although some Laptop Stand may not work as (passive) cooling device due to some of them may block your laptop inlet vent.

## Laptop Cooler

{{< figure
    src="https://media.rafliard.net/content/projects/laptopCooler/laptopCooler-notepal-x3.webp"
    alt="Laptop Cooler Coolermaster"
    caption="Notepal X3 from Coolermaster"
    class="grid-w60 xl:grid-w40"
    >}}

Laptop Cooler solely used to cool laptop and usually they're powered using USB Input (so you're going limited with 5V voltage or maybe some of them had boost converter though it will limit the current).

Laptop Coolers have various performance as some of them either simply bad (especially if you get those knock off products), or those that capable to cool up to 20° degree difference. 

## Design Planning

The goal for this project is that I want something that capable as laptop stand and also can be mounted with fans to act like laptop cooler. Since I want to keep compatibility with most of common fans, I will use 12V voltage level. For sake of simplicity and avoid overkill solution, Analog control should be enough with 555 Timer to output "PWM" Signal that drive the gate of Mosfet to control the output Voltage level (as later on I use those 3PIN fan that the 3rd pin is tachometer output of fan).

From Mechanical standpoint, I designed this one to capable to hold 13.3" to 15.6" Laptop and can be configured either as Standalone (no pun intended) Laptop Stand or being Laptop Cooler with 2x120mm fan attached on its mounting point. Another consideration is the main feature of the Laptop Stand part is that the design is 3D Printable. The design must fit the most common printer on here (Mostly people use Ender 3 here).

Electronics portion, I designed custom PCB to handle the speed control and accept 3PIN fan connector to be controlled with 555 Timer.

### Mechanical Design

I designed the part as simple as it could but also to consider structural strength and practical side. The design should be printable with Ender 3 bed size and bigger. My parts printed using SUNLU PLA filament and as of October 2023, the laptop stand part still strong and usable.

{{< figure
    src="https://media.rafliard.net/content/projects/laptopCooler/img-inv3.webp"
    alt="Desain Laptop Stand DIY"
    caption="Laptop Stand Design"
    class="grid-w70 xl:grid-w50"
    >}}

To mount fans, we need to add some part using acrylic 2mm/3mm to mount them into Stand part.

{{< figure
    src="https://media.rafliard.net/content/projects/laptopCooler/img-inv2.webp"
    alt="Fan Bracket Fitting"
    caption="Laptop Stand design fitted with 2x120mm Fans"
    class="grid-w70 xl:grid-w50"
    >}}

### Electrics Design

Since I rely on "simple" control and doesn't need fancy microcontroller, I resorted to 555 Timer with good ol' NE555 IC. As we can power them with 12VDC, we don't need DC-DC converter and we can just power it using 12VDC input from barrel jack input. As 3PIN Fan design doesn't have any mean of speed control, we have to control them via V_OUT voltage level control by sending V_OUT in form of PWM output. This PWM Output will regulate voltage output based on our input using Potentiometer of our 555 System. For MOSFET part, I decided to use generic NPN IRFZ44N mosfet as it does the job very well and doesn't seem to overloaded from the task.

{{< figure
    src="https://media.rafliard.net/content/projects/laptopCooler/img-kicad-sch1.webp"
    alt="Skematik Rangkaian KiCAD"
    caption="Fan Speed Control Schematics"
    class="grid-w70 xl:grid-w50"
    >}}

{{< figure
    src="https://media.rafliard.net/content/projects/laptopCooler/img-kicad-pcb1.webp"
    alt="Layout Trace PCB"
    caption="PCB Layout of Speed Controller"
    class="grid-w70 xl:grid-w50"
    >}}

You can visit my github repository for more information about the PCB, I made it using KiCAD 6:

{{< github repo="rafliard23/laptopCooler-hardware" showThumbnail=false >}}

{{< figure
    src="https://media.rafliard.net/content/projects/laptopCooler/img-board1.webp"
    alt="Assembled PCB"
    caption="Assembled PCB"
    class="grid-w70 xl:grid-w50"
    >}}

### Test Usage

I've only tested this Stand and Cooler with my laptop ASUS TUF FX505GD (i5 8300H and GTX 1050). This laptop has stock under case (no drilling mod applied) at the time of testing take place, the thermal paste age ~9 months since last paste, modified PL boost TDP, and ambient temperature above 30° C (yep, living on tropical side of world is hot plus on low land area).

To measure internal temperature, I relies HWiNFO to monitor CPU, and GPU core temp. I only tested it with syntethic benchmark, on average temperature can be reduced 10-15° from 80°C max. For power usage of fan cooler, I can say it does pretty good job with theoritical 3.84W or around 4W for entire system as my 2x120mm has 0.16A rating each on max speed, this cooler can be powered with 12V1A adapter although you can have as much as you want if you going to fit a Delta fan 120mm 12VDC (for that extra airflow and localised Airplane jet sound).

## Summary

Laptop Stand or Cooler is one of the method that you can use to extracts more power out of your system. Though we need to take note other factor in whole system as adding a cooler wouldn't bring your system to cool as much if your laptop fan clogged by dust or your thermal paste dried out. Periodical maintenance also helps your laptop temperature and definitely laptop longetivity.

Reference(s):  
https://www.build-electronic-circuits.com/555-pwm-circuit/  
https://www.electronics-tutorials.ws/waveforms/555_timer.html