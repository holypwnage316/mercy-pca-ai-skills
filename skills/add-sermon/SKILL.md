---
name: add-sermon
description: Add a sermon to a Reformation Sites / WordPress church website, including preparing the source audio and creating the sermon entry.
---

# Add Sermon

Use this skill when the user asks to add or publish a sermon to a church website hosted by Reformation Sites.

## Safety and approval

- Do not guess sermon metadata such as date, preacher, passage, title, or series.
- If required metadata is missing or ambiguous, ask the user.
- Do not publish the sermon until the user has explicitly approved the completed sermon entry.
- Never store website credentials, passwords, or session cookies in this skill file.
- Site-specific URLs and credentials should be supplied through local configuration or an authenticated browser session.

## Project repository

This skill is being developed in:

`https://github.com/holypwnage316/mercy-pca-ai-skills`

Keep reusable workflow instructions in this skill file. Keep passwords, authentication secrets, session cookies, and other sensitive credentials out of the repository.

## Required inputs

Collect the following inputs for the completed entry. Audio preparation may begin before all metadata is available, as described below:

- **Sermon title** — the exact title to use on the website.
- **Source audio file** — typically an `.m4a` recording supplied by the user or downloaded from a link the user provides.
- **Sermon date** — used for the final MP3 filename in `YYYY-MM-DD.mp3` format.
- **Scripture passage** — the passage text/reference to place in the sermon body.
- **Speaker** — the preacher/speaker to select from the site's existing Speaker list.
- **Service type** — the appropriate service classification, such as Morning Service.
- **Sermon series** — the existing sermon series to associate with the sermon.

Do not block audio preparation on unrelated metadata once the source is downloaded and the sermon date is confirmed.

Do not infer or invent the sermon title from the audio filename, scripture passage, or other context unless the user explicitly instructs you to do so.

## Persistent run record and conversation checklist

Maintain a durable local run record outside the repository for each sermon. Update it as messages arrive and after each completed operation; reload it when resuming. Keep credentials and authenticated download URLs out of the record.

- For every required input, store its value, source message or reference, and status: **confirmed**, **inferred**, or **missing**. User-supplied values are confirmed unless ambiguous; filename-derived clues remain inferred until confirmed. For example, a filename suggesting `1 Corinthians 16:1–24` does not confirm the passage.
- Reread the full active request thread, including nearby messages and attachments, and reconcile it with the record before asking any follow-up. Never ask again for a value already supplied. If earlier context is inaccessible, state that limitation rather than claiming the user never supplied it.
- Apply explicit corrections to the stored values. Ask only about unresolved conflicts, missing inputs, or inferred values needing confirmation; bundle these questions when practical.
- Store the source and output file paths, audio-processing log, WordPress draft/post ID, edit URL, permalink, uploaded media ID/URL, approval state, and verification results. Record milestones already reported.
- Start audio preparation as soon as the source is downloaded and the date is confirmed, while collecting remaining metadata. Do not publish with required values still inferred or missing.

## Workflow

### 1. Receive and prepare sermon audio

The source sermon audio may be provided by text message, email, or a shared/download link such as Dropbox.

Typical source format: `.m4a`.

Prepare the sermon audio as follows:

1. Download the original audio file.
2. Convert the audio to MP3.
3. Improve spoken-audio quality with conservative processing appropriate for sermon speech:
   - noise reduction
   - EQ for voice clarity
   - normalization
   - light compression
4. Preserve intelligibility and avoid aggressive processing that makes speech sound unnatural.
5. Rename the finished file using the sermon date in this format:

   `YYYY-MM-DD.mp3`

Examples:

- Sermon date July 19, 2026 → `2026-07-19.mp3`
- Sermon date July 26, 2026 → `2026-07-26.mp3`

If the sermon date cannot be determined confidently from the source information, ask the user rather than guessing.

#### Reproducible audio-processing log

Retain the original audio. Record the exact recipe actually used, not just “cleaned and normalized.” Choose conservative settings appropriate to the recording; do not invent settings or measurements after processing.

Record:

- Source filename, duration, container/codec, sample rate, and channels.
- Tool and version, exact command or equivalent processing configuration, filter order and every setting (noise reduction, EQ, compression, normalization), including any processing deliberately skipped and why.
- Target loudness and peak ceiling chosen before processing, plus measured final MP3 integrated loudness (LUFS) and true peak (dBTP). Record both passes if using two-pass normalization.
- Output filename (`YYYY-MM-DD.mp3`), duration, codec, sample rate, channels, and bitrate or VBR quality setting with measured average bitrate.
- Successful decode, comparison of source/output duration with any intentional edits explained, and checks against the chosen loudness/peak targets.
- Brief listening checks at the beginning, middle, and end for intelligibility, clipping, pumping, excessive noise reduction, and accidental truncation. If listening or measurement tools are unavailable, mark the check unverified and disclose this in the review summary; do not claim it passed.

Keep this log with the local run record so the result can be reproduced without repeatedly processing the original.

### 2. Open the sermon administration area

Before creating an entry, check the run record for an existing draft/post ID and resume that entry. If none is recorded, inspect **All Sermons**, including drafts, for the same title and sermon date; use speaker and service type to disambiguate. Resume a clearly matching draft. If a published match or an ambiguous match exists, ask how to proceed rather than creating a duplicate or overwriting it. After an interrupted save, upload, or publish, inspect the current state before retrying.

1. Open the church's Reformation Sites / WordPress administration login.
2. Authenticate using the site's existing secure browser session or approved credential mechanism.
3. If a direct Add New Sermon URL is configured, open it after authentication and confirm the **Add New Sermon** editor appears; then continue to Step 3 below. Otherwise, from the Reformation Websites dashboard, locate the **CONTENT** section in the left navigation.
4. Select **Sermons**.
5. The Sermons submenu opens with options including:
   - All Sermons
   - Add Sermons
   - Series
   - Speakers
   - Service Types
   - Topics
   - Settings
6. Select **Add Sermons** to begin creating the sermon entry.

Use **All Sermons** for duplicate checks or resuming an existing draft. Use **Add Sermons** only when a new entry is needed; taxonomy and settings pages do not create sermon entries.

The Reformation Websites dashboard may also contain other content areas such as Articles, Books, Bulletins, Courses, Events, Ministries, Pages, and Profiles. Use the **Sermons** content area for this workflow.

#### Restricted landing page after login

An Editor account may successfully authenticate but land on a restricted custom overview page, such as `wp-admin/admin.php?page=overview-uiptp-27627`, showing **Sorry, you are not allowed to access this page.** This alone does not establish that the account lacks sermon permissions.

- Open the configured Add New Sermon URL directly in the same authenticated session. For the demonstrated site, the path is `/wp-admin/post-new.php?post_type=cpl_item`, relative to the configured church website URL.
- If **Add New Sermon** opens, continue with sermon metadata entry. The dashboard navigation above can be skipped.
- If the direct sermon editor also denies access, stop and report the permission problem; do not automatically elevate the account role or create another user.

Mercy PCA's Editor account was confirmed to reach the sermon editor through this direct path despite the restricted overview landing page. Keep the church domain, login URL, and full direct editor URL in local configuration rather than hard-coding them into the reusable public skill.

### 3. Enter sermon metadata

On the **Add New Sermon** editor:

1. **Title**
   - Locate the **Add title** field near the top of the page.
   - Enter the exact sermon title supplied as an input.
   - Do not derive or rewrite the title unless the user explicitly asks.

2. **Scripture passage**
   - Enter the supplied scripture passage/reference in the main rich-text editor.
   - Use the passage/reference exactly as supplied unless the user asks for formatting or correction.

3. **Series**
   - Locate the **Series** panel in the right sidebar.
   - Select the supplied existing sermon series.
   - Do not create a new series unless the user explicitly asks.

4. **Speaker**
   - Locate the **Speaker** panel in the right sidebar.
   - Select the supplied existing speaker.
   - Do not create a new speaker unless the user explicitly asks.

5. **Service Type**
   - Locate the **Service Type** panel in the right sidebar.
   - Select the supplied service type.
   - Do not infer Morning Service, Evening Service, or another service type solely from the sermon date/time unless the user has provided enough context or a site-specific configuration explicitly defines the rule.

6. **Sermon date**
   - Verify the date used by this site's sermon listing matches the confirmed sermon date. Use the site's established date control or configuration; the walkthrough has not established the exact control. Do not assume renaming the MP3 sets the displayed date or confuse the sermon date with publication scheduling. Resolve uncertainty before review.

Before proceeding, compare the editor values against the stored confirmed metadata. Save the draft and immediately record its WordPress post ID, edit URL, and permalink. Reuse that draft on subsequent steps or after interruption.

### 4. Upload the prepared sermon audio

1. Scroll to the **Sermon Details** section.
2. Locate **Sermon Audio**.
3. Select **Add or Upload File**.
4. Upload/select the cleaned MP3 created in Step 1, named `YYYY-MM-DD.mp3`.
5. Use the uploaded media file for the Sermon Audio field.
6. Verify that the Sermon Audio field references the intended MP3 before continuing. Record its media ID/URL and save the same draft; reuse the attached media on resume instead of uploading another copy.
7. Do not upload the original `.m4a` when the prepared MP3 is available.

The Sermon Audio field may also accept a URL or embed HTML, but this workflow uses the prepared uploaded MP3 unless the user explicitly requests another source.

### 5. Publish the sermon

1. Scroll back to the top of the **Add New Sermon** editor.
2. Locate the **Publish** panel in the right sidebar.
3. Before publishing, verify the completed entry contains the intended:
   - sermon title and sermon date
   - scripture passage
   - sermon series
   - speaker
   - service type
   - prepared sermon MP3
4. Generate a formal review summary from the stored confirmed values, after comparing them with the saved draft. Include every field above, the draft/post ID and preview or edit link, audio filename, duration, processing/quality-check results, and any unverified checks. Resolve missing or conflicting metadata before presenting the entry as ready.
5. Require a separate, unmistakable approval of that completed summary, such as **Publish it**. Supplying metadata, requesting preparation, or approving audio alone is not publication approval. Record approval and the exact entry/version it covers. If metadata or audio changes afterward, present a revised summary and obtain fresh approval.
6. After approval, click **Publish** once. Confirm the editor changes to **Update** and the entry reports published status; record the post ID and final permalink. If the result is uncertain, inspect that same entry before retrying.

Publishing is an externally visible action. Do not click **Publish** without the required approval unless the user's local configuration explicitly pre-authorizes sermon publishing.

### 6. Verify the public sermon

After the sermon has been published:

1. Open the church's public website.
2. In the main website navigation, open **Sermons**.
3. Select **Recent Sermons**.
4. Locate the newly published sermon in the recent-sermons listing. The listing exposes enough metadata to identify and validate the sermon, including:
   - sermon title
   - speaker
   - sermon series
   - sermon date
   - scripture passage
   - service type
   - a **Listen** control
5. Match the new sermon primarily by the supplied **title and sermon date**. Use the other displayed metadata as additional verification. Do not assume the first item is correct merely because it is newest.
6. Verify the listing matches the intended title, speaker, series, date, scripture passage, and service type.
7. Open the sermon or use the **Listen** control as appropriate to verify that sermon audio is present and accessible.
8. Confirm that the public sermon audio corresponds to the recorded uploaded MP3 and is available without authentication. For Mercy's verification, follow redirects to the final audio URL and verify a normal GET returns **HTTP 200** with **Content-Type: audio/mpeg**. Separately request a small byte range (for example `Range: bytes=0-1023`) and verify **HTTP 206** with a matching **Content-Range**. An `Accept-Ranges` header alone does not prove seeking works. Record the final URL, statuses, content type, and range result. Use bounded/streamed requests to avoid unnecessarily downloading the whole file again. Verify Listen playback as well; HTTP checks do not replace listening.
9. If the public sermon is missing, contains incorrect information, or the audio is unavailable, do not silently consider the task complete. Report the problem to the user and correct it only within the permissions and approval rules of this skill.
10. When the public sermon is correct and accessible, report that the sermon workflow is complete.

## Progress reporting

Report each milestone once: **audio prepared**, **draft ready for review**, and **published and publicly verified**. Persist which milestones were reported so resuming does not repeat them. Send additional updates only for a meaningful blocker, correction, or user-requested status. Keep detailed processing records local and summarize the results for the user.

## Completion criteria

The task is complete only when:

- the source audio has been converted, cleaned, and named correctly;
- the sermon entry contains the supplied metadata;
- the prepared MP3 has been attached;
- the sermon has been published with the required approval; and
- the resulting sermon has been verified on the public website.

## Visual workflow references

These screenshots document the demonstrated workflow. Consult the relevant image when identifying a page or control. Use named UI elements and current page state rather than fixed pixel coordinates; layouts and site configuration may differ. Example sermon metadata in the screenshots is not input for a new sermon.

- [Reformation Websites dashboard](references/reformation-dashboard.png) — CONTENT navigation and Sermons entry.
- [Sermons menu](references/sermons-menu.png) — Add Sermons navigation.
- [Add New Sermon editor](references/add-sermon-editor.png) — title, main editor, Series, and Speaker panels.
- [Sermon Details audio](references/sermon-details-audio.png) — Sermon Audio and Add or Upload File.
- [Publish panel](references/publish-panel.png) — draft state and Publish control; apply the approval rules above.
- [Recent Sermons listing](references/recent-sermons.png) — public metadata and Listen control used for verification.
