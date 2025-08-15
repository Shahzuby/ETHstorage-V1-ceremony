# EthStorage V1 — Trusted Setup Ceremony Community Guide

> A clean, step‑by‑step guide to help you contribute to the **EthStorage V1** trusted setup (Groth16) ceremony. This repo is an independent write‑up derived from public instructions and community experience. Always cross‑check with the official EthStorage announcement before running commands.

---

## 📅 Timeline

- **Window:** **Aug 13–22, 2025** — the contribution queue stays open during this period.  
- Your actual turn depends on the global queue. Keep your machine online until your slot is processed.

---

## 🧰 What you need

- **OS:** Ubuntu 22.04
- **Hardware (suggested for VPS):** 4 vCPU, 8-16GB RAM, 30GB+ SSD
- **GitHub account:** 
  - Age ≥ 1 month
  - ≥ 1 public repo
  - Follows ≥ 5 accounts **and** ≥ 1 follower
  - Allow read/write access to **GitHub Gists** (used by the CLI)
- **Internet:** Stable connection (you may sit in queue for hours)
- **Node & npm:** Node.js **v18** and npm **≥ 9.2**

> 💡 Tip: Using a low‑cost VPS for a few days avoids keeping your own PC on the whole time.

---

## 🚀 Quick Start (Ubuntu 22.04)

Update and base tools:
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y curl git build-essential
```

Install Node.js 18 and npm 9.2:
```bash
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs
sudo npm install -g npm@9.2
```

Check versions:
```bash
node -v
npm -v
```

Prepare a temporary working folder:
```bash
mkdir -p ~/trusted-setup-tmp && cd ~/trusted-setup-tmp
```

Install the Phase 2 CLI:
```bash
sudo npm install -g @p0tion/phase2cli
```

Verify:
```bash
phase2cli --version
```

---

## 🔐 Authenticate with GitHub

```bash
phase2cli auth
```
- The CLI will show a code and a URL (https://github.com/login/device).
- Open the URL in a browser, paste the code, and authorize access to **Gists** for the tool.
- Return to the terminal once authorization completes.

---

## 🧾 Join the ceremony queue

It’s best to run inside a screen session so you can disconnect safely:

```bash
screen -S ceremony
```

Start contribution (this registers you in the queue and performs your turn automatically when it arrives):
```bash
phase2cli contribute -c ethstorage-v1-trusted-setup-ceremony
```

When prompted about randomness, you can simply press **Enter** for automatic randomness, or provide your own if you prefer.

> Detach from screen any time with **Ctrl+A**, then **D**.  
> Reattach later with:
```bash
screen -r ceremony
```

---

## ⏳ While you wait

- Keep the machine **online** until your turn is processed.
- If you see very long ETA (e.g., “10 days”), don’t panic; many participants drop off and the queue often advances faster than the worst‑case estimate.

---

## ✅ After your contribution

1. The CLI will finish your turn and produce an **attestation log**.  
2. (Optional) Publish your attestation as a GitHub Gist to prove your participation.
3. **Clean up and remove GitHub permissions** on a VPS when done:

```bash
phase2cli clean
phase2cli logout
cd ~ && rm -rf ~/trusted-setup-tmp
```

---

## 🧩 Troubleshooting

- **`phase2cli` not found** → Re‑install globally: `sudo npm install -g @p0tion/phase2cli`
- **Auth device code expired** → Re‑run `phase2cli auth`
- **Disconnected SSH** → Re‑attach with `screen -r ceremony`; the process continues in the background
- **Slow queue / huge ETA** → Leave the process running; ETA often shrinks as others drop

---

## 🔐 Security notes

- Never run unknown scripts or paste private keys anywhere.  
- If contributing from a VPS, destroy the instance after you finish.  
- Remove the tool’s GitHub access (Gist permissions) once done.

---

## 🙌 Credits

- EthStorage team for the official ceremony and documentation.
- Community contributors for field‑tested tips.
- This guide is a rewritten summary prepared for convenient sharing on GitHub.
  
If you found this helpful, give it a ⭐ and share with others waiting in the queueand and join our telegram channel https://t.me/andhiiTGkamaii Good luck! ✨
