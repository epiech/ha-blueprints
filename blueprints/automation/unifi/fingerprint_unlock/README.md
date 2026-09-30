# 🚪 UniFi Protect Doorbell: Unlock Smart Lock via Fingerprint

Unlocks a smart lock when an authorized fingerprint is scanned on a UniFi Protect Doorbell Pro, with built-in safety reboot checks and optional push notifications.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fepiech%2Fha-blueprints%2Fblob%2Fmain%2Fblueprints%2Fautomation%2Funifi%2Ffingerprint_unlock%2Funifi_protect_fingerprint_unlock.yaml)

> [!NOTE]
> This blueprint requires a doorbell with built-in fingerprint hardware, such as the **UniFi G4 Doorbell Pro (Wi-Fi / PoE)** or **G5 Doorbell Pro**, paired via the official [UniFi Protect Integration](https://www.home-assistant.io/integrations/unifiprotect/). It is **not** for UniFi doorbells without fingerprint sensors (original G4 Doorbell / Doorbell Lite) or UniFi Access readers.

---

### 🎯 Features
- **Anti-Reboot Safety Check**: Verifies that the fingerprint scan occurred within the last 10 seconds. This prevents your door from unlocking accidentally if the doorbell reboots, updates, or reconnects to the network and re-broadcasts its last event state.
- **Universal Lock Compatibility**: Works with any smart lock in Home Assistant (`lock.*`), including Schlage, Yale, August, SwitchBot, Zigbee, and Z-Wave locks.
- **User-Identified Notifications**: Optionally sends a push notification to selected mobile devices showing who unlocked the door (e.g. *"Door unlocked by John"*).
- **Custom Actions Hook**: Optionally trigger extra actions upon unlocking (e.g., turn on entryway lights, disarm an alarm system, or play a chime).

---

### 🚀 How to Import

#### Method 1: My Home Assistant (One-Click)
Click the badge below to open your Home Assistant instance with the blueprint pre-filled:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fepiech%2Fha-blueprints%2Fblob%2Fmain%2Fblueprints%2Fautomation%2Funifi%2Ffingerprint_unlock%2Funifi_protect_fingerprint_unlock.yaml)

#### Method 2: Manual Import via URL
1. In Home Assistant, navigate to **Settings** > **Automations & Scenes** > **Blueprints**.
2. Click **Import Blueprint** (bottom right).
3. Paste the following URL into the dialog:
   ```text
   https://github.com/epiech/ha-blueprints/blob/main/blueprints/automation/unifi/fingerprint_unlock/unifi_protect_fingerprint_unlock.yaml
   ```
4. Click Preview Blueprint, then click Import Blueprint.

---

❓ Troubleshooting & FAQ
1. Which entity should I select for the Fingerprint Sensor?
   - Look for the event entity associated with your doorbell's fingerprint reader, typically named event.<your_doorbell>_fingerprint (e.g., event.g4_doorbell_pro_poe_fingerprint).

2. Why does my notification say "Door unlocked by Authorized Fingerprint" instead of a person's name?
   - Make sure you have named the user/fingerprint inside the UniFi Protect app or console. If no name is assigned to that fingerprint in Protect, it falls back to the user ID or "Authorized Fingerprint".
     
3. Can an unauthorized or unrecognized fingerprint trigger an unlock?
   - No. The automation strictly triggers only when the fingerprint event status is identified. Unrecognized or rejected prints emit different event states (unidentified or failed) and are completely ignored.
     
4. Will my door unlock if the doorbell reboots or loses power?
   - No. The built-in safety check ensures that the event occurred within 10 seconds of execution. When UniFi Protect restarts or reconnects, any stale cached events are blocked by this condition.
