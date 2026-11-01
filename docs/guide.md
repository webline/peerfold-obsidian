# Peerfold – Guide

Peerfold lets you share a folder of your Obsidian vault with other people. You work on the same notes, and changes reach everyone after saving. There is no account and no server run by the developer; everything is end-to-end encrypted.

*Deutsche Fassung: [anleitung.md](anleitung.md)*

## Contents

1. [What you need](#what-you-need)
2. [Installation](#installation)
3. [First-time setup](#first-time-setup)
4. [Sharing a folder](#sharing-a-folder)
5. [Following an invitation](#following-an-invitation)
6. [Setting up a mailbox](#setting-up-a-mailbox)
7. [Directly over the internet](#directly-over-the-internet)
8. [Day to day](#day-to-day)
9. [Managing members](#managing-members)
10. [Troubleshooting](#troubleshooting)
11. [Privacy](#privacy)

## What you need

- Obsidian 1.8.7 or later on macOS, Windows or Linux. Peerfold does not run on iPhone, iPad or Android.
- To work together beyond your own network: a **mailbox**, i.e. online storage everyone involved can reach. This can be a Nextcloud or S3 storage ([section 6](#setting-up-a-mailbox)).
- A way to send invitations confidentially, e.g. an end-to-end encrypted messenger.

## Installation

### Manually

1. From the latest [release](https://github.com/webline/peerfold-obsidian/releases/latest), download `main.js`, `manifest.json` and `styles.css`.
2. Open your vault folder in Finder or Explorer. The `.obsidian` folder is hidden; on a Mac, show it with <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>.</kbd>.
3. Create the folder `.obsidian/plugins/peerfold/` and copy the three files into it. The folder must be named exactly `peerfold`.
4. In Obsidian, open *Settings → Community plugins*. Turn off restricted mode, reload the list and enable **Peerfold**.

### With BRAT

[BRAT](https://github.com/TfTHacker/obsidian42-brat) installs beta plugins straight from GitHub and keeps them up to date.

1. Install and enable BRAT from the community plugins.
2. In BRAT, choose *Add beta plugin* and enter `webline/peerfold-obsidian`.

## First-time setup

On first start the **setup assistant** opens. It walks you through four steps:

1. **Device name:** how the others see you. A first name plus device, e.g. "Anna laptop", is clearest.
2. **Connection routes:** local network and direct connection over the internet. Both are on by default.
3. **Mailbox:** what it is and which options exist.
4. **Let's go:** share a folder or follow an invitation.

You can open the assistant again at any time: command palette (<kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>P</kbd>) → "Peerfold: Open setup assistant", or *Settings → Peerfold → Help*.

> [!NOTE]
> On first start your system firewall may ask whether Obsidian may accept incoming connections. Allow it for private networks, otherwise devices on the same network won't find each other.

## Sharing a folder

1. Right-click the folder in the file explorer and choose **Share with Peerfold**.
2. Enter a mailbox if you don't only work on the same network, and click **Test connection**. Without a mailbox, choose **No mailbox**.
3. Peerfold checks the links in the folder: images and other attachments stored outside are copied into the `Anhänge` subfolder and the links are updated. Links to notes outside the folder are reported.
4. The invitation dialog opens. Decide whether to include mailbox access and click **Copy invitation**.
5. Paste the text into an email or message and send it. It contains short instructions and the invitation link.

An invitation is valid for **one device** and **seven days**. Create a new one for every further person or device (right-click the folder → **Peerfold: Invite…**).

> [!WARNING]
> If you include mailbox access, the password is contained in the invitation. Ideally send it through a messenger with end-to-end encryption. Create a separate app password for it that you can revoke at any time.

### Approving the request

As soon as someone accepts the invitation, a dialog shows their name and **device ID**. Compare the ID with the person (phone, chat) before clicking **Approve**. The device then receives the folder key and the files.

## Following an invitation

1. Click the link in the invitation. If nothing happens, copy the whole message and choose **Peerfold: Accept invite…** in the command palette. Peerfold picks up the invitation from the clipboard.
2. Choose a location in your vault, e.g. `Shared/Project`. A new, empty folder works best.
3. Click **Request to join**. The person who invited you has to approve; they see your device ID (shown under *Settings → Peerfold → Device ID*).
4. After approval the files arrive. On the same network this takes seconds, through the mailbox up to the next check (default: one minute).

## Setting up a mailbox

You need the mailbox when you work in different places or aren't online at the same time. It also sets up the direct connection. It only holds encrypted data with unrecognisable names.

### Nextcloud (WebDAV)

1. Log in to your Nextcloud and create a folder, e.g. `Peerfold`.
2. Create an **app password**: avatar top right → *Personal settings → Security → Create new app password*. Name it e.g. "Peerfold".
3. Enter in Peerfold:

| Field | Value |
|---|---|
| Type | WebDAV |
| Address | `https://cloud.example.com/remote.php/dav/files/USERNAME/Peerfold/` |
| Username | your Nextcloud username |
| Password | the app password |

Nextcloud also shows the exact WebDAV path in the Files app under *Files settings → WebDAV* (bottom left).

For several people there are two options: everyone uses the same access (simplest: include mailbox access with the invitation), or you share the folder in Nextcloud with the others and everyone enters their own access with the path to the shared folder.

### S3 storage

Any S3-compatible storage works, e.g. Hetzner Object Storage, IONOS or your own MinIO server. Example for Hetzner (Falkenstein):

| Field | Value |
|---|---|
| Type | S3-compatible |
| Endpoint | `https://fsn1.your-objectstorage.com` |
| Region | `fsn1` |
| Bucket | name of your bucket |
| Prefix | optional, e.g. `peerfold` |
| Access key ID / secret access key | from the provider's console |
| Path style | on |

Create the bucket in the provider's console first and give the key read and write access to that bucket only.

### Changing the mailbox later

*Settings → Peerfold →* click **Mailbox** next to the folder. All members must use the same mailbox. If you switch, send the new access details to the others; they enter them under **Mailbox** on their side.

## Directly over the internet

When devices are in different places, Peerfold tries a direct connection (WebRTC). The mailbox sets it up; no third-party server is involved.

- **With IPv6 on both sides** this works without further steps. Most fibre, cable and mobile connections have IPv6. [test-ipv6.com](https://test-ipv6.com) shows whether yours does.
- **With IPv4 only** behind a router (NAT) it usually doesn't work. Syncing then continues through the mailbox, just a little slower. If you run your own STUN or TURN server (e.g. coturn), enter it under *Settings → Peerfold → Own STUN/TURN servers*:

```text
stun:stun.example.com:3478
turn:user:password@turn.example.com:3478
```

The status window (click the status bar) and the member list show which route is active: "connected on the LAN" or "connected directly over the internet".

## Day to day

### The status bar

| Display | Meaning |
|---|---|
| Icon and ✓ | everything synced |
| ↻ 3 | three files haven't reached everyone yet |
| ✉ 1 | a join request is waiting for you |
| ⚠ | a problem; click for details |

### Conflicts

If two people edit the same note at the same time in different places, Peerfold merges the changes. If they overlap, one version stays in the note and the other is saved next to it as a copy:

```text
Plan (Konflikt Anna laptop 2026-10-31 1955 UTC).md
```

The time in the name is UTC and the word "Konflikt" is fixed, so the name is identical on every device. Take what you need and delete the copy.

### Attachments and links

- If you insert an image stored outside the shared folder, Peerfold copies it into the `Anhänge` folder on save.
- Links to notes outside the folder appear unresolved for the others. Peerfold warns you; in the settings you can have them converted to plain text instead.
- If someone renames a file, links are updated for everyone. If someone deletes a file, the link's text remains.
- The command **Show orphaned attachments in the shared folder** lists attachments no note refers to. Removing moves them to the trash.

### What to avoid

- Syncing the shared folder **additionally** with iCloud, Dropbox or Obsidian Sync. Exclude it there, otherwise two systems work against each other.
- Posting invitation codes in public channels.

## Managing members

- **View members:** right-click the folder → **Peerfold: Members**.
- **Remove someone** (owner only): click **Remove** next to the member in the member list. The device receives nothing new afterwards and cannot rejoin; it keeps what it already has.
- **Leave yourself:** *Settings → Peerfold →* **Leave** next to the folder. Your files stay; keys and your data in the mailbox are deleted.
- **End sharing** (owner only): nobody receives changes any more, the mailbox is emptied, everyone keeps the files.
- **New device** (e.g. a second laptop): every device is a member of its own and needs its own invitation.

## Troubleshooting

| What happens | Possible cause | What helps |
|---|---|---|
| The join request doesn't arrive | different network and no mailbox in the invitation | create a new invitation including mailbox access |
| Devices on the same Wi-Fi don't find each other | firewall blocks Obsidian; guest Wi-Fi isolates devices | allow Obsidian in the firewall; under *Fixed addresses* enter the other device's IP and port (e.g. `192.168.1.20:47322`) |
| "Access denied" for the mailbox | wrong password or app password revoked | check access, **Test connection** |
| "Not found" for the mailbox | folder or bucket missing, wrong address | create the folder in Nextcloud or the bucket, address ending in `/` |
| "n file(s) still waiting for data" | the device holding the file is offline and there is no mailbox | wait until it is online, or set up a mailbox |
| No direct connection | one side has no IPv6 | syncing continues through the mailbox; optionally your own STUN/TURN server |
| "Access revoked" | you were removed from the folder | ask the person who shared it |

If nothing helps: **command palette → Peerfold: Sync now** triggers everything at once. Technical messages appear in the developer console (<kbd>Cmd</kbd>+<kbd>Opt</kbd>+<kbd>I</kbd> or <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>I</kbd>) with the prefix `[Peerfold]`.

## Privacy

- Contents, file names and device names cannot be read by the mailbox provider.
- With direct connections, members see each other's IP addresses.
- Peerfold sends no telemetry and contacts no servers other than your mailbox and, if entered, your STUN/TURN servers.

More details, including a privacy notice template for teams (German): [datenschutz.md](datenschutz.md).
