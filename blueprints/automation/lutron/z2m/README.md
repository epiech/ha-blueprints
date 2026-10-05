# 💡 Zigbee2MQTT: Lutron Connected Bulb Remote (LZL-4B)

Automate your Lutron Connected Bulb Remote (LZL-4B / LZL4BWHL01) directly through Zigbee2MQTT, mapping all 4 buttons and release events to any Home Assistant action.

> [!WARNING]
> **Not for Caséta**: This blueprint is strictly for the Zigbee-based Connected Bulb Remote (LZL-4B-WH-L01), not the proprietary Lutron Caséta Pico remotes, which require the Lutron Smart Bridge.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fepiech%2Fha-blueprints%2Fblob%2Fmain%2Fblueprints%2Fautomation%2Flutron%2Fz2m_lutron_connected_bulb_remote_%28lzl-4b%29%2Flzl4b_z2m_blueprint.yaml)

> [!NOTE]
> This blueprint requires Zigbee2MQTT and relies on the automatically generated MQTT device `action` sensor entity. Ensure your remote is successfully paired and reporting actions to Z2M before using this blueprint.

---

### 🎯 Features

- **Full Button Mapping**: Map the Top, Up, Down, and Bottom buttons to absolutely any Home Assistant action.
- **Universal Action Support**: You are not limited to lights! Run any sequence of actions on button presses, including calling scripts, toggling fans, locking doors, setting scenes, running conditionals, or sending notifications.
- **Hold & Release Support**: Binds the `brightness_stop` event when you release the Up or Down buttons, allowing you to create smooth dimming transitions or stop long-running scripts.
- **Hub-Free Zigbee Integration**: Leverages Zigbee2MQTT to integrate directly with Home Assistant without requiring the Lutron Caséta Smart Bridge.

---

### 🚀 How to Import

#### Method 1: My Home Assistant (One-Click)
Click the badge below to import directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fepiech%2Fha-blueprints%2Fblob%2Fmain%2Fblueprints%2Fautomation%2Flutron%2Fz2m_lutron_connected_bulb_remote_%28lzl-4b%29%2Flzl4b_z2m_blueprint.yaml)

#### Method 2: Manual Import via URL
1. In Home Assistant, navigate to **Settings** > **Automations & Scenes** > **Blueprints**.
2. Click **Import Blueprint** (bottom right).
3. Paste the blueprint URL into the dialog:
```text
https://github.com/epiech/ha-blueprints/blob/main/blueprints/automation/lutron/z2m_lutron_connected_bulb_remote_(lzl-4b)/lzl4b_z2m_blueprint.yaml
```
4. Click Preview Blueprint, then click Import Blueprint.

---

### ❓ Troubleshooting & FAQ

1. **Which entity should I select for the Remote Action Sensor?**
   - You need to select the `action` sensor entity exposed by Zigbee2MQTT for this remote. It is typically named something like `sensor.living_room_remote_action`. Ensure you are not selecting the battery or linkquality sensor.

2. **Why are button presses not triggering my automation?**
   - Ensure the remote is fully paired with your Zigbee coordinator. You can verify this by going to **Developer Tools** > **States** and checking if the state of your `sensor.<your_remote>_action` changes (e.g., to `on`, `off`, `brightness_step_up`) when you press the buttons.

3. **How do I configure smooth dimming?**
   - Zigbee2MQTT emits `brightness_step_up` or `brightness_step_down` when holding the buttons, and `brightness_stop` when released. You can use the **Button Release (Stop Dimming)** action block in this blueprint to call a script that stops the dimming transition of your bulbs.

4. **Is this compatible with ZHA?**
   - No. This specific blueprint is built around the `action` sensor state provided by Zigbee2MQTT. ZHA handles button events differently via the `zha_event` event bus.

5. **Can I use this to run scripts or control non-lighting devices?**
   - **Yes!** The inputs in this blueprint use the native Home Assistant `action` selector. This means you can assign absolutely anything to a button press. When configuring the blueprint in the UI, simply click **Add Action** and choose **Call Service** to run a script, toggle a fan, lock a door, or activate a scene.
