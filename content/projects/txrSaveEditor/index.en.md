---
title: "Tokyo Xtreme Racer - Save Editor GUI"
date: 2025-05-12T17:29:36+07:00
lastmod: 2025-11-26T20:10:12+07:00
tags: [Software, Game Modding]
categories: [Posts, Projects]
slug:
thumbnailLink: "https://raw.githubusercontent.com/rafliard23/txr-use-py/refs/heads/main/img/txr_use-vehicle_upgrades.png"
summary: "Simple GUI Save Editor for Tokyo Xtreme Racer (2025) using uesave-cli and Python"
draft: false
excludeFromSearch: false
---

{{< gallery >}}
  <img src="https://raw.githubusercontent.com/rafliard23/txr-use-py/refs/heads/main/img/txr_use-vehicle_upgrades.png" class="md:grid-w33 xl:grid-w50"/>
{{< /gallery >}}

Last year somewhere in August 2024, we have unexpected announcement that Tokyo Xtreme Racer or in its native release _Shutokō Battle_ (首都高バトル) announced for new entry almost 10 years since last release in console! Fast forward to January 23rd We have Early Access launch which is awesome! As later people digging through the gamefiles it come clear that the game use Unreal Engine 5.

Thought because I liked this series far way back in PS2 era, I decided to maybe _give_ back small contribution to the community by making custom GUI app for save editing the game.

You can check my repo for the app itself

{{< github repo="rafliard23/txr-use-py" showThumbnail=false >}}

## It's a _wrapper_ app

{{< figure
    src="https://media.rafliard.net/content/projects/txrSaveEditor/txrSE_overview.webp"
    alt="Layer overview"
    caption="Tokyo Xtreme Racer Save Editor app layer overview"
    class="xl:grid-w50"
    >}}

First roadblock that came to me was Serial-Deserialize the save file. Unreal game are saved in a way that's packed by specific function. The save file structure are clear enough that you can edit it with hex editor however we would encounter byte collision if we add or remove additional bytes into the file, thus we would move in ready-to-use tool to save time not to mention this is my first UE5 game that I play! (well I don't want to spend time writing Ser-Des function myself).

There goes I found this fancy cli tool that enough for my use case. Serial and Deserialize the UE save file (`.sav`) into JSON document (`.json`) and vice versa.

{{< github repo="trumank/uesave-rs" showThumbnail=true >}}

By any means the cli tool alone is the save editor itself, however to make things easier for user we can add additional front end to edit what user want and convert it from the value into respective block of data that need to be edited then save it as .sav file once player hit "Save" or "Save As"

## How it works

### Loading File Process

{{< figure
    src="https://media.rafliard.net/content/projects/txrSaveEditor/txrSE_sav2json.webp"
    alt="Sav2JSON"
    caption="Loading save file deserialize into `.json` file"
    class="xl:grid-w75"
    >}}

First and foremost the Editor UI needs you to load a save file `.sav` which we will save the path for processing later on. This path will be piped to uesave-cli which converts the `.sav` into `.json` onto specified folder we set.

### Editing Data

{{< figure
    src="https://media.rafliard.net/content/projects/txrSaveEditor/txrSE_userEdit.webp"
    alt="User Edit runtime"
    caption="Open loop data editing overview"
    class="xl:grid-w75"
    >}}

Once we have our `.json` save file, we can edit it right away and adjust any value according to valid range and reasonable set. Almost any value related to player character can be edited that affect achievements however for in-game freeroam related check they may checked over `raceinfo` entry that loaded in `transient` or volatile in memory during gameplay. This save editor front end at best very basic as I don't want to expand the GUI to attribute larger customization (e.g plate modding, muffler swap and some tricky edits). Once we complete edit the value, we can write our changes into the `.json` file.

### Put it back as `.sav`

{{< figure
    src="https://media.rafliard.net/content/projects/txrSaveEditor/txrSE_json2sav.webp"
    alt="UJSON2Sav"
    caption="Saving `.json` file into save file"
    class="xl:grid-w75"
    >}}

This process handled by uesave-cli with help of GUI to retrieve our original path of `.sav` file and as conversion output path of uesave-cli.

## Remark
I believe the next logical step would be implement this editor as in-game Trainer to make things more streamlined and contained within the game. Although I have not start the process as a lot of things to do in real life, maybe somebody would make it before I complete it myself, who knows. All that matters is that I want to make something and share it in case someone find it useful though I find it limitating :p