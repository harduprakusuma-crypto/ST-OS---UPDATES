# ST OS Updates

Official update channel repository for **ST OS — Simple Tawangsari**.

This repository is intentionally separate from the ST OS source repository.

## Purpose

Release assets published here are consumed by **ST OS System Center** for
ST OS-specific component updates. Debian security/system updates continue to
come from Debian repositories, and device firmware continues to use fwupd.

## Required release assets

Every ST OS update release must publish:

- `st-os-update-manifest.json`
- `st-os-update-manifest.json.asc`
- the signed update payload referenced by the manifest (currently a `.deb`)
- optional release notes

The manifest signature is verified before the payload is accepted. The payload
SHA256 inside the signed manifest must match the downloaded payload.

## Security

**Never commit private signing keys to this repository.**

ST OS clients contain only the public release key. The private signing key must
remain offline or in a protected release environment.

Unsigned manifests and payloads are rejected.

## Access requirement

Installed ST OS systems must be able to fetch release assets without embedding
GitHub credentials. If this repository remains private, a separate authenticated
update distribution service is required. For direct GitHub Releases delivery,
this repository must be readable by deployed ST OS clients.
