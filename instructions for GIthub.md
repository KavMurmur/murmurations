
---

# GitHub + SSH + Jekyll Setup Guide

---

## 1. Create a GitHub Repository

- Go to [GitHub](https://github.com) and create a new repository.
    
- Name it, add a README if you want.
    
- Choose **Public** or **Private** depending on your needs.
    

---

## 2. SSH Key: What & Why?

**What is it?**  
An SSH key is a pair of cryptographic files:

- **Private key** (keep secret on your computer)
    
- **Public key** (shared with GitHub)
    

**Why?**  
It lets your computer securely prove to GitHub who you are, without needing to type your password every time you push code.

**Do you need one key per repo?**  
No, **one key per computer** is enough for all your GitHub repos.

---

## 3. Generate an SSH Key (one time per computer)

Open your terminal and run:

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

- `-t ed25519` means use a strong, modern encryption type.
    
- `-C` adds a comment with your email for identification.
    

Press Enter to accept default file location (`~/.ssh/id_ed25519`), then set a passphrase (optional but recommended).

---

## 4. Add the SSH Key to your GitHub Account

Show your public key with:

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy the output.

- Go to GitHub → Settings → SSH and GPG keys → New SSH key.
    
- Paste your key, name it something like "My Laptop".
    

---

## 5. Connect your local repo to GitHub via SSH

Inside your local project folder:

```bash
git remote set-url origin git@github.com:username/repo.git
```

(Replace `username` and `repo` with your GitHub username and repository name.)

---

## 6. Push your local Jekyll site to GitHub

Make sure your local files are ready:

```bash
git add .
git commit -m "Initial commit with Jekyll setup"
git push origin main
```

---

## 7. What does pushing mean?

- **Local files** = your Jekyll site on your computer.
    
- **GitHub repo** = online copy of your site’s files.
    
- **Push** = upload changes from local to GitHub.
    

GitHub Pages then **automatically builds and hosts** your site from the repo.

---

## 8. How to update your site?

- Edit your files locally (e.g., add posts or change layouts).
    
- Commit your changes with `git commit`.
    
- Push them with `git push origin main`.
    
- GitHub Pages rebuilds your site automatically.
    

---

## Quick Recap: Commands

```bash
# Generate SSH key (once)
ssh-keygen -t ed25519 -C "your_email@example.com"

# Show public key (copy this)
cat ~/.ssh/id_ed25519.pub

# Change remote URL to SSH (inside repo folder)
git remote set-url origin git@github.com:username/repo.git

# Add all changes
git add .

# Commit changes
git commit -m "Your message"

# Push to GitHub
git push origin main
```

---

cd ~/murmurations
git pull origin main --rebase
git add .
git commit -m "Update $(date +'%Y-%m-%d %H:%M:%S')"
git push origin main