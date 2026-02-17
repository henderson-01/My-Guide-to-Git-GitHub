# 🚀 My No-Stress Guide to Git & GitHub (Ubuntu Edition)

This guide ensures you can use Git on your Ubuntu desktop without password prompts, privacy leaks, or terminal headaches.

## 🛡️ Step 1: Verification & Privacy

Before we start, let's make sure your computer is ready and your email is hidden.

1. **Check if Git is installed:** Open your terminal (**Ctrl+Alt+T**) and type:
```bash
git --version

```


*If it shows a version number, you're good! If not, run: `sudo apt update && sudo apt install git -y`
2. **Hide your Email on GitHub:** * Go to **Settings** → **Emails**.
* Check **"Keep my email addresses private"** and **"Block command line pushes that expose my email."**


3. **Copy your "Noreply" Email:** GitHub will show a specific address in that menu, like `12345678+username@users.noreply.github.com`. **Save this for Step 2.**

---

## 🛠️ Step 2: Global Setup (One-Time Only)

Run these in your terminal to identify yourself and match GitHub's naming convention:

```bash
# 1. Set your GitHub Username
git config --global user.name "YourGitHubUsername"

# 2. Set your Private Email (Paste the address from Step 1)
git config --global user.email "12345678+username@users.noreply.github.com"

# 3. Ensure your default branch is 'main'
git config --global init.defaultBranch main

```

---

## 🔑 Step 3: SSH Key (The "No-Password" Magic)

This lets Ubuntu talk to GitHub securely without you typing a password every time.

1. **Generate the key:**
```bash
ssh-keygen -t ed25519 -C "your-noreply-email@users.noreply.github.com"

```


2. **The "Enter" Trick:** When it asks for a file location or passphrase, **press ENTER for all three prompts** (leave them blank).
3. **Copy the key to your clipboard:**
```bash
cat ~/.ssh/id_ed25519.pub

```


*Highlight the output starting with `ssh-ed25519` and copy it.*
4. **Add to GitHub:** Go to **Settings** → **SSH and GPG keys** → **New SSH Key**. Give it a title (e.g., "Ubuntu Desktop") and paste the key.
5. **The Critical Test:**
```bash
ssh -T git@github.com

```



> [!IMPORTANT]
> When you run the test above for the first time, the terminal will ask:
> `Are you sure you want to continue connecting (yes/no/[fingerprint])?`
> **You must type `yes` and press Enter.** If it says *"Hi [Username]!"*, you are officially connected!

---

## 📂 Step 4: Daily Workflow

The commands you’ll use in your project folder every day:

| Command | What it does |
| --- | --- |
| `git status` | **The Check-in:** See what you've changed. |
| `git add .` | **The Stage:** Get changes ready to save. |
| `git commit -m "msg"` | **The Save:** Create a local snapshot. |
| `git push` | **The Upload:** Send your saves to GitHub. |
| `git pull` | **The Sync:** Download the latest changes from GitHub. |

---

## ☁️ Step 5: Connecting to GitHub

### To Upload a New Local Project:

1. **Navigate to your project:**
```bash
cd ~/Documents/your-project-folder

```


2. **Initialize & Save locally:**
```bash
git init
git add .
git commit -m "initial commit"
git status

```


> 💡 **Why run status here?** If it says *"nothing to commit, working tree clean"*, it means your "Snapshot" was successful. You are now ready to send it to the cloud!


3. **Link and Push:** (Copy the **SSH link** from your new GitHub repo page). On GitHub, click on the plus icon, top right side. Then click on the new repository. This will take you through to a separate page. Name your repository. I find it best practice to keep it the same name as the folder that you're pushing. Then click the create. And this will take you through to a separate page where it will display the origin SSH link. Click on the SSH link, copy that and follow the next steps. 
```bash
# Connect local to remote (Replace with your actual SSH link)
git remote add origin git@github.com:Username/RepositoryName.git

# Push to GitHub for the first time
git push -u origin main

```



---

## 🚀 Pro-Tip: The "One-Word" Save

If you hate typing three commands every time, you can create a shortcut (alias).

1. Run: `nano ~/.bashrc`
2. Scroll to the bottom and paste:
```bash
alias gsave='git add . && git commit -m "update" && git push'

```


3. Save (**Ctrl+O, Enter**) and Exit (**Ctrl+X**).
4. Refresh your terminal: `source ~/.bashrc`

**Now, you can just type `gsave` to stage, commit, and push everything at once!**

---
---

## Disclaimer

This project is provided "as-is" without any warranty of any kind. I am not responsible for any issues, data loss, or "explosions" (code-related or otherwise) that may occur from using this software. **Use it at your own risk.**


