# W2-PM1 — Footprinting with Multiple Kali Tools

## Objective

Perform authorized footprinting and reconnaissance using six Kali Linux tools against the designated Networkwalks training target `networkwalks.com`.

## Tools

- `whois`
- `whatweb`
- `nslookup`
- `curl -I`
- `wafw00f`
- `dnsrecon`

---

## Task 1 — WHOIS

### Command

```bash
whois networkwalks.com
```

### Findings

| Field | Result |
|---|---|
| Domain | `networkwalks.com` |
| Registrar | GoDaddy.com, LLC |
| Creation Date | 2019-11-06 |
| Registry Expiry | 2027-11-06 |
| Name Server | `NS6135.HOSTGATOR.COM` |
| Name Server | `NS6136.HOSTGATOR.COM` |
| DNSSEC | Unsigned |

The WHOIS query returned the registration data before a final timeout message.

**Evidence:** `evidence/01-whois-networkwalks.png`

---

## Task 2 — WhatWeb

### Command

```bash
whatweb networkwalks.com
```

### Findings

- Web server: Apache
- IP address: `192.232.216.135`
- CMS: WordPress `7.1`
- WordPress Download Manager: `3.3.58`
- jQuery: `3.7.1`
- Bootstrap: `7.1`
- HTML5 detected
- Google Tag Manager detected
- HTTPS response returned `200 OK`
- Initial HTTP request returned `301 Moved Permanently` to HTTPS
- Page title: `Networkwalks Academy`

**Evidence:** `evidence/02-whatweb-networkwalks.png`

---

## Task 3 — nslookup

### Command

```bash
nslookup networkwalks.com
```

### Findings

- Configured DNS resolver: `10.255.255.254`
- DNS port: `53`
- Resolved IPv4 address: `192.232.216.135`
- Response type: Non-authoritative answer

**Evidence:** `evidence/03-nslookup-networkwalks.png`

---

## Task 4 — curl HTTP Headers

### Command

```bash
curl -I https://networkwalks.com
```

### Findings

- HTTP status: `200 OK`
- Server: Apache
- Content-Type: `text/html; charset=UTF-8`
- WordPress-related cache headers were present
- WordPress REST API information was indicated in the `Link` header
- Referrer-Policy header was present
- Permissions-Policy header was present
- A WordPress Download Manager client cookie was returned

> The original screenshot contains a cookie value. Do not publish the raw cookie value in a public repository.

**Evidence:** `evidence/04-curl-headers.png`

---

## Task 5 — WAF Detection

### Command

```bash
wafw00f networkwalks.com
```

### Finding

WAFW00F identified **ModSecurity (SpiderLabs)** as the detected Web Application Firewall.

- Tool version: `v2.4.2`
- Number of requests: `2`

**Evidence:** `evidence/05-wafw00f-networkwalks.png`

---

## Task 6 — DNSRecon

### Command

```bash
dnsrecon -d networkwalks.com
```

### Findings

The enumeration completed with **8 records found**.

Observed records included:

- SOA: `ns6135.hostgator.com`
- NS: `ns6135.hostgator.com`
- NS: `ns6136.hostgator.com`
- MX: `mail.networkwalks.com` → `192.232.216.135`
- A: `networkwalks.com` → `192.232.216.135`
- TXT: SPF record was observed
- TXT: Google site-verification record was observed
- SRV: `_autodiscover._tcp.networkwalks.com` entries pointing to cPanel email discovery infrastructure

> Redact verification tokens or other sensitive-looking DNS values before publishing raw terminal screenshots publicly.

**Evidence:** `evidence/06-dnsrecon-networkwalks.png`

---

## Conclusion

W2-PM1 demonstrated how multiple reconnaissance tools can build a public-facing profile of an authorized training target. WHOIS and DNS tools exposed registration and DNS information, WhatWeb fingerprinted the web technology stack, curl exposed HTTP response metadata, WAFW00F identified the detected WAF, and DNSRecon enumerated DNS records.

## Ethical Use

This work is for education and authorized security testing only. Do not use these techniques against systems, networks, websites, devices, or accounts without permission.
