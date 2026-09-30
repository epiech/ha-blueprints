# 🛡️ UniFi Protect Blueprints

Automations designed for UniFi Protect doorbells and cameras connected via the official Home Assistant [UniFi Protect Integration](https://www.home-assistant.io/integrations/unifiprotect/).

---

## 1. UniFi Protect Doorbell: Fingerprint Door Unlock

Unlocks a smart lock when an authorized fingerprint is identified on a UniFi Protect G4 or G5 Doorbell Pro.

[![Import to Home Assistant](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fepiech%2Fha-blueprints%2Fblob%2Fmain%2Fblueprints%2Fautomation%2Funifi%2Funifi_protect_fingerprint_unlock.yaml)

### 🎯 Features
- **Anti-Reboot Safety Check**: Verifies that the fingerprint scan occurred within the last 10 seconds. This prevents your door from unlocking accidentally if the doorbell reboots or reconnects to the network and re-broadcasts its last event state.
- **Push Notifications**: Optionally sends a notification to selected mobile devices showing the person's name (e.g. *"Door unlocked by John"*).
- **Custom Actions Hook**: Run optional actions upon unlock (turn on hallway lights, chime a speaker, disarm an alarm).
- **Works with Any Lock**: Compatible with any Home Assistant `lock.*` entity (Schlage, Yale, August, SwitchBot, Zigbee, Z-Wave).

### 🚀 Import URL
```text
https://github.com/epiech/ha-blueprints/blob/main/blueprints/automation/unifi/unifi_protect_fingerprint_unlock.yaml
