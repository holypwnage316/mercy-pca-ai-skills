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

Before beginning the workflow, obtain at minimum:

- **Sermon title** — the exact title to use on the website.
- **Source audio file** — typically an `.m4a` recording supplied by the user or downloaded from a link the user provides.
- **Sermon date** — used for the final MP3 filename in `YYYY-MM-DD.mp3` format.
- **Scripture passage** — the passage text/reference to place in the sermon body.
- **Speaker** — the preacher/speaker to select from the site's existing Speaker list.
- **Service type** — the appropriate service classification, such as Morning Service.
- **Sermon series** — the existing sermon series to associate with the sermon.

Additional required sermon metadata will be added to this list as the workflow is documented.

Do not infer or invent the sermon title from the audio filename, scripture passage, or other context unless the user explicitly instructs you to do so.

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

### 2. Open the sermon administration area

1. Open the church's Reformation Sites / WordPress administration login.
2. Authenticate using the site's existing secure browser session or approved credential mechanism.
3. From the Reformation Websites dashboard, locate the **CONTENT** section in the left navigation.
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

Do not choose **All Sermons**, **Series**, **Speakers**, **Service Types**, **Topics**, or **Settings** when the task is to create a new sermon.

The Reformation Websites dashboard may also contain other content areas such as Articles, Books, Bulletins, Courses, Events, Ministries, Pages, and Profiles. Use the **Sermons** content area for this workflow.

For Mercy PCA, the current login flow begins at the church WordPress login page and redirects into the Reformation Websites administration interface. This site-specific URL should remain local configuration and should not be hard-coded into the reusable public skill.

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

Before proceeding, verify that the title, scripture passage, speaker, service type, and sermon series match the supplied sermon information.

### 4. Upload the prepared sermon audio

1. Scroll to the **Sermon Details** section.
2. Locate **Sermon Audio**.
3. Select **Add or Upload File**.
4. Upload/select the cleaned MP3 created in Step 1, named `YYYY-MM-DD.mp3`.
5. Use the uploaded media file for the Sermon Audio field.
6. Verify that the Sermon Audio field references the intended MP3 before continuing.
7. Do not upload the original `.m4a` when the prepared MP3 is available.

The Sermon Audio field may also accept a URL or embed HTML, but this workflow uses the prepared uploaded MP3 unless the user explicitly requests another source.

### 5. Publish the sermon

1. Scroll back to the top of the **Add New Sermon** editor.
2. Locate the **Publish** panel in the right sidebar.
3. Before publishing, verify the completed entry contains the intended:
   - sermon title
   - scripture passage
   - sermon series
   - speaker
   - service type
   - prepared sermon MP3
4. Obtain explicit approval from the user before making the sermon public.
5. After approval, click **Publish**.

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
8. Confirm that the public sermon audio corresponds to the newly published sermon and is available to visitors.
9. If the public sermon is missing, contains incorrect information, or the audio is unavailable, do not silently consider the task complete. Report the problem to the user and correct it only within the permissions and approval rules of this skill.
10. When the public sermon is correct and accessible, report that the sermon workflow is complete.

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
