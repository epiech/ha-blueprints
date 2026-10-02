# 🚪 UniFi Protect Doorbell: Unlock Smart Lock via Fingerprint or NFC

Unlocks a smart lock when an authorized fingerprint or approved NFC card is scanned on a UniFi Protect Doorbell Pro, featuring built-in safety reboot checks, UID filtering, and customizable push notifications.

> [!WARNING]
> **Security Reminder**: Standard NFC card UIDs (serial numbers) can be cloned or emulated using common NFC tools (e.g., Flipper Zero, Proxmark, or certain smartphones). Only whitelist tags and cards that you physically control and verify, and consider pairing NFC access with other security layers (such as entry cameras, door sensors, or secondary PINs).


[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fepiech%2Fha-blueprints%2Fblob%2Fmain%2Fblueprints%2Fautomation%2Funifi%2Ffingerprint_unlock%2Funifi_protect_fingerprint_unlock.yaml)

> [!NOTE]
> This blueprint requires a doorbell with built-in biometric and NFC hardware, such as the **UniFi G4 Doorbell Pro (Wi-Fi / PoE)** or **G5 Doorbell Pro**, integrated via the official [UniFi Protect Integration](https://www.home-assistant.io/integrations/unifiprotect/). It is **not** compatible with doorbells lacking fingerprint/NFC hardware (e.g., standard G4 Doorbell or Doorbell Lite) or UniFi Access standalone readers.

---

### 🎯 Features

- **Dual Access Methods (Fingerprint & NFC)**: Unlock your door using enrolled fingerprints, authorized NFC tags/cards/fobs, or both.
- **Independent Enable Toggles**: Toggle Fingerprint unlock, NFC unlock, or both on/off according to your preference.
- **Strict NFC Whitelisting**: Protects against unauthorized NFC scans. Only explicitly whitelisted Card UIDs can trigger an unlock. Matching is flexible and case-insensitive, automatically stripping colons and spaces (e.g. `ABCDEF1234` matches `ab:cd:ef:12:34`).
- **Anti-Reboot & Reconnect Safety Checks**: Prevents ghost unlocks when the doorbell reboots, updates firmware, or reconnects to Wi-Fi. It explicitly blocks transitions from `unavailable`/`unknown`/`restored` states, requires a new event timestamp, and enforces a strict 10-second freshness window.
- **Unknown Fingerprint Filtering**: Protects against unrecognized fingerprints by requiring an `identified` event type and a valid user ID.
- **Context-Aware Push Notifications**: Sends detailed push notifications to selected mobile devices specifying whether the door was unlocked via **Fingerprint** (with user name) or **NFC** (with tag UID and user name if assigned in Protect).
- **Universal Smart Lock Support**: Compatible with any Home Assistant lock entity (`lock.*`), including Yale, Schlage, August, SwitchBot, Zigbee, Z-Wave, and Matter locks.
- **Custom Actions Hook**: Run extra actions on a successful unlock (e.g., disarm security systems, turn on entryway lights, or chime a speaker).

---

### 🚀 How to Import

#### Method 1: My Home Assistant (One-Click)
Click the badge below to import directly into your Home Assistant instance:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fepiech%2Fha-blueprints%2Fblob%2Fmain%2Fblueprints%2Fautomation%2Funifi%2Ffingerprint_unlock%2Funifi_protect_fingerprint_unlock.yaml)

#### Method 2: Manual Import via URL
1. In Home Assistant, navigate to **Settings** > **Automations & Scenes** > **Blueprints**.
2. Click **Import Blueprint** (bottom right).
3. Paste the blueprint URL into the dialog:
   ```text
   https://github.com/epiech/ha-blueprints/blob/main/blueprints/automation/unifi/fingerprint_unlock/unifi_protect_fingerprint_unlock.yaml

   ```
4. Click Preview Blueprint, then click Import Blueprint.

---

### ❓ Troubleshooting & FAQ

1. **Which entities should I select for the Fingerprint and NFC sensors?**
   - Look for the `event` entities provided by the UniFi Protect integration:
     - **Fingerprint**: `event.<doorbell_name>_fingerprint` (e.g., `event.g4_doorbell_pro_poe_fingerprint`)
     - **NFC**: `event.<doorbell_name>_nfc` (e.g., `event.g4_doorbell_pro_poe_nfc`)

2. **How do I find my NFC card or tag UID?**
   1. Scan your card, fob, or phone at the G4 Doorbell Pro reader.
   2. In Home Assistant, navigate to **Settings** > **Tools** > **States** (or **Developer Tools** > **States** in older versions).
   3. Search for your NFC entity (e.g., `event.g4_doorbell_pro_nfc`).
   4. Locate the `nfc_id` attribute. Copy that value (e.g., `ABCDEF1234` or `04:12:a3:b4`) into the **Authorized NFC Card IDs** field of your automation.

3. **Will any random NFC tag or phone unlock the door?**
   - No. UniFi Protect emits an event whenever any readable NFC card or phone touches the reader. However, this blueprint strictly checks whether the scanned UID exists in your **Authorized NFC Card IDs** list. If the list is empty or the UID does not match, the scan is rejected.

4. **Can an unauthorized fingerprint trigger an unlock?**
   - No. The Protect integration fires events on both recognized and unrecognized fingerprints, but unrecognized prints do not contain a recognized user identifier. The blueprint requires `event_type: identified` and a valid, non-empty `user_id` attribute.

5. **Why does my notification say "Door unlocked via fingerprint (user_id)" instead of a person's name?**
   - Ensure you have linked the enrolled fingerprint to an actual user within the UniFi Protect console or app. If no `full_name` is present in the Protect attributes, Home Assistant falls back to displaying the `user_id`.

6. **Will my door unlock if the doorbell reboots, updates, or reconnects?**
   - No. Protect devices may restore state or replay cached attributes following network drops or reboots. This blueprint protects against replayed events by:
     - Ignoring any state transitions originating from `unavailable`, `unknown`, or `restored` states.
     - Confirming that the state timestamp actually changed (`trigger.from_state.state != trigger.to_state.state`).
     - Validating that the hardware event timestamp is less than 10 seconds old.

