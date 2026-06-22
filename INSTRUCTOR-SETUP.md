# Instructor setup — NorthBridge lab template (M34028)

This folder IS the student repository. Push it to GitHub once, mark it as a template, and every
student gets an identical one-click Codespace (attacker box + Juice Shop target). Do NOT commit this
file's parent Barin project — only the contents of `lab-northbridge/` go in the GitHub repo.

## 1. Publish the repo (one-off)

From a copy of this `lab-northbridge/` folder on its own:

```bash
gh repo create UoP-London/m34028-northbridge-lab --public --source=. --push
# or create the repo in the GitHub UI and push manually
```

Then on GitHub: **Settings ▸ General ▸ Template repository ✓**, and confirm **Settings ▸ Codespaces**
is enabled.

## 2. Smoke-test it yourself (the dry-run)

1. **Code ▸ Codespaces ▸ Create codespace on main.** Wait for the build (first build pulls the Juice
   Shop image, ~1–2 min).
2. The **port 3000** notification appears → **Open in Browser** → NorthBridge loads. ✅
3. In the terminal:
   ```bash
   ping -c1 northbridge
   nmap -sV northbridge        # expect port 3000 open, Node/Express
   nmap -sV scanme.nmap.org    # outbound works from Codespaces
   ```
4. **Stop** the Codespace afterwards.

## 3. GitHub Classroom (once Faculty approval lands)

Classroom **assignment creation** is the only part gated by the pending GitHub Education Faculty
approval — the template repo above works today on any account.

1. classroom.github.com → create a classroom for M34028, connect your roster.
2. New assignment → **starter code = `m34028-northbridge-lab`** (the template) → enable
   **"students can use Codespaces"**.
3. Share the assignment link via Moodle. Each student gets their own private copy + Codespace.

## 4. Cost

A 4-hour recon lab is a tiny fraction of the **180 free Codespaces hrs/month** every student gets via
the Student Developer Pack, billed to their own account. No org/paid Codespaces billing is needed.
Pin the Juice Shop image version in `docker-compose.yml` so the whole cohort sees the same build.
