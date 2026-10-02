<div align="center">
# 💡 Smart Room & Bathroom Lighting Automation
### Home Assistant Blueprint for Intelligent Multi-Sensor Occupancy, Privacy Mode & Granular Color Control
A comprehensive, production-ready Home Assistant automation blueprint designed for intelligent room and bathroom occupancy lighting. It supports **multiple motion/presence sensors**, **multiple door contact sensors**, **privacy/shower auto-off prevention**, and **granular lighting control** (brightness, Kelvin color temperature, and RGB color) across daytime and night mode schedules.
[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fepiech%2Fha-blueprints%2Fblob%2Fmain%2Fblueprints%2Fautomation%2Fsmart_bathroom_occupancy_lighting.yaml)
[![Home Assistant Version](https://img.shields.io/badge/Home%20Assistant-2024.6.0%2B-blue.svg?style=flat-square&logo=home-assistant)](https://www.home-assistant.io)
[![Blueprint Type](https://img.shields.io/badge/Type-Automation%20Blueprint-orange.svg?style=flat-square&logo=yaml)](https://www.home-assistant.io/docs/blueprint/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)
<p align="center">
  <b>Multi-Motion Sync</b> • <b>Multi-Door Occupancy</b> • <b>Shower/Privacy Protection</b> • <b>Kelvin / RGB / Brightness</b> • <b>Day & Night Schedules</b>
</p>
---
## 🌟 Key Features
</div>
* **Multi-Motion Sensor Synchronization**: Add 1, 2, or more motion/presence sensors. Vacancy timers synchronize across all sensors so lights will not turn off prematurely if one sensor clears while another still detected recent motion.
* **Multi-Door Detection & Bathroom Privacy Protection**:
  * Opening any door triggers occupancy immediately (often before motion sensors catch you entering).
  * **Privacy / Shower Mode**: Configurable door check prevents lights from auto-turning off while all doors are closed (ideal when taking a shower, bath, or using the restroom).
* **Granular Light Controls**:
  * Set brightness (1–100%).
  * Select your color mode: **Color Temperature (Kelvin)**, **RGB Color**, or **Default/Don't Change Color**.
  * Dedicated sliders for Kelvin (2000K–6500K) and color pickers for RGB.
* **Day vs. Night Schedules**:
  * **Daytime Mode**: Triggered during daytime hours when an optional Night Mode helper is off, with optional sun elevation check (`above_horizon`) and ambient illuminance threshold check (Lux).
  * **Night Mode**: Triggered via an `input_boolean` helper (e.g., Bedtime / Goodnight) or a set time window (e.g., 10:00 PM – 6:00 AM).
* **Flexible Light Targets**:
  * **Main Targets**: Group of lights to control during the day.
  * **Night Target (Optional)**: Specific nightlight (e.g. WLED toe-kick strip) for night mode.
  * **Additional Off Lights (Optional)**: Automatically turn off extra lights on vacancy (e.g., vanity mirror lights that someone may have manually toggled).
* **Bypass & Kill Switches**:
  * **Bath Mode / Keep-On Bypass**: Helper entity to lock lights on.
  * **Automation Kill Switch**: Master toggle to suppress the automation entirely.
## 📖 Overview
Standard motion light automations often suffer from common frustrations:
- Lights turning off while you are in the shower or using the bathroom because you are sitting still.
- Lack of support for multiple motion sensors covering different angles or zones.
- Rigid color settings that don't differentiate between day and night.
