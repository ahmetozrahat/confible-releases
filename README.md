# Confiable — releases

Download artefacts for **Confiable**, a cross-platform connection manager
(SSH, SFTP, S3, PostgreSQL, MySQL and RDP).

Grab the latest build from the [Releases page](../../releases/latest).

| Platform | File |
| --- | --- |
| macOS (Apple silicon) | `.dmg` |
| Windows | `-setup.exe` |
| Linux | `.AppImage`, `.deb`, `.snap` |

## Why this repository exists

This repository holds **only build artefacts**. Confiable's source lives in a
separate, private repository.

The split is deliberate. Confiable checks for updates by reading the
`latest*.yml` files published here, and reading them from a *private*
repository would require a GitHub token shipped inside the application — where
it would belong to everyone who downloaded it, and could not be rotated without
cutting a new release. A public artefact repository needs no credential at all.

An update check is a single anonymous HTTPS GET of one small YAML file. It
sends no identifier, no telemetry and no information about what you connect to.

## Verifying a download

Every release includes `latest*.yml` carrying a SHA-512 for each artefact.
The in-app updater checks it automatically and discards a mismatch. To check a
manual download yourself:

```sh
shasum -a 512 -b <file> | cut -d' ' -f1 | xxd -r -p | base64
```

Compare the result with the `sha512` field for that file in the matching
`latest*.yml`.

## Issues

Bug reports and feature requests belong on the private source repository —
please raise them with the maintainer directly. Issues here are not monitored.
