---
name: church-website-login
description: Establish or restore authenticated access to Mercy PCA's Reformation Sites / WordPress administration for church website workflows, including sermons and announcements.
---

# Church Website Login

Use this shared workflow when a church website task needs authenticated administration access. Read it at the point access is needed; callers retain their own content editing, publication, and verification instructions.

## Login and session reuse

1. Use the church domain and administration login URL from Friday's local configuration or the active request. The calling workflow supplies the intended admin destination when known.
2. Reuse an existing authenticated browser session for the configured church site. Open the intended destination and check the current page before logging in again.
3. If authentication is required, use the Reformation Sites credential in Friday's Bitwarden through her existing secure access mechanism. Do not copy credentials, passwords, or session cookies into the repository, conversation, or run records.
4. Complete login, then open the calling workflow's intended destination in the same session. If credential access or an interactive authentication challenge requires user action, report the specific blocker.
5. Verify the intended administration page is accessible, then return to the calling workflow. Successful login alone does not establish permission to edit a particular content area.

## Restricted overview after login

An Editor account may authenticate successfully but land on a restricted custom overview page, such as `wp-admin/admin.php?page=overview-uiptp-27627`, displaying **Sorry, you are not allowed to access this page.** This alone does not mean login failed or that all content areas are inaccessible.

- Open the known destination supplied by the calling workflow directly in the same authenticated session.
- If no destination is known, use available admin navigation or obtain the destination from the user's walkthrough. Do not invent an announcement editor path or use the sermon editor for another content type.
- If the intended page also denies access, report the permission problem. Do not automatically elevate the account role or create another user.

This skill establishes access only. Continue the caller's workflow and its existing authorization requirements before changing or publishing content.
