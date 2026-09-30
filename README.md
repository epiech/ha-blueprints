# 🏠 Home Assistant Blueprints

A collection of tested, modern Home Assistant automation blueprints designed for reliability, clean UI selectors, and compatibility with current Home Assistant Core releases.

---

## 📋 Available Blueprints

| Blueprint | Supported Hardware | Integration | Import |
| :--- | :--- | :--- | :--- |
| **Philips Hue Tap (Original 4-Button)** | Model `ZGPSWITCH` / `8718696743133` | [Philips Hue](https://www.home-assistant.io/integrations/hue/) | [![Import to Home Assistant](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fepiech%2Fha-blueprints%2Fblob%2Fmain%2Fblueprints%2Fautomation%2Fphilips_hue_tap.yaml) |

---

## 🔘 Philips Hue Tap Switch (Original 4-Button)

Controls actions for each of the 4 buttons on the **original kinetic Philips Hue Tap Switch** connected via the official Philips Hue bridge integration.

> [!NOTE]
> This blueprint is for the **original kinetic 4-button Hue Tap** (battery-free, EnOcean kinetic harvester). It is **not** for the newer battery-powered Hue Tap Dial with rotary ring.



### 🎯 Features
- **Modern Device Registry Support**: Works with modern Home Assistant Core releases where the model identifier is `Hue tap switch` or `Hue tap switch (ZGPSWITCH)`.
- **Dual Trigger Handling**: Uses both native device trigger IDs and event data subtype fallbacks for instantaneous response.
- **Independent Actions**: Assign any sequence of service calls, scenes, toggles, or scripts to each button.
- **Restart Mode**: Handles rapid successive presses smoothly without queuing errors.

🚀 How to Import

Method 1: My Home Assistant (One-Click)
Click the badge below to open your Home Assistant instance and import automatically:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fepiech%2Fha-blueprints%2Fblob%2Fmain%2Fblueprints%2Fautomation%2Fphilips_hue_tap.yaml)

Method 2: Manual Import via URL
  1. In Home Assistant, navigate to Settings > Automations & Scenes > Blueprints.
  2. Click Import Blueprint (bottom right).
  3. Paste the following URL into the dialog:
https://github.com/epiech/ha-blueprints/blob/main/blueprints/automation/philips_hue_tap.yaml
  4. Click Preview Blueprint, then click Import Blueprint.


❓ Troubleshooting & FAQ

Why doesn't my switch appear in the device selector?
  1. Make sure your switch is paired through the official Philips Hue integration (via a Philips Hue Bridge). If paired via Zigbee2MQTT or ZHA, this blueprint does not apply.
  2. Confirm the device model in Home Assistant under Settings > Devices & Services > Philips Hue is listed as Hue tap switch or ZGPSWITCH.

Does this switch support long press or double click?
No. The original Philips Hue Tap switch is powered entirely by kinetic energy harvested from your physical press (no battery). Because the circuit only has power for a fraction of a second during the click, hardware long-press or hold states do not exist.


### 📐 Button Layout

```text
       ┌──────────────┐
       │      ●       │  <-- Button 1 (Large main surface / 1 dot)    │
       │  ●●     ●●●● │
       │     ●●●      │
       └──────────────┘
            ▲   ▲    ▲
            │   │    └── Button 4 (Bottom right / 4 dots)
            │   └─────── Button 3 (Bottom center / 3 dots)
            └─────────── Button 2 (Bottom left / 2 dots)

