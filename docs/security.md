# Nest security (draft v0.1)

## Promise

The company cannot read your messages, cannot reset your key, and holds no central store of readable data. There is no central database to breach.

## What we protect against

- A breach of Nest's servers or relays.
- A company insider, or a legal demand, trying to read user content.
- Passive network eavesdropping.
- Password leaks (there are no passwords).

## What we cannot fully protect against

Being honest about this matters more than a big promise.

- **A compromised phone.** Malware on a device can read what the user can read.
- **Phishing.** A user can be tricked into approving a login or sharing a recovery phrase.
- **A malicious recipient.** Someone who receives a message can copy it, photograph the screen or modify their app.
- **Metadata.** Who talks to whom, and when, is harder to hide than content. We minimise it but do not claim to remove it.
- **Lost keys.** If a user loses their device and every recovery option, the data is gone. Nobody can reset it.

## Keys and recovery

- Keys are created on the device and never leave it in readable form.
- Unlock with a passkey (biometric or device PIN).
- **Recovery phrase:** shown once, written down by the user, never stored by Nest.
- **Trusted circle:** the key is split with a secret-sharing scheme so that any 2 of 3 chosen contacts can restore it. No single contact can.
- Offer both. Make the trade-off clear in plain words.

## The Vault, honestly

- A sealed item is encrypted with its own one-time key.
- Expiry and view limits are enforced by the recipient's app and by deleting the key.
- This stops accidental sharing and leftover history. It does **not** stop a determined recipient from photographing the screen.
- The interface must say "hard to copy", never "cannot be copied".

## Email connector

- Read-only permissions only.
- Tokens live in the device's secure storage.
- Parsing happens on the device. Raw email is never uploaded.
- One-tap disconnect that deletes tokens and local extracts.

## Kid-safe lens

- Contacts need parent approval.
- No Vault, no links from strangers, no location sharing.
- Parent controls must work without the company reading messages.

## Engineering rules

1. Use audited libraries for Signal protocol, MLS and WebAuthn. No custom crypto.
2. No secrets in the repo. Scan every commit.
3. Pin and review dependencies. Treat a new package as a security decision.
4. Security-related changes need a human reviewer.
5. Test key handling, expiry, view limits and permissions.
6. Independent audit before real users, and again before large launches.

## If something goes wrong

1. Say what happened, plainly and quickly.
2. Rotate any affected relay or service credentials.
3. Because servers hold no readable data, focus on metadata exposure and affected clients.
4. Publish a short post-mortem.
