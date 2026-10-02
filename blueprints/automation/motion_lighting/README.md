<div align="center">

  <h1>💡 Smart Room & Bathroom Lighting Automation</h1>
  <h3>Home Assistant Blueprint for Intelligent Multi-Sensor Occupancy, Privacy Mode & Granular Color Control</h3>

  <p>
    A comprehensive, production-ready Home Assistant automation blueprint designed for intelligent room and bathroom occupancy lighting. It supports <b>multiple motion/presence sensors</b>, <b>multiple door contact sensors</b>, <b>privacy/shower auto-off prevention</b>, and <b>granular lighting control</b> (brightness, Kelvin color temperature, and RGB color) across daytime and night mode schedules.
  </p>

  <p>
    <a href="https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fepiech%2Fha-blueprints%2Fblob%2Fmain%2Fblueprints%2Fautomation%2Fsmart_bathroom_occupancy_lighting.yaml">
      <img src="https://my.home-assistant.io/badges/blueprint_import.svg" alt="Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled." />
    </a>
  </p>

  <p>
    <a href="https://www.home-assistant.io"><img src="https://img.shields.io/badge/Home%20Assistant-2024.6.0%2B-blue.svg?style=flat-square&logo=home-assistant" alt="Home Assistant Version" /></a>
    <a href="https://www.home-assistant.io/docs/blueprint/"><img src="https://img.shields.io/badge/Type-Automation%20Blueprint-orange.svg?style=flat-square&logo=yaml" alt="Blueprint Type" /></a>
    <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square" alt="License: MIT" /></a>
  </p>

  <p>
    <b>Multi-Motion Sync</b> • <b>Multi-Door Occupancy</b> • <b>Shower/Privacy Protection</b> • <b>Kelvin / RGB / Brightness</b> • <b>Day & Night Schedules</b>
  </p>

</div>

---

## 📖 Overview

Standard motion light automations often suffer from common frustrations:
- Lights turning off while you are in the shower or using the bathroom because you are sitting still.
- Lack of support for multiple motion sensors covering different angles or zones.
- Rigid color settings that don't differentiate between day and night.
- Premature shutoff when one motion sensor resets before another.

This blueprint solves all of these challenges in a single, robust automation. It connects **multiple motion/presence sensors** and **multiple door contact sensors** with built-in **bathroom privacy protection**, **sun/illuminance gating**, and **granular color control** (brightness %, color temperature in Kelvin, or RGB color).

---

## 🌟 Key Features

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
