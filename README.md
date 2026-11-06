# YIHUI Training Program

A static training-management app for [GitHub Pages](https://yhcoffee.github.io/training-program/), with the 12-shift barista program, trainee shift completions signed by lead initials, three lead competency sign-offs, notes, and editable training content.

## GitHub Pages

Go to **Settings → Pages**, select **Deploy from a branch**, choose **main** and **/(root)**, and save. The entrypoint is `index.html`. If Pages is already configured, publishing updates automatically deploys new commits.

## Firebase Realtime Database

The client is configured for Firebase project `training-program-46853`, database `https://training-program-46853-default-rtdb.firebaseio.com/` and data path `trainingProgram/v1`.

**Authentication is intentionally disabled by request.** In [Firebase Console](https://console.firebase.google.com/project/training-program-46853/database), select **Realtime Database → Rules**. To enable open no-login access, publish the contents of `database.rules.example.json` if there are no other rules you need to preserve. If other rules already exist, merge only `trainingProgram/v1` into them instead of replacing the full rules document.

**Security warning:** `.read: true` and `.write: true` grant every Internet user who knows or discovers the database URL permission to read, change, or delete trainee records. The Firebase API key and GitHub Pages source are public; they are **not** access controls. Do not store sensitive personnel details using these rules. A safer long-term option is authorized staff authentication with restricted database rules.

The app displays a connection error rather than falsely claiming a save when database access is denied. If the cloud is empty, the default training program is seeded on first use; users with existing local progress can import their saved JSON backup through **Data & Backup** (desktop: sidebar bottom; mobile: ellipsis menu). If the browser has old local records on the same origin and Firebase is still empty, the app offers to upload those records instead.

## Backups

Data & Backup lets managers export JSON and restore it. An import replaces the *shared* cloud training data (not just a single browser's data). Keep a JSON backup before major changes.

## Version

v1.5