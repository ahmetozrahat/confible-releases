# Confible

**All your servers. One window.**

SSH, files, databases, object storage, remote desktop and Redis — every
connection you own, in one focused workspace. macOS, Windows and Linux.

[**confible.dev**](https://confible.dev) · [Download the latest build](../../releases/latest) · [Roadmap](#roadmap) · [Report a bug](../../issues/new?template=bug_report.yml) · [Discussions](../../discussions)

---

## What this repository is

**The public face of a private product.** The source lives in a private
repository; what lives here is everything that has to be public for the product
to be usable and honest about itself:

| | |
| --- | --- |
| [Releases](../../releases) | Every build we ship, with the `latest*.yml` the in-app updater reads |
| [Issues](../../issues) | Bug reports and ideas — **read, and answered** |
| [Roadmap](#roadmap) | What is planned, in progress and shipped |
| [Discussions](../../discussions) | Questions, and ideas you want to talk through before filing |
| [Security policy](SECURITY.md) | How to report a vulnerability, and what is worth trying to break |

The artefact split is deliberate rather than incidental. Confible checks for
updates by reading the `latest*.yml` files published here, and reading them
from a *private* repository would require a GitHub token shipped inside the
application — where it would belong to everyone who downloaded it, and could not
be rotated without cutting a new release. A public artefact repository needs no
credential at all.

An update check is a single anonymous HTTPS GET of one small YAML file. It sends
no identifier, no telemetry and nothing about what you connect to.

## Downloads

| Platform | Architecture | File | Signing |
| --- | --- | --- | --- |
| macOS | Apple silicon | `.dmg` | Signed and notarized |
| macOS | Intel | `.dmg` | Signed and notarized |
| Windows | x64 | `-setup.exe` | **Unsigned** — SmartScreen will interrupt |
| Linux | x86_64 | `.AppImage` | **Unsigned** |
| Linux | amd64 | `.deb` | **Unsigned** |

Requirements: macOS 12 Monterey or later · Windows 10 (1809) or later, x64 · a
glibc 2.31 distribution or later.

There is **no brew, winget or AUR tap yet.** They are decided and they wait on
code signing, because a package manager distributes an identity as much as a
binary. See the roadmap.

[**confible.dev/download**](https://confible.dev/download) lists every artefact
with its size, its signing state, its SHA-256 and the exact command to verify
it on that platform. Each release here also carries `latest*.yml` with a
SHA-512 per file, which is what the in-app updater checks — a mismatch is
discarded rather than installed.

## Trying it

Fourteen days, the whole product, no card. Every workspace and every engine —
there is no reduced build, because a trial that hides the thing you were
evaluating tells you nothing. On day fifteen nothing is deleted: your
connections, identities, snippets and settings are where you left them.

Pricing is one purchase, not a subscription, and it is lower in some countries —
[confible.dev/pricing](https://confible.dev/pricing) will tell you which one is
yours before you pay anything.

## Roadmap

The labels are the roadmap. These queries are live, so nothing here can go stale
against a hand-written list:

- 🔵 [**Planned**](https://github.com/ahmetozrahat/confible-releases/issues?q=is%3Aissue+is%3Aopen+label%3A%22status%3A+planned%22) — decided and queued
- 🟣 [**In progress**](https://github.com/ahmetozrahat/confible-releases/issues?q=is%3Aissue+is%3Aopen+label%3A%22status%3A+in+progress%22) — being worked on now
- 🟢 [**Shipped**](https://github.com/ahmetozrahat/confible-releases/issues?q=is%3Aissue+label%3A%22status%3A+shipped%22) — released, with the version on the issue
- ⚪️ [**Not planned**](https://github.com/ahmetozrahat/confible-releases/issues?q=is%3Aissue+label%3A%22status%3A+not+planned%22) — considered and declined, **with the reason**

Nothing gets a date. A one-person product that promises a quarter and misses it
has told you less than one that promises an order and keeps it.

An idea that is taken gets `status: planned` — that is the whole mechanism, and
it means an accepted request appears on the roadmap rather than in a reply that
nobody reads again.

## Reporting something

- **A bug** → [open an issue](../../issues/new?template=bug_report.yml). The
  template asks for the version, the OS and what is on the other end, because
  those three are usually the difference between a fix and a guess.
- **An idea** → [open an issue](../../issues/new?template=feature_request.yml),
  or a [discussion](../../discussions) if you want to argue about the shape of
  it first.
- **A vulnerability** → **not here.** [SECURITY.md](SECURITY.md).
- **Licence, billing, a refund** → [confible.dev/contact](https://confible.dev/contact).
  It needs an address we can reply to, not a public thread.

Confible ships no telemetry, which means nothing about your systems reaches us
unless you type it into one of these. It also means **this page is public** —
redact hostnames and never paste a key. The templates say so at the top.

## Not open source

Confible is a paid product and the source is private. This is said here rather
than left to be discovered, because a repository under a product's name reads
like an offer of the code and this one is not.

What you can verify without the source is on
[confible.dev/security](https://confible.dev/security): what the app refuses to
do, where secrets live, and why the sync server holds ciphertext it has no key
for.
