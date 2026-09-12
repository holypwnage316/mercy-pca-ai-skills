# Mercy PCA AI Skills

Reusable church website workflows for Friday. These skills document Mercy PCA's Reformation Sites / WordPress processes, with screenshots to help identify the relevant controls.

## Skills

| Skill | Purpose |
| --- | --- |
| [Church website login](skills/church-website-login/SKILL.md) | Reuse or establish an authenticated session through Friday's existing Bitwarden access, including handling a restricted dashboard landing page and end-of-task logout and tab cleanup. |
| [Add sermon](skills/add-sermon/SKILL.md) | Prepare sermon audio, enter metadata, upload the MP3, obtain publication approval, and verify the public sermon and audio. |
| [Update announcements](skills/update-announcements/SKILL.md) | Duplicate an announcement, replace its content, set John Downs as author, publish and verify it, then send the user a Discord/Facebook summary in Telegram. |

| [Upload bulletins](skills/upload-bulletins/SKILL.md) | Read an emailed bulletin PDF, copy page 2 into the website, upload the complete PDF, obtain preview approval, publish, and verify the bulletin. |

The sermon, announcement, and bulletin skills link to the shared login skill when authentication is needed. Keep all four skill folders together so those relative links remain available. Each workflow links to its screenshots at the step where they are useful.

## Announcement inputs and output

Supply Pastor John's current announcement email by forwarding it to Friday's Proton mailbox, or provide the content directly. Friday needs working, authorized mailbox access to read forwarded email; this repository does not configure that connection.

The announcement workflow uses:

- The quote and its attribution.
- The new announcement body, including dates, times, locations, and links.
- Optional interesting links, or “Nothing to share this week.” when none are supplied in the complete current message.
- The update date, defaulting to the day Friday makes the update in the user's local timezone.
- An existing announcement to duplicate, clarified when the source is ambiguous.

The author is always **John Downs**. Friday checks the published entry on the public Articles page, opens **Read More** to verify the full content, and sends a ready-to-copy Discord/Facebook post with the verified link to the user's established private Telegram chat. The user shares that copy on Discord and Facebook.

Forwarding headers, signatures, private correspondence, and incidental email addresses are excluded from public content. An email address is included only when it is intentionally part of an announcement, such as a ministry contact.

Before publishing, Friday compares the website and social drafts with the user's latest corrections and privacy choices. Event locations, site numbers, and private signup links are reviewed for public suitability. Obvious mechanical typos may be corrected without changing meaning; uncertain edits are flagged. Tracking links are replaced with verified public destinations when safely possible.

If the restricted Posts list hides published announcements, the skill provides a fallback through the public Articles page and a verified direct editor link to **Duplicate This**.

## Sermon inputs and output

Supply the source audio (typically an `.m4a` file or download link), exact sermon title, sermon date, scripture passage, speaker, service type, and series. Friday prepares a `YYYY-MM-DD.mp3`, maintains the metadata and processing record, prepares the website entry, and follows the sermon skill's publication approval requirements before verifying the public result.

## Bulletin inputs and output

Email Friday the bulletin PDF and identify the service date and morning/evening service when these are not clear from the source. Friday uses **page 2** for the website's order of worship and sermon notes, and uploads the **complete PDF**. The skill covers duplication, service-date permalink and date fields, both content columns, draft saves, and a website preview sent to Bryan. Publication requires Bryan's explicit approval of that preview.

After publishing, Friday locates the matching block on the public Bulletins page and verifies the full bulletin and PDF. The skill includes eleven walkthrough screenshots and uses the shared logout/tab-cleanup procedure. It has been checked structurally and against the walkthrough; a full live run in Friday's environment remains untested.

## End-of-task browser cleanup

All church content workflows use the shared login skill's cleanup procedure. Friday preserves saved work and resumable references, logs out of WordPress, closes every tab opened for the task, and checks that task admin/editor tabs no longer remain. Unrelated user tabs are preserved.

Cleanup also applies when ending with a saved draft, cancellation, or blocker. The completion report includes verified logout and tab-cleanup status; any failure is reported separately from publication or Telegram delivery. Credentials are filled and submitted without intermediate browser snapshots that could expose their contents.

## Friday's environment

These files are workflow instructions, not a standalone application or an integration installer. Friday needs her existing website browser access and secure credential mechanism. Announcement and bulletin email intake additionally need mailbox access, and Telegram delivery needs a working messaging capability and the user's known private chat.

Keep credentials, cookies, raw email, and private run records outside this repository. The included screenshots illustrate the interface; their dates and content are examples, not inputs for future updates.
