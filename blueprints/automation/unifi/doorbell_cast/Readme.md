# 🔘 Automatically streams the live camera feed from your UniFi Doorbell to Google Nest Hubs or Chromecast screens when someone rings the doorbell, and automatically stops after a set duration.

Controls actions for each of the 4 buttons on the **original kinetic Philips Hue Tap Switch** connected via the official Philips Hue bridge integration.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fepiech%2Fha-blueprints%2Fblob%2Fmain%2Fblueprints%2Fautomation%2Funifi%2Fdoorbell_cast%2Funifi_protect_doorbell_cast.yaml)


> [!NOTE]
> This blueprint is for the **G4 Doorbell Pro (POE)** It is **not** for the newer G6 Entry.

---

### 🎯 Features
- **Dual Trigger Support: Works with either the Last Doorbell Ring timestamp sensor or the doorbell binary_sensor.
- **Smart Restart: If pressed again while streaming, the timer resets so the video feed doesn't cut off prematurely.
- **Auto-Stop: Automatically stops the stream after the configured duration (default: 90 seconds).
- **Nighttime Shield: Ignores unavailable and unknown state transitions so Nest Hub screens don't wake up during overnight Home Assistant updates.
- **Multi-Device: Stream to one or multiple Google Nest Hubs or Chromecast screens simultaneously.

---

🚀 How to Import

Method 1: My Home Assistant (One-Click)
Click the badge below to open your Home Assistant instance and import automatically:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fepiech%2Fha-blueprints%2Fblob%2Fmain%2Fblueprints%2Fautomation%2Funifi%2Fdoorbell_cast%2Funifi_protect_doorbell_cast.yaml)


Method 2: Manual Import via URL
 1. In Home Assistant, navigate to Settings > Automations & Scenes > Blueprints.
 2. Click Import Blueprint (bottom right).
 3. Paste the following URL into the dialog:  https://github.com/epiech/ha-blueprints/blob/main/blueprints/automation/unifi/doorbell_cast/unifi_protect_doorbell_cast.yaml
 4. Click Preview Blueprint, then click Import Blueprint.
---

❓ Troubleshooting & FAQ:


