# Nest architecture (draft v0.1)

## Goal

Chat, voice and life-organising where users hold the keys. The company runs no central store of readable data.

## Building blocks

| Block | Plan | Notes |
|---|---|---|
| **Client** | Progressive web app first, native apps later | One codebase, three lenses (Standard, Big and simple, Kid-safe). |
| **Identity** | Keypair made on the device, plus a passkey (WebAuthn) to unlock it | No passwords. No account recovery by the company. |
| **Messaging encryption** | Signal protocol for 1:1, MLS for groups | Use audited libraries. Never custom crypto. |
| **Transport** | Decentralised relays (Matrix-compatible or Nostr style) | Relays carry encrypted blobs only. Anyone can run one. |
| **Local storage** | Encrypted database on the device | Search and summaries run locally. |
| **Backup** | Encrypted with the user's key before upload | Optional. The server cannot read it. |
| **Vault** | Sealed items with a one-time key, expiry and a view limit | See limits in `security.md`. |
| **Voice** | WebRTC with end-to-end encrypted media | Live captions made on the device. |
| **Email connector** | OAuth, read-only, parsed on the device | Access tokens stay in the device's secure storage. Mail is never uploaded. |
| **AI features** | On-device models first (summaries, decision detection) | Any cloud model is opt-in and sees only what the user chooses to send. |

## Data flow (message)

1. Sender's device encrypts the message to each recipient's keys.
2. Encrypted blob goes to a relay.
3. Relay forwards it. It cannot read it.
4. Recipient's device decrypts it and runs local features (Now, Decided, Catch me up).

## Orbit logic (runs locally)

- **Ring position:** from urgency signals such as unanswered questions, mentions, deadlines found in email and recency.
- **Decided tab:** a local model flags dates, places and tasks, and the user can pin or correct them.
- **Quiet fold:** reactions, stickers and chatter are grouped by a local classifier.

## Open decisions

1. **Relay protocol:** Matrix (mature, federated) versus Nostr (simple, lighter) versus custom. Leaning Matrix for maturity.
2. **Client:** progressive web app versus Flutter. Web is fastest to ship. Native gives better voice and background behaviour.
3. **Push notifications:** Apple and Google push services see metadata. Decide how much to minimise.
4. **Key recovery default:** recovery phrase only, or trusted circle by default.
5. **Moderation for the Kid-safe lens:** parent controls need to work without the company reading messages.

## Build order

1. Keys and passkeys (local only).
2. Two-device encrypted messaging against a test relay.
3. Orbit and Now, Decided, Vault on real data.
4. Voice notes, then voice rooms.
5. Email connector.
6. Local AI features.
7. Independent security audit.
