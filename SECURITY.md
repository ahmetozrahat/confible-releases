# Security policy

## Reporting a vulnerability

Email **info@confible.dev**. Do not open an issue, and do not post it in a
discussion — this repository is public and an issue is a disclosure.

Include what you need to include and nothing you do not: a description, the
version, and the smallest thing that demonstrates it. If you would rather not
put a proof of concept in an email, say so and we will agree on somewhere else
to put it.

You will get a reply within two working days — the same promise confible.dev/contact makes, because two pages promising different numbers is one page lying. If the report is valid you will
be told what the fix is and when it ships, and you will be credited in the
release notes unless you ask not to be.

## What is in scope

The desktop application, its installers and its auto-update path — the builds
published on this repository's [releases](../../releases) page — and the sync
API at `api.confible.dev`.

`confible.dev` itself is a static site with no backend and no session. Findings
there are welcome but the surface is small on purpose.

## What Confible already refuses to do

These are constraints in the code rather than intentions, and they are the
things worth trying to break:

- **Secrets never enter the renderer.** The window that draws the interface has
  never held a password or a private key. There is no IPC method that returns
  one. They live in the main process and go to the driver directly.
- **Credentials live in the operating system's own keystore** — Keychain,
  Credential Manager, libsecret. Confible does not invent a password file.
- **A changed host key stops the connection.** Trust on first use, and fail
  closed after it. There is no "continue anyway" for a production host whose
  fingerprint moved.
- **The sync server holds ciphertext it has no key for.** The key hierarchy is
  derived on your machine before the account exists.

A report that shows one of these is not true is the most valuable thing we
could receive.

## Supported versions

The current release. Fixes ship in a new version rather than as patches to an
older one.
