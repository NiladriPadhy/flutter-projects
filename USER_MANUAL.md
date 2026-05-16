# Flutter Projects - User Manual

This guide explains how to work with the **flutter-projects** repository, which contains 3 Flutter apps (app1, app2, app3) as Git submodules.

---

## What is a Git Submodule?

A submodule is a Git repo inside another Git repo. Each app (app1, app2, app3) is its own separate repo, but they are all linked together inside the **flutter-projects** parent repo.

---

## 1. Clone the Project (First Time Setup)

To download everything (parent repo + all 3 apps):

```bash
git clone --recurse-submodules https://github.com/NiladriPadhy/flutter-projects.git
```

Then go into the folder:

```bash
cd flutter-projects
```

You will see:

```
flutter-projects/
├── app1/    (Flutter app 1)
├── app2/    (Flutter app 2)
├── app3/    (Flutter app 3)
└── .gitmodules
```

---

## 2. If You Already Cloned Without Submodules

If you cloned without `--recurse-submodules` and the app folders are empty, run:

```bash
git submodule init
git submodule update
```

---

## 3. Pull Latest Changes (Update Everything)

To get the latest code for the parent repo AND all apps:

```bash
git pull
git submodule update --remote
```

---

## 4. Work on a Specific App

Go into the app folder:

```bash
cd app1
```

Make your changes, then save them:

```bash
git add .
git commit -m "Your message about what you changed"
git push
```

Then go back to the parent folder and update the submodule reference:

```bash
cd ..
git add app1
git commit -m "Updated app1 to latest version"
git push
```

> **Important:** After pushing changes inside an app, always go back to the parent folder and commit + push there too. This tells the parent repo which version of the app to use.

---

## 5. Run a Flutter App

Go into any app folder and run it:

```bash
cd app1
flutter run
```

---

## 6. Add a New App as a Submodule

If you want to add another Flutter app (e.g., app4):

**Step 1:** Create the app and push it to GitHub as a separate repo.

**Step 2:** From the parent folder, add it as a submodule:

```bash
cd flutter-projects
git submodule add https://github.com/NiladriPadhy/app4.git app4
git commit -m "Added app4 as submodule"
git push
```

---

## 7. Remove a Submodule

If you want to remove an app (e.g., app3):

```bash
git submodule deinit app3
git rm app3
git commit -m "Removed app3"
git push
```

---

## 8. Check Status of All Apps

To see which apps have new changes:

```bash
git submodule status
```

---

## 9. Switch GitHub Account (if needed)

To log in with a different GitHub account:

```bash
gh auth login --web
```

Follow the steps in the browser to log in.

To check which account is active:

```bash
gh auth status
```

---

## Quick Reference Table

| Task | Command |
|------|---------|
| Clone everything | `git clone --recurse-submodules https://github.com/NiladriPadhy/flutter-projects.git` |
| Pull latest updates | `git pull && git submodule update --remote` |
| Go into an app | `cd app1` |
| Save changes in app | `git add . && git commit -m "message" && git push` |
| Update parent after app change | `cd .. && git add app1 && git commit -m "Updated app1" && git push` |
| Check submodule status | `git submodule status` |
| Add new submodule | `git submodule add <repo-url> <folder-name>` |
| Remove a submodule | `git submodule deinit <name> && git rm <name>` |
| Run Flutter app | `cd app1 && flutter run` |

---

## GitHub Links

- **Parent Repo:** https://github.com/NiladriPadhy/flutter-projects
- **App 1:** https://github.com/NiladriPadhy/app1
- **App 2:** https://github.com/NiladriPadhy/app2
- **App 3:** https://github.com/NiladriPadhy/app3
