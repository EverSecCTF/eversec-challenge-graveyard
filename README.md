# eversec-challenge-graveyard

Retired CTF challenges from EverSec events — available for practice, self-study, and learning environments.

## What is this?

We build CTF challenges for security events. After a challenge has been used at a conference, we retire it here so it can keep serving a purpose. These challenges are intentionally vulnerable — that's the point. They're designed to teach real-world attack techniques in a safe, isolated environment.

**Do not deploy these in production or expose them to the public internet.** Each challenge contains deliberate security flaws.

## Challenges

| Challenge | Category | Description |
|-----------|----------|-------------|
| **alpha-sqli-basics** | SQL Injection | Login bypass via basic SQL injection |
| **bravo-weak-jwt** | Authentication | JWT with no signature verification → SSTI → sudo privesc |
| **charlie-cookie-tampering** | Session Management | Unsigned base64 cookies → path traversal → SSH key theft → sudo privesc |
| **delta-idor-document-vault** | Access Control | Insecure direct object reference across documents and user profiles |
| **echo-rate-limit-bypass** | API Security | Rate limiting bypass via X-Forwarded-For header spoofing |
| **foxtrot-xss-support-tickets** | XSS / RCE | Stored XSS → admin cookie theft → RCE → SUID privesc |
| **golf-static-analysis-config** | Recon | Exposed source maps, hardcoded keys, and .git directory |
| **hotel-junior-dev-challenge** | Scripting | API key rotation with time constraint — requires scripting to solve |
| **india-nosql-injection** | Injection | NoSQL injection → admin bypass → RCE → sudo privesc |
| **juliet-xxe-injection** | XXE | XXE → file read → SSRF → RCE → sudo privesc |
| **kilo-ssti-template-generator** | SSTI | Jinja2 template injection → RCE → sudo privesc |
| **lima-deserialization-session** | Deserialization | Python pickle deserialization → RCE → sudo privesc |
| **mike-ssrf-to-rce** | SSRF | SSRF → internal service enumeration → RCE |
| **november-drupalgeddon** | CVE | CVE-2018-7600: Drupal 7 unauthenticated RCE |
| **oscar-race-conditions** | Logic Flaws | TOCTOU race condition in coupon redemption |
| **papa-graphql-injection** | GraphQL | Introspection → injection → unauthorized data access |
| **quebec-enumeration** | Recon | 15-flag web enumeration challenge covering common recon techniques |
| **romeo-dfir-memdump** | DFIR | Memory forensics — 3-tier incident response investigation |
| **sierra-filing-cabinet** | Crypto | Classic cryptography chain: Base64, hex, ROT variants, steganography |
| **tango-calculator** | LLM Security | LLM prompt injection in a web calculator |
| **xray-craftcms-rce** | CVE | CVE-2025-32432: CraftCMS unauthenticated RCE via session file injection |
| **yankee-log4shell** | CVE | CVE-2021-44228: Log4j JNDI injection → RCE → sudo privesc |
| **zulu-koa-devtools** | CVE | CVE-2026-27959: Koa hostname bypass + sudo node privesc |
| **cheerio** | Web | Node.js exploitation challenge |
| **coffee** | Web | Node.js/SQLite web challenge |

## How to run a challenge

Each challenge is fully containerized. Most challenges have a single `Dockerfile`; a few use Docker Compose for multi-service setups (e.g., challenges with a database backend).

### Single-container challenges

```bash
cd Challenges/alpha-sqli-basics
docker build -t alpha-sqli-basics .
docker run --rm -p 5001:5001 alpha-sqli-basics
```

Replace the port with whatever the challenge uses (check its README or Dockerfile `EXPOSE`).

### Multi-container challenges (Docker Compose)

Some challenges include a `docker-compose.yml`:

```bash
cd Challenges/xray-craftcms-rce
docker compose up
```

### Finding the right port

Check the challenge's `README.md` or look for `EXPOSE` / `PORTS` in its Dockerfile or docker-compose.yml.

### Stopping a challenge

```bash
# Single container
docker stop <container-id>

# Docker Compose
docker compose down
```

## Solutions

Each challenge directory has a `README.md` with a full solution walkthrough. Don't read it until you've given the challenge a real attempt.

## Flag format

Flags are plain strings without a wrapper — for example: `sql_1nj3ct10n_1s_34sy`

## Notes

- These challenges are retired from active CTF use and may not receive updates.
- Some challenges have multiple flags representing a multi-stage attack chain.
- Challenges run as non-root users internally; privilege escalation to root is often part of the challenge.
- A few challenges require an LLM API key (`tango-calculator`) or specific dependencies — check the individual README.
