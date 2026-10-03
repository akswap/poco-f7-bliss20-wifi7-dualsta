# POCO F7 Bliss 20 Android 17 Wi-Fi 7 + Dual STA

Device-specific working files for **POCO F7 / onyx** running:

- ROM: Bliss-v20.0-onyx-OFFICIAL-gapps-20260923
- Android: 17
- Dual STA controller: v1.0.4-bliss17

## Important

These files are verified only on the ROM/build above. Do not flash the patched init_boot or load the .ko on another ROM or kernel build without checking exact compatibility. Keep a stock bootable image and fastboot access available.

For reliable secondary 6 GHz, keep the standalone 6 GHz profile module-managed. Saving it in Android Settings can promote it to primary.

## Release assets

| File | Purpose |
|---|---|
| POCO-F7-Bliss20-A17-WiFi7-6GHz-320MHz-v1.0-UNIFIED.zip | 6 GHz Wi-Fi 7 / 320 MHz hotspot module using ACS |
| POCO-F7-Bliss20-A17-DualSTA-Resources-v1.0.zip | Android Multi-STA resource overlays |
| POCO-F7-Bliss20-A17-DualSTA-Controller-v1.0.4.zip | Boot auto-connect, fallback and hotspot-aware controller |
| DualStaProfileManager-Bliss20-A17-v2.0.1.apk | Bliss profile manager using cmd wifi status |
| init_boot_a_Bliss17_Hotspot_DualSTA_TEST.img | Rooted init_boot with working patched Wi-Fi driver |
| qca_cld3_wcn7750-bliss17-dualsta-CANDIDATE.ko | Candidate driver for future ROM comparison/porting |
| SHA256SUMS.txt | Asset integrity hashes |

No Wi-Fi credentials are included in the module ZIPs.

## Installation order

1. Flash the matching patched init_boot only on the exact Bliss build above.
2. Install the Wi-Fi 7/6 GHz unified module.
3. Install the Dual STA Resources module.
4. Install the Dual STA Controller v1.0.4 module.
5. Reboot.
6. Install the APK and create your own profiles.

For hotspot operation, leave 6 GHz channel selection on ACS/automatic.

## Verified Dual STA combinations

| Primary STA | Secondary STA | Result |
|---|---|---|
| MLO 5+6 GHz | 2.4 GHz | PASS |
| MLO 5+6 GHz | 5 GHz | PASS |
| MLO 5+6 GHz | standalone 6 GHz | PASS |
| standalone 6 GHz | 5 GHz | PASS |
| standalone 6 GHz | 2.4 GHz | PASS |
| 5 GHz | standalone 6 GHz | PASS |
| 2.4 GHz | standalone 6 GHz | PASS |
| 2.4 GHz | 2.4 GHz | PASS |
| 5 GHz | 5 GHz | PASS |
| 2.4 GHz | 5 GHz | PASS |

The strongest verified case was primary MLO with a live 6 GHz link plus standalone 6 GHz secondary on the same router/channel.

## Verified hotspot

- 6 GHz SoftAP
- 320 MHz using ACS
- Wi-Fi 7 / 802.11be client connection verified

## Rollback

If the device does not boot, restore the original matching init_boot through fastboot. To disable a Magisk module, create its disable marker from recovery/ADB or remove it and reboot.

Experimental device/ROM-specific port. Use at your own risk.
