# Public Safety

This repository is public. Only what is listed under "May be public" is published.

## May be public
- Skills, prompts and Markdown docs
- Documentation, README, CHANGELOG, LICENSE
- Generic examples with placeholder values

## Never published
- Secrets: API keys, tokens, passwords, private keys, `.env` files, credentials
- Personal data: personal e-mails, phone numbers, addresses
- Client names and data; internal URLs and hosts
- Local absolute user paths; private notes, logs, memory or progress files

## Where private values live instead
- None: the plugin needs no secrets and holds no private values.

## Checks
- `scan_secrets.py . --history` (working tree plus full git history, run with the aiaddon checker scripts) before every release
- Allowed false positives: `.public-safety-allow`, entries for the public support address, a public vendor contact address quoted from the vendor's published docs, and old history hits (folder paths, no credential)

## If something leaks
Rotate the credential first, then remove it from history. Never force-push without the owner's explicit OK.
