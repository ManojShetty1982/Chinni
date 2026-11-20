# Nest

A chat and life-organising app for every age. You own the keys, not the company.

Nest tries to fix what is hard about WhatsApp and Telegram:

| Problem today | Nest's answer |
|---|---|
| One endless list of chats | **Orbit**: people and groups sit on rings around you. Closer means more urgent. |
| Hundreds of unread messages | **Catch me up**: a 10-second summary. |
| Decisions buried in scroll | **Decided** tab: dates, venues and tasks pinned automatically. |
| Banter hiding real questions | **Now** tab shows only what needs you. Quiet messages fold away. |
| Forgotten replies | **Later** snoozes a message and brings it back. |
| Private details left in history | **Vault**: seal a detail. One view, then it is gone. |
| Apps built for one kind of user | **Lenses**: Standard, Big and simple, Kid-safe. |
| Chat and life kept apart | **Coming up**: flights, appointments and tickets found in your email. |
| Voice notes you cannot skim | Voice notes with transcripts, plus voice rooms with live captions. |

## Status

Front-end prototype only. Everything you see is simulated: no real accounts, encryption, messaging, voice or email access yet. Do not put real private data into it.

## Run it

Open `index.html` in a browser. No build step.

## Folder layout

```
nest/
├── README.md
├── CLAUDE.md          Instructions for Claude Code
├── index.html         Current prototype (Nest Orbit)
├── prototype/         Older prototype versions, for reference
├── docs/
│   ├── architecture.md
│   ├── security.md
│   └── roadmap.md
└── app/               Real app code (created when we outgrow one file)
    ├── client/
    ├── relay/
    └── tests/
```

## Host it

Use GitHub Pages: Settings, then Pages, then deploy from the main branch. Netlify and Cloudflare Pages also work.

## Security principles

1. Keys are created on the user's device and never leave it.
2. The company holds no copy of any key and cannot reset one.
3. Use proven protocols (Signal protocol or MLS). Never write our own cryptography.
4. Sign in with device passkeys. No passwords to leak.
5. Recovery through a recovery phrase or a trusted circle (any 2 of 3 restore the key).
6. Email is read on the device. Nest never stores it.
7. No secrets in this repo, ever.
8. An independent security audit before real users.

## Roadmap

1. Accounts: device-made keys and passkeys.
2. Live encrypted messaging over a decentralised relay.
3. Vault with real expiry and view limits.
4. Voice notes, then voice rooms.
5. Email connection (read-only Gmail and Outlook).
6. AI summaries and decision detection, on device where possible.
7. Security audit, then a small private beta.

## Working with Claude

Make one small change per branch. Ask Claude to explain each change, preview it, then merge. Read `CLAUDE.md` for the rules Claude follows in this repo.
