# SetuSSH downloads

Installers for **SetuSSH**, an SSH client for Windows, macOS and Linux with
tabbed terminals, split panes, SFTP file transfer, SSH tunnels and an AI
assistant. *Setu* (सेतु) is Sanskrit for *bridge*: SetuSSH is the bridge
between you and your servers.

**Official site: [setussh.com](https://setussh.com)**

**[Download the latest build](https://github.com/SetuSSH/setussh-releases/releases/latest)**

This repository holds only the built installers. The source code is not
public.

## What it costs

The first 7 days have everything turned on, with no key, account or card.
After that SetuSSH keeps working for free with up to 10 saved sessions, and
the AI assistant is paused. Nothing is deleted. A full-access key lifts the
limits and is free on request: [ask at setussh.com](https://setussh.com/#request).

## Installing

**Windows:** run `SetuSSH-Setup-*.exe`. Builds are not code-signed yet, so
SmartScreen says "Unknown publisher". Choose **More info**, then **Run anyway**.

**macOS:** open the `.dmg` for your Mac (`arm64` for Apple silicon, `x64` for
Intel) and drag SetuSSH to Applications. Gatekeeper reports an unsigned app as
damaged. It is not. Clear the flag once:

```sh
xattr -cr /Applications/SetuSSH.app
```

**Linux:** add the SetuSSH apt repository once, and updates come through
`apt upgrade` like everything else:

```sh
curl -fsSL https://setussh.com/apt/setussh.gpg \
  | sudo tee /usr/share/keyrings/setussh.gpg > /dev/null

echo "deb [signed-by=/usr/share/keyrings/setussh.gpg] \
https://setussh.com/apt stable main" \
  | sudo tee /etc/apt/sources.list.d/setussh.list

sudo apt update && sudo apt install setussh
```

The `.deb` from a release also installs on its own
(`sudo apt install ./SetuSSH-*-amd64.deb`), but it will not update itself.
The `.AppImage` is portable but needs `libfuse2`.

## Checking a download

Every release has a `SHA256SUMS` file and a `SHA256SUMS.asc` signature, made
with the key that signs the apt repository:

```sh
curl -fsSL https://setussh.com/apt/setussh.asc | gpg --import
gpg --verify SHA256SUMS.asc SHA256SUMS
sha256sum -c SHA256SUMS --ignore-missing
```

## Reporting problems

If SetuSSH crashes it offers to send a report, which is the fastest route to a
fix. The report carries no hostnames, credentials or file contents. You can
also write to [support@setussh.com](mailto:support@setussh.com); please include
your platform and the build version.

---

© 2026 Jayesh Barman. Distributed under the [EULA](https://setussh.com/eula.html).
