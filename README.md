# Galaxy Buds 2 Pro Manager for iPhone

Open-source attempt to control Galaxy Buds 2 Pro (ANC, EQ, touch controls) from an iPhone without Samsung's app.

## Status: Phase 1 – feasibility probe

Buds 2 Pro normally talk to Samsung's app over Bluetooth Classic (RFCOMM). iOS blocks that for non-MFi apps, so an iPhone can only use **BLE**. We first check whether the Buds expose anything useful over BLE.

See [`docs/`](docs/) for the probe page.
