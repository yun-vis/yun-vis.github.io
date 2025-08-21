You're describing a setup where you want to:

* Create a **new Git repository** based on an **existing one**.
* Still be able to **pull updates from the original repository**.

This is commonly done by **forking** a repository manually and then setting the **original repository as a remote called `upstream`**.

Here’s how you can do it step by step:

---

## ✅ Step-by-Step Instructions

### 1. **Clone the original repository**

```bash
git clone https://github.com/original-user/original-repo.git
cd original-repo
```

### 2. **Rename the `origin` remote (optional)**

If you want to keep using the original repo as `origin`, skip this step.

If you're going to **push to a new repository** (your own), it's better to rename `origin` to `upstream`:

```bash
git remote rename origin upstream
```

You can now pull from the original using:

```bash
git pull upstream main
```

> Replace `main` with whatever the default branch is (often `master` or `main`).

---

### 3. **Create a new repository on GitHub / GitLab / etc.**

Create a new empty repo on your Git provider (e.g., `https://github.com/your-user/my-new-repo.git`).

---

### 4. **Add your new repo as `origin`**

```bash
git remote add origin https://github.com/your-user/my-new-repo.git
```

To verify:

```bash
git remote -v
```

You should see:

```
origin    https://github.com/your-user/my-new-repo.git (fetch)
origin    https://github.com/your-user/my-new-repo.git (push)
upstream  https://github.com/original-user/original-repo.git (fetch)
upstream  https://github.com/original-user/original-repo.git (push)
```

---

### 5. **Push to your new repository**

Make sure all branches are pushed to your new `origin`:

```bash
git push -u origin main
```

---

## 🧪 Pulling Updates from the Original Repo

Whenever you want to sync updates from the original repository:

```bash
git fetch upstream
git merge upstream/main
```

Or, if you're using rebase:

```bash
git fetch upstream
git rebase upstream/main
```

---

## ✅ Summary

| Task                          | Command                             |
| ----------------------------- | ----------------------------------- |
| Clone original                | `git clone ...`                     |
| Rename `origin` to `upstream` | `git remote rename origin upstream` |
| Add your own repo             | `git remote add origin ...`         |
| Pull from original            | `git pull upstream main`            |
| Push to new repo              | `git push -u origin main`           |

---

Let me know if you want a script to automate this.

