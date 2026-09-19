# ST OS Update Release Contract

## Channels

ST OS separates four update owners:

1. Debian system/security — APT.
2. Device firmware — fwupd/LVFS where supported.
3. Approved bundled applications — their approved package source.
4. ST OS components — this repository.

## ST OS component release flow

1. Build a versioned ST OS update `.deb`.
2. Generate the release manifest from the authoritative ST OS source commit.
3. Put the payload URL and SHA256 in the manifest.
4. Sign the manifest using the official private ST OS release key.
5. Verify the detached signature locally.
6. Publish payload, manifest and detached signature in one GitHub Release.
7. Test `Periksa Komponen ST OS` on a non-production installed ST OS.
8. Test update plus rollback/recovery before promotion.

## Fail-closed rules

The ST OS client must refuse installation when any of these conditions occurs:

- release public key is missing;
- manifest cannot be downloaded;
- detached signature is missing or invalid;
- product is not ST OS;
- payload type is unsupported;
- payload URL is missing;
- payload SHA256 is malformed;
- downloaded payload SHA256 does not match the signed manifest;
- package installation fails.

## Repository visibility

Do not place GitHub PATs or account tokens inside the ST OS ISO.
If this repository remains private, use a dedicated authenticated distribution
service instead of embedding credentials.
