# ORACLE ICT AI — Android App

Same setup as your IM Operations app — a ready-to-build Capacitor Android
project with the ORACLE-ICT AI dashboard wired in, plus your app icon
already generated and placed in all the right folders.

## Fastest path (what worked last time):

1. Create a **new, empty** repo on GitHub, e.g. `oracle-ict-app`
   (don't check "Add a README")
2. In Termux:
   ```
   git config --global --add safe.directory /storage/emulated/0/Download/Oracle_App
   cd ~/storage/downloads
   unzip Oracle_ICT_Android_App.zip -d Oracle_App
   cd Oracle_App
   git init
   git add .
   git commit -m "first upload"
   git branch -M main
   git remote add origin https://github.com/densonhaimbangu-byte/oracle-ict-app.git
   git push -u origin main
   ```
   When it asks for Username/Password: username is `densonhaimbangu-byte`,
   password is a GitHub personal access token with **repo** and **workflow**
   scopes checked (you can reuse your existing token if it still has both).
3. Go to `github.com/densonhaimbangu-byte/oracle-ict-app` → **Actions** tab
4. Wait ~2-3 min for the green checkmark
5. Open that run → **Artifacts** → download **app-debug-apk**
6. Unzip → tap `app-debug.apk` → install

## What's different from last time (already fixed for you)

- The `.github/workflows/build-apk.yml` file is included this time (last
  time it got dropped during the phone unzip — if that happens again,
  recreate it in Termux the same way we did before).
- App icon is already generated in all 5 required sizes
  (`android/app/src/main/res/mipmap-*`), using your uploaded logo.
- The workflow already installs npm packages and runs `npx cap sync android`
  before building — this was the fix that made the IM Operations build
  finally succeed.

## If you edit the dashboard HTML later

Your dashboard source is at `www/index.html`. Edit it, then:
```
git add .
git commit -m "update dashboard"
git push
```
GitHub rebuilds automatically on every push.
