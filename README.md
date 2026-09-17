# 🔐 Networkwalks Cybersecurity — Week 02

Practical cybersecurity lab portfolio covering **Footprinting, Reconnaissance, Maltego, theHarvester and Zenmap/Nmap**.

> **Ethical-use notice:** All active scanning is performed only against systems, networks and assets that I own or have explicit permission to test.

## 📚 Week 02 Modules

| Module | Topic | Status |
|---|---|---|
| W2-PM1 | Footprinting with Multiple Kali Tools | 🟡 In Progress |
| W2-PM2 | Google Hacking Database (GHDB) | ⬜ Pending |
| W2-PM3 | Footprinting with Maltego | ⬜ Pending |
| W2-PM4 | Footprinting & Reconnaissance with theHarvester | ⬜ Pending |
| W2-PM5 | Network Scanning with Zenmap | ⬜ Pending |

## 🛠️ W2-PM1 — Footprinting with Multiple Tools

Tools used in the lab:

- `whois`
- `whatweb`
- `nslookup`
- `curl`
- `wafw00f`
- `dnsrecon`

### Task 1 — WHOIS

**Target:** `networkwalks.com`

Command:

```bash
whois networkwalks.com
```

Initial observed findings:

| Field | Result |
|---|---|
| Registrar | GoDaddy.com, LLC |
| Creation Date | 2019-11-06 |
| Registry Expiry | 2027-11-06 |
| Name Server | NS6135.HOSTGATOR.COM |
| Name Server | NS6136.HOSTGATOR.COM |
| DNSSEC | unsigned |

Evidence will be added under `W2-PM1/evidence/` as the practical progresses.

## 📁 Repository Structure

```text
W2-PM1-Multiple-Kali-Tools/
W2-PM2-GHDB/
W2-PM3-Maltego/
W2-PM4-theHarvester/
W2-PM5-Zenmap/
final-report/
```

## 🎯 Learning Goals

- Understand passive reconnaissance and footprinting.
- Identify publicly exposed domain and DNS information.
- Fingerprint web technologies in an authorized assessment.
- Discover live hosts on an owned/authorized LAN.
- Document findings professionally with reproducible commands and evidence.

**Author:** Siddharth Singh
