# 🎛️ Lutron Caséta: 5-Button Pico Remote

Automate your standard 5-Button Lutron Caséta Pico Remote (e.g., PJ2-3BRL) through the official Home Assistant Lutron Caséta integration. Map all five buttons to any action you desire.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fepiech%2Fha-blueprints%2Fblob%2Fmain%2Fblueprints%2Fautomation%2Flutron%2Fcaseta%2F5_Button_pico_remote%2Fcaseta_pico_5_button_blueprint.yaml)

> [!NOTE]
> This blueprint requires the **official Lutron Caséta integration** (which relies on the Lutron Smart Bridge). By default, Home Assistant often disables Pico remote entities. Before using this blueprint, go to **Settings** > **Devices & Services** > **Lutron Caséta** > **Devices**, click on your Pico Remote, and ensure its entities are enabled.

---

### 🎯 Features

- **Full Button Mapping**: Map the Top (On), Up, Center (Favorite), Down, and Bottom (Off) buttons to absolutely any Home Assistant action.
- **Universal Action Support**: You are not limited to lights! Run any sequence of actions on button presses, including calling scripts, toggling fans, locking doors, setting scenes, running conditionals, or sending notifications.
- **Native Integration**: Relies on Home Assistant's native device triggers for rapid response times.

---

### 🚀 How to Import

#### Method 1: My Home Assistant (One-Click)
Click the badge below to import directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fepiech%2Fha-blueprints%2Fblob%2Fmain%2Fblueprints%2Fautomation%2Flutron%2Fcaseta%2F5_Button_pico_remote%2Fcaseta_pico_5_button_blueprint.yaml)

#### Method 2: Manual Import via URL
1. In Home Assistant, navigate to **Settings** > **Automations & Scenes** > **Blueprints**.
2. Click **Import Blueprint** (bottom right).
3. Paste the blueprint URL into the dialog:
```text
https://github.com/epiech/ha-blueprints/blob/main/blueprints/automation/lutron/caseta/5_Button_pico_remote/caseta_pico_5button_blueprint.yaml
```
4. Click Preview Blueprint, then click Import Blueprint.

---

### ❓ Troubleshooting & FAQ

1. **Why doesn't my Pico remote show up in the Device dropdown?**
   - Home Assistant often imports Pico remotes as "disabled" by default because they can generate a lot of events. You must manually enable them. Go to **Settings** > **Devices & Services** > **Lutron Caséta** > **Devices**, select your Pico remote, and click the gear icon to enable its entities.

2. **Can I use this to run scripts or control non-lighting devices?**
   - **Yes!** The inputs in this blueprint use the native Home Assistant `action` selector. This means you can assign absolutely anything to a button press. When configuring the blueprint in the UI, simply click **Add Action** and choose **Call Service** to run a script, toggle a fan, lock a door, or activate a scene.
