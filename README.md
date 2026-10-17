# Galaxy Buds 2 Pro Manager for iPhone

Open-source attempt to control Galaxy Buds 2 Pro (ANC, EQ, touch controls) from an iPhone without Samsung's app.

## Status: Phase 1 – feasibility probe

Buds 2 Pro normally talk to Samsung's app over Bluetooth Classic (RFCOMM). iOS blocks that for non-MFi apps, so an iPhone can only use **BLE**. We first check whether the Buds expose anything useful over BLE.

See [`docs/`](docs/) for the probe page.

## Findings so far (Buds2 Pro SM-R510, fw R510XXU0AZD1)

Over BLE the iPhone sees Device Info, Battery, LE Audio services, and two Samsung-specific services:

- `A7A473E9-19C6-491B-AEA6-7EA92B8F043A`: write `…8311`, notify `…8322` (likely control pipe)
- `8FE1`: write `8FCC`, notify `8FCB`

The probe page now has a **Samsung control test** panel that sends the Android app's ANC/Ambient/Off command over these pipes.

## Try the probe

1. Enable GitHub Pages: repo **Settings → Pages → Deploy from branch → `main` / `/docs`**.
2. On iPhone, install **Bluefy** (free, App Store) and open `https://msrk0320.github.io/SamsungGalaxyBuds2Pro/`.
3. Tap **Scan**, pick the Buds, then **Copy report**.

## Roadmap

- **Phase 1 (now):** BLE probe – what services do the Buds expose to iPhone?
- **Phase 2 (if a control channel exists):** use [REA](https://github.com/morluto/rea) on Samsung's Galaxy Wearable / Buds 2 Pro plugin APK to map the message IDs (ANC, ambient, EQ, touch lock, battery), cross-checked with the protocol documented by [GalaxyBudsClient](https://github.com/timschneeb/GalaxyBudsClient).
- **Phase 3:** full manager UI in the same web page (no App Store app, no Mac needed).

If BLE exposes nothing useful, iPhone control isn't possible without Apple MFi certification; the fallback is managing the Buds from a PC.

For personal interoperability use only. Not affiliated with Samsung.
