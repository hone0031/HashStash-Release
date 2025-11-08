# Password Manager (PyQt5)

Simple password manager using PyQt5 GUI. On first run the program will generate an Authentication key (shown once) and prompt the user to create a master password. The auth key and master password are salted+hashed; stored passwords are encrypted using AES-GCM with a key derived from the master password.


# HashStash — End‑User Guide

This README contains concise instructions for end users: how to install, run, update, back up and restore your data, and troubleshoot common problems.

## Install & run (Windows — released builds)

1. Download the latest release ZIP from the official release page.
2. Extract the ZIP to a folder you control (for example `C:\Program Files\HashStash` or a folder under your user profile).
3. Double‑click `HashStash.exe` to start the application.

On first run you will be asked to create a Master Password and will be shown a one‑time Recovery token. Copy or securely store that token — it is shown only once.

## Automatic updates

- When a new release is available, HashStash will prompt and run the built‑in updater which verifies the downloaded package before applying it.
- To update manually: download the new release ZIP, extract to a temporary folder, close HashStash, and replace the application folder with the new files.

## Where your data is stored

Default data directory (Windows):

	%USERPROFILE%\Documents\HashStash

Important files:
- `vault.bin` — your encrypted password vault
- `dek.bin` — encrypted Data Encryption Key (wrapped to your Master Password)
- `recovery.json` — optional recovery metadata
- `backups/` — rotated timestamped backups created by the app

These files are sensitive; keep backups encrypted and do not share them unencrypted.

## Back up and restore

Recommended backup steps:
1. Close HashStash.
2. Copy `%USERPROFILE%\Documents\HashStash\backups` and the current `vault.bin` + `dek.bin` to encrypted storage (external drive, encrypted cloud storage, etc.).
3. Verify backup integrity before deleting local copies.

Restore steps:
1. Close HashStash.
2. Copy your backup `vault.bin` and `dek.bin` back into `%USERPROFILE%\Documents\HashStash`.
3. Start HashStash and log in with the Master Password that matches the restored DEK.

If the Master Password used to protect the DEK has changed since the backup was created, restore the matching `dek.bin` for that password or use your saved recovery token.

## Recovery token

The recovery token shown on first run allows you to regain access if you forget your Master Password (only if you saved it). Store it securely — treat it like a high‑value secret.

## Troubleshooting

- App won't start: try running `HashStash.exe` as your regular user. If blocked by antivirus, whitelist the extracted folder.
- Cannot unlock vault after restore: ensure `vault.bin` and `dek.bin` are from the same backup and you are using the correct Master Password.
- Update failed: the updater keeps a backup and will try to roll back. If rollback fails, restore from your manual backup.

If problems persist, collect the small log file from the app folder or `%LOCALAPPDATA%\HashStash\logs` and contact the person or team who provided the release.

## Security reminders

- HashStash encrypts your vault locally. The security of your data depends on the strength and secrecy of your Master Password and backup handling.
- Never store your Master Password or recovery token in plaintext on shared or cloud locations without additional encryption.

---

Developer notes and build/test instructions are intentionally omitted from this README.
