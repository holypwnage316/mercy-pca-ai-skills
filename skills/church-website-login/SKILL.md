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
4. Inspect the empty login form and identify its fields and submit control before entering credentials. Fill and submit credentials as one uninterrupted sequence without taking an intermediate screenshot, browser snapshot, DOM/accessibility dump, or field-value read. Use a secure input mechanism that does not echo secrets in tool output; if the available tool automatically snapshots filled fields and cannot suppress that output, use a safer existing credential/autofill mechanism or request user-assisted login. Never print or log credential values.
5. Complete login, then open the calling workflow's intended destination in the same session. If credential access or an interactive authentication challenge requires user action, report the specific blocker.
6. Verify the intended administration page is accessible, then return to the calling workflow. Successful login alone does not establish permission to edit a particular content area.

Only inspect or snapshot the post-login page once it is clear of filled credentials. If submission fails and leaves credentials populated, clear the sensitive fields without reading them before obtaining diagnostic page state. If the tool cannot do this without exposing values, report the blocker rather than capturing the filled form.

## Restricted overview after login

An Editor account may authenticate successfully but land on a restricted custom overview page, such as `wp-admin/admin.php?page=overview-uiptp-27627`, displaying **Sorry, you are not allowed to access this page.** This alone does not mean login failed or that all content areas are inaccessible.

- Open the known destination supplied by the calling workflow directly in the same authenticated session.
- If no destination is known, use available admin navigation or obtain the destination from the user's walkthrough. Do not invent an announcement editor path or use the sermon editor for another content type.
- If the intended page also denies access, report the permission problem. Do not automatically elevate the account role or create another user.

Continue the caller's workflow and its existing authorization requirements before changing or publishing content. Returning authenticated access to the caller is not the end of the overall task; perform the cleanup below when that task ends.

## End-of-task logout and browser cleanup

At task start, record the browser/profile and existing tab IDs. Track every tab opened for the task, including popups, redirects into new tabs, public verification pages, and external link checks. Reuse this record when resuming instead of inferring ownership from a page title alone.

When the overall task is complete, cancelled, or being ended with a blocker:

1. Preserve required results and resumable state first: confirm any intended draft save, and record the post ID, edit URL, public URL, and remaining work outside the repository. Do not discard unsaved edits silently or publish merely to close a tab.
2. Log out of WordPress using its authenticated logout control and complete any logout confirmation. Verify the session has ended, for example by observing the login page or a login requirement on an admin page. Closing tabs alone does not establish logout. If logout cannot be confirmed, report that limitation and still close the task's tabs.
3. Close every tab opened for the task in Chrome or any other browser used, including the logout page, admin/editor pages, public pages, and link-check tabs. Close a pre-existing church admin/editor tab too if it was reused for this task, after preserving work. Do not close unrelated user tabs or quit the whole browser indiscriminately.
4. Inspect the remaining tab inventory and verify no task-opened tabs or church admin/editor tabs used by the task remain. If other pre-existing church admin/editor tabs remain, report them rather than claiming none remain or closing unrelated work without authorization.
5. Include logout and tab-cleanup status in the final completion report. Distinguish verified cleanup from failed or unavailable checks; a successful publication does not imply successful cleanup.

An active pause for a user response is not task completion. When the calling workflow provides an authenticated preview link that the reviewer needs during approval, preserve the saved draft and resumable references and keep only the required authenticated task and preview tabs open. Do not log out merely because the current agent run ends. Perform cleanup after approval and completion, explicit cancellation/abandonment, or a blocker that ends the task. If security requires ending the session earlier, save the work, explain that the preview may require a fresh login, then clean up.
