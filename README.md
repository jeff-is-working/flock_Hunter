# flock_Hunter

WiFi-based surveillance device scanner for the Orbic RC400L mobile hotspot.

> **Status: Early concept — feasibility TBD**

## Concept

Run a passive WiFi OUI scanner on the Orbic RC400L (a $30 LTE hotspot that EFF's [rayhunter](https://github.com/EFForg/rayhunter) project has already rooted and documented). Detect Flock cameras, ALPRs, and other surveillance tech by matching WiFi MAC prefixes against a known database.

Think [oui-spy-too](https://github.com/jeff-is-working/oui-spy-too) but running natively on the Orbic instead of an ESP32 + Raspberry Pi.

## Why the Orbic?

- $30, pocket-sized, battery-powered
- Rayhunter already has a working root exploit and deployment pipeline
- WiFi radios (2.4GHz + 5GHz), writable filesystem, init.d persistence
- Could run alongside rayhunter (IMSI catcher detection + surveillance scanner in one device)

## Open Questions

- **No BLE** — the Orbic has no Bluetooth radio. oui-spy-too relies heavily on BLE for detection (company IDs, service UUIDs). WiFi-only scanning may miss many targets.
- **WiFi monitor mode** — does the Orbic's WiFi chipset/driver support monitor mode or passive scanning? If not, detection is limited to devices on the same network.
- **OUI database coverage** — how many surveillance devices are detectable via WiFi alone vs BLE? Need to audit the oui-spy-too database for WiFi-only viability.
- **GPS** — no hardware GPS on the Orbic. Cellular location is imprecise. Could use phone browser geolocation via the web UI (same approach as oui-spy-too).
- **Resource constraints** — how much CPU/RAM/storage is available after rayhunter is running?
- **Is this concept even useful?** — if most surveillance devices aren't discoverable via WiFi OUI scanning alone, this may not be worth pursuing.

## Related Projects

- [oui-spy-too](https://github.com/jeff-is-working/oui-spy-too) — ESP32 + Pi surveillance scanner (BLE + WiFi)
- [ESP-GlassHole](https://github.com/jeff-is-working/ESP-GlassHole) — ESP32 BLE smart glasses detector
- [rayhunter](https://github.com/EFForg/rayhunter) — EFF's IMSI catcher detector for the Orbic RC400L
- [oui-spy](https://github.com/colonelpanichacks/oui-spy) — Original OUI-based surveillance scanner

## License

GPL-3.0
