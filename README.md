# NFL Line Board

Password-gated weekly NFL line-movement board: spreads, moneylines, totals and player props.

`index.html` is a single self-contained file. Its contents are encrypted with AES-256-GCM;
the key is derived in the browser from the password with PBKDF2-SHA256 (600,000 iterations).
Without the password the file is ciphertext.

## Updating

The unencrypted source is built elsewhere and encrypted before it lands here.
**Only `index.html` belongs in this repository.** If an unencrypted build is ever committed,
it stays in the git history and the password stops meaning anything.

Refreshes run automatically Thursday 8:00 AM ET and Sunday 10:00 AM ET. A launchd agent
(`auto-push.sh` + `com.mike.nfl-autopush.plist`) watches `index.html` and commits and pushes
on change, refusing to act if any file other than `index.html` has changed.
