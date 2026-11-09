# Security Policy

## Supported versions

| Version | Supported |
|---|---|
| 1.0.x | Yes |

## Reporting a vulnerability

Please report suspected vulnerabilities privately through [GitHub's private vulnerability reporting](https://github.com/LordeStudios/LordeOS/security/advisories/new) rather than a public issue. Do not include credentials, pairing tokens or working exploit details in public posts.

## Signing

Release builds are signed with the Lorde Studios release key. If a build you downloaded is not signed by that key, or its SHA-256 does not match the checksum on the release page, do not install it.

## Runtime safety

Lorde OS runs application containers and a rootless Linux userspace on your device. It executes the software you launch. The companion bridge listens only on the device's own loopback interface (127.0.0.1) and requires a pairing secret before it accepts commands. Keep pairing codes private, review what you install into a container, and avoid running sensitive workflows unattended on a shared or untrusted device.
