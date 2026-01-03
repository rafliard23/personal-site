---
title: "Computer Vision in Amphibious UAV"
date: 2022-09-28T12:09:05+07:00
lastmod:
tags: [Computer Vision]
categories: [Posts, Projects]
slug:
thumbnailLink: "https://media.rafliard.net/content/projects/amfibiUAV/amfibiUAV_waterShoot.webp"
summary: "This project was one of my effort for project funding a research for our UAV team. We modified our EVARO UAV for amphibious terrain and mini PC system to retrieve video feed during flight and _process_ for simple human detection."
draft: false
excludeFromSearch: true
---

{{< figure
    src="https://media.rafliard.net/content/projects/amfibiUAV/amfibiUAV_waterShoot.webp"
    class="w-50"
    >}}

This project was one of my effort for project funding a research for our UAV team. We modified our EVARO UAV for amphibious terrain and mini PC system to retrieve video feed during flight and _process_ for simple human detection.

{{< button href="rafliard.net/projects/evaro/" target="_blank" >}} EVARO {{< /button >}}
{{< article link="/projects/evaro/" >}}

This project was part of accepted Student Creativity Programme (Program Kreativitas Mahasiswa | PKM) 2022. I have to implement computer vision using mini PC using Raspberry Pi 3B to detect disaster victim as part of research topic.

I opted to use YoloV3-tiny for my computer vision, by computation resource Pi 3B won't cut it alone therefore I had to use the C++ build and use small resolution input. For demonstration purpose we feed the video feed into the program and it will output the result with highlighted object of interest.

{{< github repo="pjreddie/darknet" >}}

Here provided simplified flowchart of the system:
{{< figure
    src="https://media.rafliard.net/content/projects/amfibiUAV/flowchartSystem.webp"
    alt="Diagram Sistem"
    caption="Simplified flowchart of the system"
    >}}

I provided several test results in form of video, due to time constraint and tight schedule, we only tests the UAV within university facility area.

Static Test:<iframe src="https://drive.google.com/file/d/1h1-m4DplsvcgpHVSnmM812SnqZ08IKCZ/preview" width="640" height="360" class="max-w-prose mb-20" allow="autoplay" allowfullscreen></iframe>
Horizontal Hover Test:<iframe src="https://drive.google.com/file/d/1j09x9fVix6wY8g5hmPhqTY33EhSPujMN/preview" width="640" height="360" class="max-w-prose mb-20" allow="autoplay" allowfullscreen></iframe>
Vertical Hover Test:<iframe src="https://drive.google.com/file/d/1yDpbiVFlFkXGyZKOs61JnQa8b50IFTAy/preview" width="640" height="360" class="max-w-prose mb-20" allow="autoplay" allowfullscreen></iframe>