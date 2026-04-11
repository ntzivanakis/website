# nikostzivanakis.com — Hugo Static Site

Your personal website, rebuilt as a free static site hosted on GitHub Pages.

---

## What's Inside

```
site/
├── hugo.toml                    # Site config (title, menu, settings)
├── content/
│   ├── _index.md                # Home page (content in layouts/index.html)
│   ├── research.md              # Research page
│   ├── data.md                  # Data resources page
│   ├── consulting.md            # NT Consulting page
│   ├── cv.md                    # Full CV page
│   ├── contact.md               # Contact page
│   └── blog/
│       ├── _index.md            # Blog listing page
│       ├── 2025-03-17-the-silent-wealth-machine.md
│       ├── 2025-03-10-the-illusion-of-tariff-benefits.md
│       └── ... (8 more posts, some need content migrated)
├── layouts/                     # HTML templates
├── static/
│   ├── css/style.css            # All styling
│   └── images/                  # Put your photo here as nikos-tzivanakis.jpg
├── archetypes/blog.md           # Template for new blog posts
└── .github/workflows/hugo.yml   # Auto-deploy on every push
```

---

## Step-by-Step: Making It Live

### Step 1: Install Git (if you don't have it)

- **Mac:** Open Terminal, type `git --version`. If not installed, it will prompt you.
- **Windows:** Download from https://git-scm.com/download/win
- **Linux:** `sudo apt install git`

### Step 2: Create a GitHub Account

Go to https://github.com and sign up if you don't have an account.

### Step 3: Create a New Repository

1. Go to https://github.com/new
2. Name it anything, e.g. `website` or `nikostzivanakis.com`
3. Make it **Public**
4. Do NOT initialise with a README (we already have files)
5. Click **Create repository**

### Step 4: Upload the Site Files

Unzip the downloaded file, then in your terminal:

```bash
cd path/to/unzipped/site
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
git push -u origin main
```

### Step 5: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** → **Pages** (left sidebar)
3. Under **Source**, select **GitHub Actions**
4. The workflow will run automatically on your first push

Your site will be live at `https://YOUR_USERNAME.github.io/YOUR_REPO_NAME/` within 2–3 minutes.

### Step 6: Add Your Photo

1. Download your photo from your current WordPress site
2. Save it as `static/images/nikos-tzivanakis.jpg`
3. Commit and push:
   ```bash
   git add static/images/nikos-tzivanakis.jpg
   git commit -m "Add photo"
   git push
   ```

### Step 7: Point Your Domain

Once the GitHub Pages site is working:

1. In your GitHub repo, go to **Settings** → **Pages**
2. Under **Custom domain**, enter `nikostzivanakis.com` and click Save
3. Update your domain's DNS (at your registrar):
   - Add these **A records** pointing to GitHub's IPs:
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```
   - Add a **CNAME record**: `www` → `YOUR_USERNAME.github.io`
4. Check **Enforce HTTPS** in GitHub Pages settings
5. DNS propagation takes 10–30 minutes. After that, `nikostzivanakis.com` will serve your new site.

### Step 8: Cancel Your WordPress.com Paid Plan

Once the domain is pointing to GitHub Pages and the site is live:
1. Log into WordPress.com
2. Go to **Upgrades** → **Purchases**
3. Cancel your plan
4. If your domain was registered through WordPress.com, transfer it to a cheaper registrar (Cloudflare Registrar charges at-cost, ~$10/year). Instructions: https://wordpress.com/support/move-domain/transfer-domain-registration/

---

## How to Edit Content

### Edit a page

Open any `.md` file in `content/`, change the text, commit, and push. The site rebuilds in ~30 seconds.

You can edit directly on GitHub.com:
1. Navigate to the file (e.g. `content/cv.md`)
2. Click the pencil icon
3. Make your changes
4. Click **Commit changes**

### Add a new blog post

Create a new file in `content/blog/` named like `2026-04-11-my-new-post.md`:

```markdown
---
title: "My New Post Title"
date: 2026-04-11
---

Your content here in plain text or Markdown.

## Subheading

More text. **Bold**, *italic*, [links](https://example.com).
```

Commit and push. It appears on the blog page automatically.

### Migrate remaining blog posts

Several older posts have placeholder content marked `<!-- TODO: Migrate content from WordPress -->`. To fill these in:
1. Visit the post on your current WordPress site
2. Copy the text
3. Paste it into the corresponding `.md` file
4. Commit and push

---

## Costs

| Item | Cost |
|------|------|
| GitHub Pages hosting | Free |
| Hugo static site generator | Free |
| Custom domain (yearly renewal) | ~£10–15/year |
| **Total** | **~£10–15/year** |

Compare with WordPress.com paid plan: £48–300/year.

---

## Installing Hugo Locally (Optional)

If you want to preview changes before pushing:

```bash
# Mac
brew install hugo

# Windows (with Chocolatey)
choco install hugo-extended

# Linux
sudo snap install hugo
```

Then run:
```bash
cd path/to/site
hugo server
```

Open `http://localhost:1313` to see your site locally. Changes update in real time.

---

## Need Help?

If anything is unclear, just ask. The most common issues are:
- **DNS not working:** Wait 30 minutes; check with https://dnschecker.org
- **Site not building:** Check the Actions tab in your GitHub repo for error logs
- **Photo not showing:** Make sure the file is at `static/images/nikos-tzivanakis.jpg`
