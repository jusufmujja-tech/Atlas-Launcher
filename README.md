<div align="center">

# 🛰️ Atlas Launcher

**A modern, open Minecraft: Java Edition launcher with first-class Fabric support.**

Resolve · Download · Inject · Launch — a deterministic, transparent launch pipeline.

[![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-2dd4bf)](#)
[![Built with Tauri](https://img.shields.io/badge/built%20with-Tauri%202-6f8cff)](https://tauri.app)
[![Minecraft](https://img.shields.io/badge/Minecraft-Java%20Edition-4be38f)](#)
[![License](https://img.shields.io/badge/license-MIT-9aa0b2)](#license)

</div>

---

## What is Atlas Launcher?

Atlas Launcher is a lightweight desktop application that lets players **install and start Minecraft: Java Edition** with their own Microsoft account. It manages game versions, Java runtimes, memory allocation and the [Fabric](https://fabricmc.net) mod loader, and can launch the game with the optional **Atlas Client** (a Fabric mod) and other user mods.

It is built with **Tauri (Rust + React/TypeScript)** for a small, fast, native footprint, and runs on Windows, macOS and Linux.

## Why Microsoft sign-in?

Atlas Launcher uses **Microsoft / Xbox Live authentication (`XboxLive.signin`)** for one purpose: to let a player sign in with **their own Microsoft account** and obtain **their own Minecraft session** so the game can be launched and played online, exactly like the official launcher.

- The user authenticates through the standard **Microsoft device-code OAuth flow** (no password ever touches the launcher).
- The resulting Minecraft access token and profile are used **only** to start the player's own game instance.
- Tokens are **not stored on any server, transmitted to third parties, or used for any purpose other than launching the user's own game.**
- Players who do not wish to sign in can use **offline mode**.

## Features

- 🔐 **Microsoft account login** (device-code flow) + offline mode fallback
- 🗂️ **Profiles** — per-profile Minecraft version, RAM, Java path and mod settings
- ☕ **Java auto-detection**
- 🧩 **Fabric loader** integration with automatic Fabric API resolution
- 📦 **Deterministic launch pipeline** with integrity-checked downloads (SHA-1) — *resolve → download → inject → launch*
- 🎮 **Modern launcher UI** with live progress and a polished launch experience

## How it works

```
Profile (UI)
   └─► LaunchConfig
          ├─ resolve   · Mojang version manifest (integrity verified)
          ├─ download  · libraries, assets, client — SHA-1 validated
          ├─ inject    · Fabric loader + Fabric API + mods
          └─ launch    · spawn the real Minecraft process
```

## Tech stack

| Layer | Technology |
|-------|------------|
| Desktop shell | Tauri 2 |
| Backend / launch engine | Rust |
| UI | React + TypeScript |
| Game | Minecraft: Java Edition + Fabric |

## Building from source

```bash
# Requirements: Rust, Node.js, and the platform WebView deps for Tauri
npm install
npm run tauri dev      # development
npm run tauri build    # production build
```

## Privacy

Atlas Launcher is a **local desktop application**. Authentication happens directly between the user's machine and Microsoft's official endpoints. The launcher has **no backend server**, collects **no analytics**, and **never** transmits user credentials or tokens anywhere except Microsoft's and Mojang's official APIs for the sole purpose of launching the user's own game.

## License

MIT © Atlas Launcher contributors
