---
name: update-announcements
description: Create updated announcements on Mercy PCA's church website by duplicating an existing announcement post as a draft. Use the shared church login workflow, replace the announcement content, set John Downs as author, publish and verify the updated post, then provide a shareable Discord/Facebook summary.
---

# Update Announcements

## 1. Open the Posts list

When administration access is needed, read and follow [Church Website Login](../church-website-login/SKILL.md). Use the same Reformation Sites account and session as the sermon workflow, with the Posts list as the intended destination.

The user-confirmed destination is [Mercy PCA Posts](https://mercypca.org/wp-admin/edit.php). Its path is `/wp-admin/edit.php` relative to the configured church website. The demonstrated page is headed **Posts**, while **Articles** is highlighted under **CONTENT** in the sidebar.

## 2. Duplicate an existing announcement

1. Locate the existing announcement post to use as the starting point. Use the user's selected post when supplied; if the source is unclear, clarify which announcement to duplicate.
2. Hover over that post's row to reveal its actions.
3. Click **Duplicate This**. Its tooltip is **Duplicate this as draft**.
4. Inspect the resulting page and confirm the copy is a draft before editing it. Continue with the copy, preserving the original published announcement. If the operation is interrupted or its result is unclear, inspect the Posts list for the resulting draft before repeating duplication.

Read [Posts list and duplicate action](references/posts-duplicate-announcement.png) when identifying the page or control. The screenshot shows **Announcements – September 4th** as an example source; that title and date are not fixed inputs for future runs. Use current labels and page state rather than fixed screen coordinates.

## 3. Open the duplicated draft

After duplication, the demonstrated interface returns to the **Posts** list. The copy initially has the same title as the published source, but its row carries a **Draft** badge. A **Draft** filter also appears above the list; its count depends on the site's current content.

1. Identify the newly duplicated announcement by its title and **Draft** badge. Do not select the original published row with the same title or rely on row position alone.
2. Hover over the draft row to reveal its actions and click **Edit** to open the full editor.
3. Confirm the editor belongs to the draft. Retain its post ID or edit URL in the local task record so later work resumes this copy without duplicating again.

Read [Duplicated announcement draft and Edit action](references/posts-announcement-draft-edit.png) when distinguishing the draft from the published source. Example titles and counts in the screenshot are not fixed inputs.

## 4. Update the title, quote, and main content

The demonstrated draft opens in the WordPress block editor. The title appears above a separate quote area and the main announcement body. The Post sidebar shows **Status: Draft**.

1. Update the title to **Announcements - Month DayOrdinal**, following the existing style (for example, `Announcements - September 11th`). Use the date the announcements are being updated, in the user's local timezone, unless the user explicitly specifies a different date. This is the update date, not automatically the upcoming Sunday, the source post's date, or the email's date. Use the full month name and day with its ordinal suffix; the demonstrated title omits the year.
2. Replace the old quote with the quote supplied in the announcement email, including its supplied attribution. Use the email or content provided for this update; do not reuse the screenshot's example quote. If the quote is unavailable, obtain it before treating the entry as ready.
3. Delete the old main announcement content and insert the new supplied content. Keep the quote separate from the main body. Preserve the new content's wording, section breaks, and hyperlinks unless the user requests editing; do not carry forward old announcements simply because they were present in the duplicated post.
4. Compare the title, quote, attribution, and complete body with the supplied source. Check that old content has been replaced, the new body is not truncated, and supplied links remain linked to their intended destinations.

Consult [Announcement draft editor](references/announcement-draft-editor.png) when locating the title, quote, main body, and Post sidebar. The screenshot also shows category **Pastor's Weekly Update** and tag **announcements** on this example. Retain the duplicated post's existing classification unless the user requests a change; these observed values do not establish new category or tag rules. The title date and the sidebar **Slug** are distinct fields; changing the title does not establish that the slug was updated.

## 5. Update the interesting-links section

Keep the section heading **A Few Interesting Links To Provoke Thought**.

- When Pastor John supplies interesting links for this update, replace the previous section content with those links, preserving supplied labels, accompanying text, and hyperlink destinations.
- When he has nothing to share for this update, replace the section content with exactly **Nothing to share this week.**
- Remove links carried over from the duplicated post unless they are also supplied for the current update. Do not find or invent substitute links.
- If the current email or supplied content is unavailable or incomplete, do not treat that as confirmation that there are no links; obtain the missing source information.

Consult [Interesting-links section](references/announcement-interesting-links.png) when locating this area. Confirm this section remains present after replacing the main announcement body, and that it contains either the current supplied links or the no-links message, not both.

## 6. Set the author to John Downs

The author for announcements is always **John Downs** (Pastor John), as explicitly specified by the user. Do not retain the duplicating account as author or ask who the author should be on each run.

1. In the editor's right sidebar, select the **Post** tab and locate **Author**.
2. Click the currently displayed author name to open the **Author** popup.
3. Open the popup's author dropdown and select the existing **John Downs** entry.
4. Verify the Post sidebar now displays **John Downs** beside **Author**. If that entry is unavailable, report the issue rather than selecting a different author or creating a user.

Consult [Post sidebar Author field](references/announcement-author-field.png) to locate the field and [Author selection popup](references/announcement-author-popup.png) to identify the dropdown. The screenshots show **Bryan Cox** before the change; the user's walkthrough establishes **John Downs** as the selection to make.

## 7. Publish the announcement

After completing the edits, click **Publish** at the top of the editor, as specified by the user's walkthrough. The button is visible at the upper right in the [Announcement draft editor](references/announcement-draft-editor.png).

Before clicking, verify that the draft has the update-date title, supplied quote and attribution, complete new announcement body, current interesting links or **Nothing to share this week.**, and **John Downs** as author. Follow the active request's publication scope: publish when completing an authorized announcement publication, and leave the post as a draft when the user asks only for preparation or review. A walkthrough teaching this skill is not a request to publish a live announcement.

Inspect the result after clicking. Do not assume the first click completes publication if the interface presents another confirmation step. If the outcome is uncertain, inspect the same post's status before retrying; do not create another copy or claim publication succeeded without confirmation.

## 8. Verify the public announcement

1. After publication, open [Mercy PCA Articles](https://mercypca.org/articles/), the public `/articles/` page.
2. The first blog post should be the announcement just published. Confirm its title and update date match the intended announcement; do not rely on position alone. If it is not first, inspect the listing and the saved post's publication state before reporting success. Do not create another duplicate to resolve a listing mismatch.
3. Click **Read More** on the matching announcement to open the full public post. The listing excerpt alone is not sufficient verification.
4. Compare the full post with the supplied material: update-date title, quote and attribution, complete main announcement body, section formatting, and current interesting links or **Nothing to share this week.** Check that supplied hyperlinks retain their intended destinations and that obsolete content from the source post is absent.
5. Confirm **John Downs** wherever an author is publicly displayed; if the public template does not show an author, use the saved editor value to verify authorship. Confirm the page is publicly accessible rather than a draft preview.
6. Retain the final public URL with the post ID/edit URL. If anything is missing or incorrect, report the specific discrepancy and correct it within the authorized task before repeating the relevant checks. Do not claim verification passed if it could not be completed.
7. After these checks pass, prepare the shareable post below and return it to the user with a brief confirmation of publication.

Consult [Public Articles listing and Read More](references/articles-announcement-verification.png) when identifying the first announcement card and its **Read More** button. Screenshot dates, titles, and excerpts are examples, not content for future announcements.

## 9. Provide a shareable Discord and Facebook post

After public verification, send the user one polished, ready-to-copy post suitable for both Discord and Facebook. The user will share it; this step does not authorize posting to either platform or sending messages to others.

Follow the user's example style:

- Open warmly with **📣 Here’s what’s happening at Mercy Church!**
- Highlight the current announcements in short, readable paragraphs, each led by an appropriate emoji. Include the most useful dates, times, locations, and participation details from the verified content. Use blank lines between items.
- Use a friendly, welcoming church-community voice. Summarize faithfully without inventing events, urgency, or details. Do not impose a fixed number of highlights.
- Close with a natural invitation to read the full announcements, mentioning supporting resources such as sermon texts, songs, sign-ups, or registration only when present in this update. Include the actual verified public post URL, not the Articles listing or a URL guessed from the title.
- Keep formatting portable: plain text, emoji, paragraph breaks, and the full URL. Do not reproduce escaped HTML artifacts such as `&#x20;` from the example. In an interface with reusable writing blocks, present the finished copy in a social-post writing block.

The user's example highlighted a new building, men's Bible study, Sunday school, building-care opportunities, and a camping trip. These are examples of tone and detail, not recurring announcements to include by default. The example's September dates, street address, campground, and old announcement URL must not carry over unless supplied for the current update. Use relative phrases such as “this Sunday” only when accurate for the current sharing date; prefer explicit dates when timing is uncertain.

## Completion criteria

The updated announcement has been published from the duplicated draft with the intended title, new content, interesting-links section, and **John Downs** as author, its full public page has been verified through the Articles listing, and the user has received a ready-to-copy Discord/Facebook post with the verified announcement link.
