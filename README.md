# Galaxy Buds 2 Pro Manager for iPhone

Control Galaxy Buds2 Pro from an iPhone with no Samsung app and no App Store install. It's a web page that talks to the Buds over Bluetooth LE.

**Open:** https://msrk0320.github.io/SamsungGalaxyBuds2Pro/ in the free **Bluefy** browser (Safari has no Web Bluetooth).

## Features

- Battery: left, right, case, wear and charging state
- Noise controls: Off / ANC / Ambient, ambient level, voice detect, ANC with one earbud
- Equalizer presets
- Touch lock, touch-and-hold action per side, double-tap edge for volume
- Find my Buds
- Seamless connection, ambient sound during calls, 360 Audio
- Model, firmware and serial

## How it works

Samsung's Android app talks to the Buds over Bluetooth Classic (RFCOMM), which iOS blocks for non-MFi apps. On Buds2 Pro (SM-R510), the same Samsung message protocol is also available over a BLE GATT pipe:

| | UUID |
|---|---|
| Service | `a7a473e9-19c6-491b-aea6-7ea92b8f043a` |
| Write (phone → buds) | `a7a48311-…` |
| Notify (buds → phone) | `a7a48322-…` |

Messages use Samsung's SPP framing: `FD | size(2, LE) | msgId | payload | CRC16-CCITT(LE) | DD`. Message IDs and payload layouts come from the open-source [GalaxyBudsClient](https://github.com/timschneeb/GalaxyBudsClient) project.

`docs/probe.html` is the BLE probe used to find the pipe.

## Tested

- Real Buds2 Pro (firmware R510XXU0AZD1) on iPhone 15 Pro with Bluefy: GATT discovery and ANC/Ambient/Off switching over the A7A4 pipe.
- All other controls and status decoding: tested against a simulated device. Please report anything that doesn't work.

For personal interoperability use only. Not affiliated with Samsung.
