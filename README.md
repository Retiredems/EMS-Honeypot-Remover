<p align="center">
  <img src="assets/icon.png" alt="EMS Honeypot Remover" width="96"/>
</p>

<h1 align="center">EMS Honeypot Remover</h1>

<p align="center">
  <strong>Clean Lists. Protect Your Sender Score.</strong><br/>
  A professional desktop tool that scrubs honeypots, spamtraps, and toxic addresses from bulk email lists — before they poison your deliverability.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%20%7C%20macOS-blue?style=flat-square"/>
  <img src="https://img.shields.io/badge/Detection-7%20Layers-red?style=flat-square"/>
  <img src="https://img.shields.io/badge/Blocklists-300%2B%20Domains-orange?style=flat-square"/>
  <img src="https://img.shields.io/badge/License-Commercial-purple?style=flat-square"/>
  <img src="https://img.shields.io/github/v/release/Retiredems/EMS-Honeypot-Remover?style=flat-square"/>
</p>

---

## What Is EMS Honeypot Remover?

Every bulk email list accumulates dangerous addresses over time — honeypots planted by anti-spam organizations, spamtrap recycled addresses, disposable inboxes, dead domains, role-based aliases, and catch-all servers that silently record every sender who hits them.

Hitting any of these can trigger blacklistings, destroy your domain reputation, and collapse deliverability across your entire sending infrastructure — even for addresses you've been sending to for years.

EMS Honeypot Remover runs your list through a **7-layer detection engine** and separates every address into clean, risky, and flagged buckets — so you send only to real, safe recipients.

Built for **email marketers**, **list brokers**, **bulk senders**, and **deliverability engineers** who need surgical control over list hygiene before a campaign goes out — on any Windows or macOS machine.

---

## Screenshots

<!-- Add screenshots here -->

---

## How Detection Works

EMS Honeypot Remover evaluates every address in sequence through seven detection layers. An address stops at the first layer it fails — no wasted lookups.

| Layer | Check | What Gets Flagged |
|-------|-------|-------------------|
| **1 — Syntax** | RFC-compliant format validation | Malformed addresses (`user@`, `@domain.com`, missing TLD) |
| **2 — Role Prefix** | Match against 60+ known role-based local parts | `abuse@`, `noreply@`, `postmaster@`, `spam@`, `test@`, `admin@` and 55+ others |
| **3 — Typo Domain** | Match against known misspelled provider domains | `gnail.com`, `hotmal.com`, `outlok.com`, `yahooo.com` and 30+ others |
| **4 — Disposable Domain** | Match against 300+ disposable/temporary mail services | Mailinator, Guerrilla Mail, TempMail, YopMail, 10MinuteMail, and hundreds more |
| **5 — Known Trap Domain** | Match against domains operated specifically to catch senders | SpamTrap.ro, ProjectHoneypot.org, Blackhole.postfix.org, and known trap networks |
| **6 — MX Record Check** | Live DNS lookup — does the domain accept email at all? | Dead domains with no MX records |
| **7 — Catch-All SMTP Probe** | Sends a probe to a random address to test if the server accepts everything | Catch-all servers that accept any recipient — a classic spamtrap vector |

---

## Output Files

Every run produces clean, separated output files in your chosen folder.

| File | Contents |
|------|----------|
| `clean.txt` | Addresses that passed all 7 layers — safe to send |
| `risky.txt` | Catch-all domains — server accepts any address, may be a trap |
| `dead.txt` | Domains with no MX records (optional — toggle in Settings) |
| `honeypots.txt` | All flagged addresses (optional — toggle in Settings) |

By default only `clean.txt` and `risky.txt` are written. Enable **Save Honeypots** in Settings to also export the flagged addresses for your records.

---

## Key Features

### 7-Layer Detection Engine
- Role prefix blocklist (60+ patterns): `abuse`, `noreply`, `spam`, `admin`, `postmaster`, `do-not-reply`, `mailer-daemon`, and more
- Typo domain blocklist catches common misspellings that will never deliver
- Disposable mail service blocklist covering 300+ known temporary inbox domains and their CDN-hosted variants
- Known spamtrap domain blocklist covering domains operated specifically to identify and blacklist senders
- Live MX record resolution to identify and optionally remove dead domains before sending
- SMTP catch-all probe using randomized local-part to detect servers that silently accept all recipients

### Multi-Threaded Processing
- Configurable thread count — tune speed vs. DNS server load
- Live progress tracking: total checked, flagged count, percent complete
- Pause / resume mid-run without losing progress
- Per-address isolation — one DNS timeout never stalls the entire queue

### Configurable DNS
- Choose your DNS resolvers (Cloudflare 1.1.1.1 and Google 8.8.8.8 by default)
- Configurable DNS timeout per address
- DNS results are not cached across different runs — every run is a fresh scan

### Clean Output
- Results sorted into separate files, one per verdict category
- Input format is preserved — if your list has duplicates, they are deduplicated before scanning
- Output folder is configurable per run

### Premium Desktop UI
- Dark UI (default) with EMS-red accents
- Clean light theme — toggle from the toolbar
- Splash on launch, in-app activation, sidebar with cross-product links

---

## Installation

### Windows

1. Download `EMS-Honeypot-Remover-Setup.exe` from the [latest release](../../releases/latest)
2. Run the installer — follow the setup wizard
3. A desktop shortcut is created automatically
4. Enter your license key on first launch

> Installs per-user (no admin required). Works on any Windows 10 / 11 desktop, laptop, VPS, or RDP environment.

### macOS

1. Download `EMS_Honeypot_Remover_macOS.zip` from the [latest release](../../releases/latest)
2. Unzip and drag `EMS Honeypot Remover.app` to your Applications folder
3. Right-click → Open on first launch (Gatekeeper bypass for unsigned builds)
4. Enter your license key

---

## Getting a License

EMS Honeypot Remover is a **commercial product**. Licenses are hardware-tied — no cloud check-in required after activation.

👉 **Telegram: [@retiredems](https://t.me/retiredems)**
🤖 **Bot: [@emsmailerbot](https://t.me/emsmailerbot)**

**Pricing — single tier, lifetime only:**

| Plan | Price | Devices |
|------|-------|---------|
| Lifetime | **$100** | Up to 3 PCs |

No monthly. No yearly. One payment, three machines, forever.

---

## How to Get a License Key

1. Open EMS Honeypot Remover — your Hardware ID (HWID) is shown on the Activation screen
2. Tap **Copy** to copy the HWID
3. Open Telegram → [@emsmailerbot](https://t.me/emsmailerbot)
4. Select **🧹 EMS Honeypot Remover** → submit your HWID and name
5. Complete payment → receive your key → paste it into the app

Your license is tied to your machine hardware. Up to **3 PCs per key** are accepted automatically. To move beyond that, contact [@retiredems](https://t.me/retiredems) for a transfer.

---

## Input Format

A plain `.txt` file with one email address per line:

```
alice@example.com
bob@contoso.com
carol@tempmail.com
dave@gnail.com
eve@validcompany.org
```

Duplicate addresses are removed before scanning begins. Each address is evaluated independently — one bad address never affects the verdict for any other.

---

## Settings

| Setting | Default | Description |
|---------|---------|-------------|
| Thread Count | 10 | Concurrent DNS / SMTP workers |
| DNS Timeout | 5 s | Timeout per DNS lookup |
| DNS Servers | 1.1.1.1, 8.8.8.8 | Resolvers to use |
| Remove Dead Domains | On | Flag domains with no MX as `dead` |
| Save Honeypots | Off | Write all flagged addresses to `honeypots.txt` |

---

## System Requirements

| | Windows | macOS |
|-|---------|-------|
| OS | Windows 10 / 11 (64-bit) | macOS 11+ (Intel or Apple Silicon) |
| RAM | 128 MB minimum | 128 MB minimum |
| Disk | 150 MB | 150 MB |
| Network | Required (DNS + SMTP probes) | Required (DNS + SMTP probes) |

> Outbound DNS (port 53) and outbound SMTP (port 25) are required for full scanning. If port 25 is blocked by your ISP, catch-all detection is skipped and addresses are marked clean at layer 6.

---

## Changelog

### v1.0.0 — May 2026

- Initial public release
- 7-layer detection engine: syntax, role prefix, typo domain, disposable domain, trap domain, MX check, SMTP catch-all probe
- 300+ disposable and spamtrap domains in the built-in blocklist
- 60+ role-based prefixes blocked by default
- Multi-threaded worker pool with pause / resume support
- Configurable DNS resolvers and timeout
- Optional dead-domain removal and honeypot export
- Hardware-tied lifetime license — up to 3 PCs per key
- Dark / light theme, premium PyQt6 UI
- Splash screen on launch with in-app activation flow

---

## Other EMS Tools

| Tool | Description |
|------|-------------|
| [EMS Mailer](https://github.com/Retiredems/Ems-Mailer) | Bulk email sending — SMTP, rotating accounts, templates |
| [EMS Mail Fetcher](https://github.com/Retiredems/EMS-Mail-Fetcher) | Bulk IMAP / POP3 / OAuth account tester and email archiver |
| [EMS Email Sorter](https://github.com/Retiredems/EMS-Email-Sorter) | Sort bulk email lists by mail provider using live MX/SPF lookups |
| [EMS Country Sorter](https://github.com/Retiredems/EMS-Country-Sorter) | Sort bulk email lists by country — TLD + DNS + GeoIP detection |
| [EMS Cookie Harvester](https://github.com/Retiredems/EMS-Cookie-Harvester) | Extract email addresses from Office 365 session cookies via IMAP XOAUTH2 |
| [EMS Office365 Verifier](https://github.com/Retiredems/EMS-Office365-Verifier) | Classify Office 365 email lists by federation type |

---

## Support

Open an issue on GitHub for bug reports and feature requests. For licensing or transfers, message [@retiredems](https://t.me/retiredems) on Telegram.

---

<p align="center">
  Built with precision by <strong>Retiredems</strong> &nbsp;·&nbsp; Powered by PyQt6
</p>
