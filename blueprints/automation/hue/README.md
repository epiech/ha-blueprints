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
