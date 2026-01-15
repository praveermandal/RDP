# 🚀 24/7 Turbo RDP Master (GitHub Actions)

This repository provides a high-performance Windows RDP environment that runs 24/7 using GitHub Actions. It includes automated session tracking, performance optimizations, and Telegram notifications.

## ✨ Features
- **24/7 Infinite Loop:** Automatically triggers a new session every 6 hours.
- **Turbo Speed:** Registry tweaks to disable animations and transparency for lower latency.
- **Auto-Cleanup:** Automatically deletes old workflow logs and offline Tailscale devices.
- **Session Tracking:** Tracks your "uptime streak" with session numbers (Session #1, #2, etc.).
- **Telegram Integration:** Sends you the IP address, Hostname, and Session status every 6 hours.
- **Manual Kill Switch:** Stop the loop anytime by creating a simple file.

---

## 🛠️ Setup Instructions

### 1. Tailscale Configuration
1. Create a **Reusable** and **Ephemeral** Auth Key at [Tailscale Keys](https://login.tailscale.com/admin/settings/keys).
2. Generate an **API Key** in the same settings page (needed for auto-cleanup).
3. Note your **Tailnet Name** (top-left of the Tailscale dashboard).

### 2. GitHub Secrets
Go to **Settings > Secrets and variables > Actions** and add the following:

| Secret Name | Description |
| :--- | :--- |
| `TS_AUTHKEY` | Your Tailscale Auth Key (`tskey-auth-...`) |
| `TS_API_KEY` | Your Tailscale API Key (`tskey-api-...`) |
| `TS_TAILNET` | Your Tailnet name (e.g., `yourname.github`) |
| `TELEGRAM_TOKEN` | Your Bot Token from @BotFather |
| `TELEGRAM_TO` | Your Telegram Chat ID |

### 3. Permissions
Go to **Settings > Actions > General**:
- Set **Workflow permissions** to **Read and write permissions**.
- Check **Allow GitHub Actions to create and approve pull requests**.

---

## 🕹️ How to Use

### Start the RDP
Go to the **Actions** tab, select `24x7_Turbo_RDP_Master_V7`, and click **Run workflow**.

### Connecting
1. Wait for the Telegram notification.
2. Connect via your RDP client using:
   - **PC Name:** `cloud-pc-[SessionNumber]`
   - **User:** `runneradmin`
   - **Pass:** `GithubRDP123!`

### Stop the Loop
To stop the 24/7 cycle manually:
1. Create a file named `STOP` in the main folder of this repository.
2. The current session will finish, send a "Terminated" alert to Telegram, and stop.
3. To restart, delete the `STOP` file and run the action again.

---

## ⚠️ Important Notes
- **Storage:** All files on the `C:` drive are wiped every 6 hours. Use cloud storage for important data.
- **Public Repo:** This repo is Public, meaning the code is visible, but your **Secrets** are always safe and hidden.
