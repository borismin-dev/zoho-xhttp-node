# zoho-xhttp-node

Node.js launcher for Zoho Catalyst AppSail: writes an Xray config (VLESS + XHTTP packet-up) from environment variables and spawns Xray on the platform port.

Sanitized archive of a working deployment (verified 2026-10-29, generate_204 = 204). All secrets are placeholders — real values live in platform env vars / local secret files, never in this repo.

## Notes
- Client MUST use ALPN http/1.1: the Zoho gateway breaks WebSocket upgrades and negotiated h2 (frame-too-large).
- sing-box does not support the xhttp transport — use an Xray-based client or Shadowrocket.
- Copy `app-config.example.json` to `app-config.json` and fill in your own UUID / WS_PATH.
- The Xray binary is not included; `server.js` downloads the pinned release at runtime if `./xray` is absent.
