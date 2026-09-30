# 🔘 Philips Hue Tap Switch (Original 4-Button)

Controls actions for each of the 4 buttons on the **original kinetic Philips Hue Tap Switch** connected via the official Philips Hue bridge integration.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fepiech%2Fha-blueprints%2Fblob%2Fmain%2Fblueprints%2Fautomation%2Fhue%2Fphilips_hue_tap.yaml)

> [!NOTE]
> This blueprint is for the **original kinetic 4-button Hue Tap** (battery-free, EnOcean kinetic harvester, model `ZGPSWITCH` / `8718696743133`). It is **not** for the newer battery-powered Hue Tap Dial with rotary dial ring.

---

### 🎯 Features
- **Modern Device Registry Support**: Solves the issue where legacy blueprints stopped matching devices because the model identifier changed from `Hue tap switch (ZGPSWITCH)` to `Hue tap switch`. Supports both formats.
- **Dual Trigger Handling**: Uses both native device trigger IDs and event data subtype fallbacks for instant response.
- **Independent Actions**: Assign any sequence of service calls, scenes, toggles, or scripts to each button.
- **Restart Mode**: Handles rapid clicks without queuing errors.

---

🚀 How to Import
One-Click Import
[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fepiech%2Fha-blueprints%2Fblob%2Fmain%2Fblueprints%2Fautomation%2Fhue%2Fphilips_hue_tap.yaml)

Manual Import URL:

Method 2: Manual Import via URL
 1. In Home Assistant, navigate to Settings > Automations & Scenes > Blueprints.
 2. Click Import Blueprint (bottom right).
 3. Paste the following URL into the dialog:
text
https://github.com/epiech/ha-blueprints/blob/main/blueprints/automation/hue/philips_hue_tap.yaml
 4. Click Preview Blueprint, then click Import Blueprint.
---

❓ Troubleshooting & FAQ:

Why doesn't my switch appear in the device selector?
 1. Make sure your switch is paired through the official Philips Hue integration (via a Philips Hue Bridge). If paired via Zigbee2MQTT or ZHA, this blueprint does not apply.
 2. Confirm the device model in Home Assistant under Settings > Devices & Services > Philips Hue is listed as Hue tap switch or ZGPSWITCH.

Does this switch support long press or double click?
 - No. The original Philips Hue Tap switch is powered entirely by kinetic energy harvested from your physical click (no battery). Because the circuit only has power for a fraction of a second during the press, hardware long-press or hold states do not exist.
---

### 📐 Button Layout

```text
       ┌──────────────┐
       │      ●       │  <-- Button 1 (Large main surface / 1 dot)
       │  ●●     ●●●● │
       │     ●●●      │
       └──────────────┘
            ▲   ▲    ▲
            │   │    └── Button 4 (Bottom right / 4 dots)
            │   └─────── Button 3 (Bottom center / 3 dots)
            └─────────── Button 2 (Bottom left / 2 dots)
