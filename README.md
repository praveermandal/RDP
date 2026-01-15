# 🚀 RDP-247 Master Control

This repository runs two parallel Windows RDP sessions (Alpha & Bravo) 24/7 using GitHub Actions and Tailscale.

## 📊 Connection Details
- **User:** `runneradmin`
- **Password:** `GithubRDP123!`
- **Session Duration:** 6 Hours (Auto-cycles)
- **Nodes:** 2 Parallel Instances (Alpha & Bravo)

## 🛠️ How to Control the Loop

### 🛑 Stop the System
To stop the 24/7 loop, create a file in this repository named exactly:
- `STOP` — Kills the entire dual-node loop.
- `STOP_ALPHA` — Stops only the Alpha node.
- `STOP_BRAVO` — Stops only the Bravo node.

### 🔄 Restart the System
1. Delete any `STOP` files you created.
2. Go to the **Actions** tab.
3. Select the **RDP-247** workflow.
4. Click **Run workflow**.

## 🛡️ Required Secrets
Ensure these are set in **Settings > Secrets and variables > Actions**:

| Secret | Description |
| :--- | :--- |
| `TS_AUTHKEY` | Tailscale Auth Key (**Must be set to REUSABLE**) |
| `TELEGRAM_TOKEN` | Your Telegram Bot Token |
| `TELEGRAM_TO` | Your Telegram User/Chat ID |

## ⚠️ Troubleshooting
- **?? in Telegram:** This version uses plain-text headers to prevent character encoding errors.
- **Only 1 Machine visible:** Check your Tailscale Auth Key. It **must** be "Reusable" to allow two machines to log in at the same time.
- **Critical Alert:** If you receive a "CRITICAL ALERT" on Telegram, a node has crashed or GitHub has reclaimed the runner early. The system will attempt to restart automatically at the next cycle.

---
~Praveer Mandal
