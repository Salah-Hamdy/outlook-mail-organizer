# Mail Organizer — Setup Guide

## 5-Step Setup (15 minutes)

### Step 1: Create GitHub Account (skip if you have one)
Go to https://github.com and sign up. Free account is all you need.

### Step 2: Create Repository & Upload Files
1. Go to https://github.com/new
2. Repository name: `outlook-mail-organizer`
3. Set to **Public** (required for GitHub Pages free tier)
4. Click **Create repository**
5. Click **"uploading an existing file"** link
6. Drag and drop ALL files into the upload area:
   - `taskpane.html`
   - `manifest.xml`
   - `assets/` folder (with all icon PNGs inside)
7. Click **Commit changes**

### Step 3: Enable GitHub Pages
1. In your repo, go to **Settings** tab (top menu)
2. Scroll down to **Pages** in the left sidebar
3. Under "Source", select **Deploy from a branch**
4. Branch: select **main**, folder: **/ (root)**
5. Click **Save**
6. Wait 1-2 minutes. Your site will be live at:
   `https://YOUR_USERNAME.github.io/outlook-mail-organizer/`
7. Visit that URL in your browser to confirm it works

### Step 4: Update the Manifest
1. In your repo on GitHub, click on `manifest.xml`
2. Click the pencil icon (Edit)
3. Use **Ctrl+H** (Find & Replace):
   - Find: `YOUR_GITHUB_USERNAME`
   - Replace: your actual GitHub username
4. Click **Commit changes**
5. **Download** the updated `manifest.xml` to your computer
   (click the file → click the download icon)

### Step 5: Sideload in Outlook
1. Open **Classic Outlook for Windows**
2. Click **Get Add-ins** on the Home ribbon
   (or File → Manage Add-ins)
3. Click **My add-ins** (left sidebar)
4. Scroll to **Custom add-ins**
5. Click **+ Add a custom add-in** → **Add from file...**
6. Select the `manifest.xml` you downloaded in Step 4
7. Click **Install**

**Done!** You'll see an **"Organize"** button on the ribbon.

---

## Using the Add-in

1. **Select** any email in your Inbox
2. Click **Organize** on the ribbon → task pane opens on the right
3. **Pin it** (click the pin icon at the top-right of the pane) so it stays open
4. Click any **folder button** to move the email + full conversation thread
5. Use **flag buttons** for follow-up reminders
6. Use the **search bar** to quickly find folders
7. Toggle **"Move entire conversation thread"** on/off as needed

---

## Adding or Editing Folders Later

1. Go to your repo on GitHub
2. Click `taskpane.html` → pencil icon (Edit)
3. Find the section where you want to add a folder
4. Add a line like:
   ```html
   <button class="folder-btn" onclick="moveToFolder('Projects/NewProject')"><span class="folder-icon">📁</span>NewProject</button>
   ```
5. Commit changes
6. Wait 1-2 minutes for GitHub Pages to update
7. Close and reopen the task pane in Outlook — changes appear automatically

---

## File Structure
```
outlook-mail-organizer/
├── manifest.xml          ← tells Outlook where the add-in lives
├── taskpane.html         ← the entire add-in UI + logic (single file)
└── assets/
    ├── icon-16.png       ← ribbon icons
    ├── icon-32.png
    ├── icon-64.png
    ├── icon-80.png
    └── icon-128.png
```

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| "Organize" button doesn't appear | Wait 2 min after sideloading. Restart Outlook if needed. |
| Task pane shows blank/error | Visit your GitHub Pages URL in a browser first to confirm it loads |
| "Folder not found" error | Folder name in the button must match your Outlook folder name exactly |
| Auth/token error | Your M365 account must be Exchange Online (not on-premise Exchange) |
| Changes to taskpane.html not showing | GitHub Pages can take 1-2 min to update. Hard-refresh the task pane. |

---

## Note on Security
The repo is public (required for free GitHub Pages), but the add-in itself doesn't store or expose any email data. It only runs locally within your Outlook session using your existing Microsoft auth token. The HTML file contains only the UI layout and folder names — no credentials, no sensitive data.
