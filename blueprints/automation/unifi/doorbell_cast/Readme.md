# 📺 UniFi Protect Doorbell: Stream to Google Nest Hub / Cast Displays

Automatically streams the live camera feed from your UniFi Doorbell to Google Nest Hubs or Chromecast screens when someone rings the doorbell, and automatically stops streaming after a customizable duration.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fepiech%2Fha-blueprints%2Fblob%2Fmain%2Fblueprints%2Fautomation%2Funifi%2Fdoorbell_cast%2Funifi_protect_doorbell_cast.yaml)

> [!NOTE]
> This blueprint is for **UniFi G4 Doorbell Pro Wi-Fi/PoE** paired via the official [UniFi Protect Integration](https://www.home-assistant.io/integrations/unifiprotect/). It is **not** for UniFi G4 Doorbell (UVC-G4-Doorbell), Doorbell Lite (UVC-Doorbell-B/UVC-Doorbell-Lite-W) or UniFi Access readers (such as the G2/G3/G6 Entry readers).

---

### 🎯 Features
- **Dual Trigger Support**: Works with either the `Last Doorbell Ring` timestamp sensor or the doorbell `binary_sensor`.
- **Smart Restart**: If pressed again while streaming, the timer resets so the video feed doesn't cut off prematurely.
- **Auto-Stop**: Automatically stops the stream after the configured duration (default: 90 seconds).
- **Nighttime Shield**: Ignores `unavailable` and `unknown` state transitions so Nest Hub screens don't turn on during overnight Home Assistant or network updates.
- **Multi-Device**: Stream to one or multiple Google Nest Hubs or Chromecast screens simultaneously.
- **Custom Actions Hook**: Optionally trigger extra actions alongside the stream (e.g., sound an indoor chime, pause media, or turn on porch lights).

---

### 🚀 How to Import

#### Method 1: My Home Assistant (One-Click)
Click the badge below to open your Home Assistant instance with the blueprint pre-filled:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fepiech%2Fha-blueprints%2Fblob%2Fmain%2Fblueprints%2Fautomation%2Funifi%2Fdoorbell_cast%2Funifi_protect_doorbell_cast.yaml)

#### Method 2: Manual Import via URL
1. In Home Assistant, navigate to **Settings** > **Automations & Scenes** > **Blueprints**.
2. Click **Import Blueprint** (bottom right).
3. Paste the following URL into the dialog:
   ```text
   https://github.com/epiech/ha-blueprints/blob/main/blueprints/automation/unifi/doorbell_cast/unifi_protect_doorbell_cast.yaml

---

❓ Troubleshooting & FAQ:

 1. Why is there a 5–10 second delay before video appears on the Nest Hub?
    - Google Cast devices play video via HLS (HTTP Live Streaming), which packages camera feeds into short segments. A 3–8 second latency is normal for Chromecast/Nest Hub devices buffering an HLS stream. Enabling the Low Latency HLS (LL-HLS) option under Home Assistant's camera settings or using go2rtc can significantly reduce this delay.
      
 2. Which camera entity should I select?
    - For best performance on Google Nest Hubs, use your doorbell's Medium or High Resolution Channel entity (e.g., camera.g4_doorbell_pro_high_resolution_channel). If you experience playback stuttering on older Nest Hubs, select the Medium resolution stream.
      
 3. Can I make it stop streaming if I answer the door earlier?
    - Yes. You can create a separate simple automation that calls media_player.media_stop on your Nest Hubs when your front door contact sensor changes to open.
