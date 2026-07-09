# Parking

A vehicle parking system for FiveM (ESX). Park your vehicles at designated parking lots around the city and retrieve them later from a kiosk — with persistent storage, so parked vehicles survive server restarts.

## Features

- 🅿️ **Park & retrieve vehicles** at designated parking lots (Legion Square Garage and Pillbox Hill Lot included by default — easy to add more)
- 💾 **Persistent storage** — parked vehicles are saved to the database with their full properties (mods, livery, plate, etc.)
- 🖥️ **Web UI kiosk** built with TypeScript for browsing and retrieving your parked vehicles
- 💰 **Configurable retrieval fee** charged from the player's bank account (free by default)
- 🔒 **Per-player vehicle limit** (default: 8 parked vehicles)
- 🚫 **Bicycle blocking** and anti-spam cooldowns on park/retrieve
- 🗺️ **Marker-based interaction** with distance-optimized rendering for good performance
- 🌐 **Locale support** — all messages are translatable

## Dependencies

- [es_extended (ESX)](https://github.com/esx-framework/esx_core)
- [oxmysql](https://github.com/overextended/oxmysql)
- [ox_lib](https://github.com/overextended/ox_lib)

## Installation

1. Download or clone this repository into your server's `resources` folder:
   ```
   git clone https://github.com/deadheartblood/Parking.git parking
   ```
2. Import `sql/install.sql` into your database.
3. Add the resource to your `server.cfg` (after its dependencies):
   ```cfg
   ensure ox_lib
   ensure oxmysql
   ensure es_extended
   ensure parking
   ```
4. Restart your server.

## Configuration

All settings live in `config.lua`. Highlights:

| Setting | Default | Description |
|---|---|---|
| Retrieval fee | `0` | Cost to take a vehicle out of parking |
| Account | `bank` | Which account the fee is charged from |
| Max parked vehicles | `8` | Per-player parking limit |
| Interaction key | `38` (E) | Key to interact with zones/kiosks |
| Marker draw distance | `35` | How far away markers render |
| Locale | `en` | Language for all messages |

Parking lots are defined in the config as well — each lot has a parking zone, a kiosk, and vehicle spawn points, so you can add your own locations by copying an existing entry.

## Usage

1. Drive your vehicle into a parking zone marker and press **E** to park it.
2. Walk up to the lot's kiosk and press **E** to open the parking menu.
3. Select your vehicle to retrieve it — it spawns at a free spawn point with all its mods intact.

## Project Structure

```
├── client/        # Client-side logic (markers, interaction, vehicle spawning)
├── server/        # Server-side logic (database, payments, validation)
├── shared/        # Locale / shared code
├── sql/           # Database schema (install.sql)
├── web/           # Kiosk web UI (TypeScript)
├── config.lua     # All configuration
└── fxmanifest.lua
```

## Credits

Made by **deadheartblood**.
