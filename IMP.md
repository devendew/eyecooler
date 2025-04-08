# Document


# 🚀 Automate Versioning & Releases with Changesets for Your VS Code Extension

This guide shows how to use [Changesets](https://github.com/changesets/changesets) to manage **semantic versioning**, **changelogs**, and **Git tagging** for your VS Code theme or extension.

It integrates smoothly with tools like `vsce` and GitHub Actions for a fully automated release pipeline.

---

## 📦 Step 1: Install Changesets

Install the CLI as a development dependency:

```bash
npm install --save-dev @changesets/cli
```

---

## ⚙️ Step 2: Initialize Changesets

Set up the changesets configuration and folder:

```bash
npx changeset init
```

This creates a `.changeset/` folder and a config file.

---

## 📝 Step 3: Create a Changeset

Run the following command every time you make a significant update:

```bash
npx changeset
```

You'll be prompted to:

- Select the package to update (usually just one if it's a single extension)
- Choose the version bump: `patch`, `minor`, or `major`
- Write a short changelog message

This will generate a markdown file in `.changeset/`, like:

```text
.changeset/
├── update-colors.md
```

This file tracks your changes until you publish.

---

## 📈 Step 4: Apply Version Bump and Generate Changelog

Once you're ready to release a new version:

```bash
npx changeset version
```

This will:

- Update `package.json` version
- Generate or append entries in `CHANGELOG.md`
- Stage these changes for commit

---

## 🚀 Step 5: Tag and Publish

To publish to the VS Code Marketplace:

```bash
npx changeset tag
vsce publish
```

This will:

- Commit the version bump and changelog
- Create a Git tag (e.g., `v1.2.0`)
- Push the commit and tag to your remote
- Publish the updated extension using `vsce`

> 💡 You can also use `vsce publish minor` or `vsce publish patch` if not using changesets.

---

## 📁 Project Structure Example

```text
.
├── .changeset/
│   └── update-icons.md
├── CHANGELOG.md
├── package.json
├── extension/
├── README.md
```

---

## 🤖 Optional: Automate with GitHub Actions

You can fully automate versioning and publishing with GitHub Actions. It can:

- Detect changesets in pull requests
- Auto-bump versions
- Generate changelogs
- Create Git tags
- Publish to the VS Code Marketplace

> ✅ Want a pre-built `.github/workflows/release.yml` file? Let us know!

---

## 🧪 Bonus Commands

### Publish with a specific version

```bash
vsce publish 1.4.0
```

### Create an annotated Git tag manually

```bash
git tag -a v1.4.0 -m "New sidebar styling and contrast improvements"
git push origin v1.4.0
```

---

## ✅ Summary Table

| Task                        | Command                                           |
|-----------------------------|---------------------------------------------------|
| Install Changesets          | `npm install --save-dev @changesets/cli`         |
| Initialize Changesets       | `npx changeset init`                              |
| Create a Changeset          | `npx changeset`                                   |
| Apply Version + Changelog   | `npx changeset version`                           |
| Tag and Publish Extension   | `npx changeset tag && vsce publish`              |

---

## 🎨 Enjoy Clean Releases

With Changesets, you'll never forget a version bump or changelog again.  
Perfect for managing VS Code themes and extensions with ease and professionalism.
