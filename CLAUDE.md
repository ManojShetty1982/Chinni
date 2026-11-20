# CLAUDE.md

Guidance for Claude Code when working in this repo.

## What this project is

Nest is a chat and life-organising app for kids, adults and elderly people. Users own their encryption keys. The company must never be able to read messages or reset keys. See `README.md` for the full vision and roadmap.

## Current state

`index.html` is a single-file front-end prototype (Nest Orbit) with simulated data. There is no backend yet.

## Rules

1. **Security first.** Never write custom cryptography. Use well-reviewed libraries for the Signal protocol or MLS, and WebAuthn for passkeys.
2. **Keys stay on the device.** Never add code that sends a private key, recovery phrase or decrypted message to a server.
3. **No secrets in the repo.** No API keys, tokens or passwords. Use environment variables and tell me what to set.
4. **Email is read on device.** Never store a user's email on our servers.
5. **Accessibility is a feature.** Every screen must work in all three lenses: Standard, Big and simple, Kid-safe. Keep keyboard focus visible, respect reduced motion, and support light and dark themes.
6. **Kid-safe lens:** only parent-approved contacts, no Vault, no link sharing.
7. **Plain language in the interface.** Short sentences, sentence case, buttons that say exactly what they do.

## How to work

- Make one small change at a time, on its own branch.
- Before editing, explain the plan in a few lines.
- After editing, explain what changed and how to test it.
- Add or update tests for anything involving keys, sharing, expiry or permissions.
- Flag security-sensitive changes clearly so a human reviews them.
- If a request would weaken privacy (for example, a company-held key), say so and suggest an alternative.

## Definition of done

The change works in all three lenses, passes tests, adds no secrets, and the README or docs are updated if behaviour changed.
