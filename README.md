# NorthBridge — M34028 Ethical Hacking engagement environment

This repository is your **authorised test environment** for the module engagement and for
Assessment Item 1. Open it in **GitHub Codespaces** and you get two machines on a private network,
in your browser, with nothing installed on the lab PC:

| Machine | Role | How you reach it |
|---------|------|------------------|
| **workspace** | Your attacker box: `nmap`, `whois`, `dig`, `curl`, `jq` | the terminal you are typing in |
| **northbridge** | The authorised target: NorthBridge web app (OWASP Juice Shop) | hostname `northbridge`, port `3000` |

> **Authorisation — read first.** You are authorised to test **only the `northbridge` target in your
> own Codespace**, plus `scanme.nmap.org` (the Nmap project's published practice host). Scanning or
> testing any other system is out of scope and an offence under the **Computer Misuse Act 1990**.
> No authorisation, no test.

## Launch it

1. Click **Code ▸ Codespaces ▸ Create codespace on main** (or open the Classroom assignment link).
2. Wait for the container to build. When it finishes you'll see a **port 3000** notification — click
   **Open in Browser**. That tab is **your NorthBridge web app**.
3. In the **Terminal** (your attacker box), confirm the target is reachable:

   ```bash
   ping -c1 northbridge
   curl -sI http://northbridge:3000 | head -n1
   ```

## Reconnaissance (Week 1b)

```bash
# Active scan of your authorised target host
nmap -sV northbridge

# Service/version detail saved to the recon/ folder as evidence
nmap -sV -oN recon/northbridge-initial.txt northbridge

# The Nmap project's published practice target (also authorised)
nmap -sV scanme.nmap.org
```

Browser-side recon: open the NorthBridge tab, press **F12**, and use **Network**, **Application**,
and **Console** to study requests, tokens, and client behaviour.

## Save your evidence

Put scan output, notes, and screenshots in **`recon/`**. Commit them — your engagement record is
exactly what Item 1 rewards: timestamps, commands run, and the result of each.

## When you finish

Stop the Codespace (github.com/codespaces ▸ "…" ▸ **Stop**) to preserve your free hours. Your work in
`recon/` is saved with the repo.
