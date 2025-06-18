# MixBoard Companion Module

This module allows [Bitfocus Companion](https://bitfocus.io/companion) to interface with the **MixBoard** video mixing application over TCP. It supports real-time control of VideoInput switch, transitions, channels and keyers with full feedback support.

---

## Features

- Connect to MixBoard via TCP
- VideoInput program/preview switching (`IN 0` to `MAX_SUPPORTED_INPUT`)
- Control up to 4 channels (`CH-0` to `CH-3`)
- Trigger transitions (`CUT`, `FADE`, `TR1`–`TR4`)
- Toggle keyers (`BKGD`, `KEY1`–`KEY4`)
- Real-time status feedback

---

## Module Configuration

To configure this module in Companion, fill in the following fields:

| Setting       | Description                                      | Default |
|---------------|--------------------------------------------------|---------|
| `host`        | IP address or hostname of the MixBoard device    | *(required)* |
| `port`        | TCP command port                                 | `701`   |
| `eventport`   | TCP event/feedback port                          | `801`   |
| `protocollog` | Enable verbose TCP response logging (debug only) | `false` |

Ensure your network allows access to these ports.

---

## Actions

Once the module is configured, the following actions become available in Companion:

- **Set current channel** – Change the active channel (`CH-0` through `CH-3`)
- **Set Program VideoInput** – Set the VideoInput id to display to program
- **Set Preview VideoInput** – Set the VideoInput id to display to preview
- **Take** – Take transitions like `CUT`, `FADE`, `TR1`, etc.
- **Resume transition** – Resumed the paused transitions following the given direction (`BACKWARD` | `FORWARD`)
- **Toggle Keyer** – Enable/disable keyers (`KEY1`, `KEY2`, etc.) to program/preview according to 'Play to preview' option
- **Key link** – Enable/disable keyer transition link option to the given keyer (`KEY1`, `KEY2`, etc.) 
- **Execute command** – Execute custom MBC command
---

## Feedbacks

The module provides feedbacks to reflect the current state of the MixBoard:

- **Current channel** – The current channel has been changed
- **Key link** – The Key link status has changed
- **Keyer on Program** – The keyer has played to program
- **Keyer on Preview** – The keyer has played to preview
- **Keyer stopped** – The keyer has stopped
- **VideoInput name** – The VideoInput name has changed
- **VideoInput on Preview** – The preview VideoInput has changed
- **VideoInput on Program** – The program VideoInput has changed

These can be used to update button colors or labels in Companion dynamically.

---

## Connection and Lifecycle

- **`init(config)`** – Initializes the module, opens TCP connections, and sets up actions/feedbacks
- **`destroy()`** – Cleans up sockets and resources on module removal
- **`configUpdated(config)`** – Reacts to any configuration change and reinitializes if needed

---

## Troubleshooting

- Check IP/port configuration in Companion matches MixBoard's network settings.
- Enable `protocollog` in the module settings to log all incoming TCP responses for debugging.
- Watch Companion’s log for connection status or errors.

---

## License

MIT License

---

## Maintainer

This module is maintained by Dar of ClassX.

For issues or contributions, please use the [GitHub Issues](https://github.com/dar-dev/companion-module-classx-mixboard/issues) page.

