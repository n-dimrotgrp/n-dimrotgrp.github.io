# So Nakamura's academic website

A single-page academic website using plain HTML and CSS. All academic content was migrated from the published “Welcome!” page (WordPress post ID 4) in `sonakamura.WordPress.2026-09-18.xml`. No build, package installation, or JavaScript is required.

## Files

```text
SoWeb/
├── sonakamura.WordPress.2026-09-18.xml  # Original source; local and Git-ignored
├── README.md
├── .gitignore
├── .vscode/
│   ├── extensions.json                # Recommends Microsoft's Live Preview
│   └── settings.json                  # Serves docs/; refreshes on save
└── docs/
    ├── index.html                    # The complete public page
    ├── .nojekyll                     # Disables Jekyll processing on Pages
    └── assets/css/style.css          # Screen, mobile, and print styles
```

## Preview in VS Code

1. Open this folder in VS Code with **File → Open Folder**.
2. Install the recommended **Live Preview** extension by Microsoft (`ms-vscode.live-server`).
3. Open `docs/index.html` and click the preview button at the top right of the editor, or use its context menu to show a preview.
4. Save HTML or CSS changes to refresh the preview. Use the preview's menu to open it in an external browser if desired.

The workspace settings make `docs/` the server root. Use the local address shown by Live Preview; there is no build command. Opening `docs/index.html` directly in a browser also works, but does not provide automatic refresh.

See [Microsoft Live Preview](https://github.com/microsoft/vscode-livepreview) for extension documentation.

## Content authority and migration map

The XML is the authoritative migration source. The website is a reviewed, one-time HTML conversion, not a live view of the XML. Replacing the XML does not automatically update the website. Use a newer export or explicit owner-provided corrections for future factual changes, then update the relevant HTML and this record.

| XML source | Website location | Treatment |
| --- | --- | --- |
| Channel title and description | Header | “So Nakamura”; capitalize “algebraist” as “Algebraist.” |
| Page 4 opening paragraph | About / introduction | Preserve the biography and all three links, including nLab. |
| Contacts | Introduction contact details | Preserve the obfuscated email and complete postal address. |
| Research Interests | `#research` | Preserve all five named fields and “etc.”; normalize capitalization. |
| Publications | `#publications` | Preserve all three entries in source order, titles, collaborators, and original link destinations. Consolidate separate lists; use readable arXiv labels and a subscript in 𝔽₁. |
| Awards | `#awards` | Preserve the award and its explanatory sentence. |
| Talks | `#talks` | Preserve all three entries, dates, venues, and UCSD's “invited” designation. |
| Conferences | `#conferences` | Preserve all five entries and the 2022 online designation. |
| Teaching Assistant | `#teaching` | Preserve 19 course/program assignments across 17 terms (2021–2026), including four graduate algebra assignments, the graduate Jumpstart program, and two grader assignments. Use term-and-course rows, newest first. |
| Service | `#service` | Preserve refereeing, organizing, volunteering, and all listed years. |
| Links | `#links` | Preserve advisor, collaborator, related people, and department links. |
| Page 4 `wp:post_modified` | Footer | 4 July 2026; the export date is not represented as the content revision date. |

### Editorial decisions

- Preserve “was a math PhD student,” the job-market statement, and “2024–present” as supplied. Do not infer a completed doctorate, a new affiliation, or updated employment status.
- The source links “Jinghao” to `https://chenovski.github.io/index.html` and “Chen” to `https://sites.uci.edu/chern/`. Present the full name with both destinations explicitly labeled “GitHub website” and “UCI website”; neither destination is discarded or assumed to supersede the other.
- Keep the “Publications” heading. Two entries supply arXiv references; the third supplies a journal citation. Do not add publication status, abstracts, DOI, or bibliographic facts absent from the XML.
- Normalize missing spaces before parentheses, punctuation, numeric dashes, and section capitalization. Replace event separators with em dashes. Remove the trailing placeholder ellipsis from related people.
- Preserve the original public-facing academic email, not author-account metadata from the export.
- Remove Gutenberg comments, WordPress classes, inline theme configuration, empty paragraphs, and fragmented list wrappers.

### Records not rendered

- **Posts 1 and 26:** “Hello Anteaters!” and “Second Post” contain template instructions, not academic news.
- **Eleven attachment records:** the XML contains image URLs and metadata, not image binaries. The academic page body embeds no images. No attachment is fetched or placed on the page.
- **Four styling records:** theme CSS and global styles are replaced by the site's stylesheet.
- **Administrative metadata and comments:** retained only in the original XML.

The source XML remains unchanged and outside `docs/`. It is Git-ignored because it includes WordPress account metadata. Retain your own backup of this file; cloning the public website repository will not restore it.

## Editing

- Edit academic content directly in `docs/index.html`, using the section IDs above.
- Edit layout and typography in `docs/assets/css/style.css`.
- Keep local URLs relative (for example, `./assets/css/style.css`) so both account and project Pages URLs work.
- Keep navigation fragments and section IDs synchronized.
- Update the footer's visible date and `datetime` attribute only when academic content is actually revised. Styling-only changes do not change that date.
- The inline favicon is a small serif “S”; the site uses system fonts and has no remote font, script, or image dependency.

## Publish later with GitHub Pages

1. Create a GitHub repository. Name it `<username>.github.io` for an account homepage, or use another name for a project site. GitHub Free requires a public repository for Pages.
2. Initialize Git locally if necessary, connect the chosen repository, and commit the website files, `.vscode/`, `.gitignore`, and this README. Keep the XML ignored.
3. Push the files to `main`.
4. In the repository, open **Settings → Pages**. Choose **Deploy from a branch**, branch **main**, folder **/docs**, and save.
5. Open the URL GitHub reports after deployment. Check the stylesheet, all section links, and the mobile layout there.

Account sites use `https://<username>.github.io/`; project sites use `https://<username>.github.io/<repository>/`. Both work with this site's relative paths. `docs/.nojekyll` skips Jekyll processing. Later pushes to `main` publish changes in `docs/` without a custom Actions workflow.

Only `docs/` is the publishing source. Do not add a `CNAME` until a custom domain has been selected and configured. Redirecting the old UCI address requires control of the WordPress site and is separate from GitHub Pages.

See [GitHub Pages setup](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site) and [publishing-source configuration](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site).

## Before publishing content changes

- Compare every changed academic entry with its source, including course codes, dates, and coauthors.
- Check every navigation anchor and local asset, and review external link destinations without silently replacing source URLs.
- Check narrow mobile and desktop widths, 200% zoom, and keyboard navigation (including “Skip to content” and “Back to top”).
- Use the browser's print preview to check readable page breaks and complete teaching history.
- Confirm that the original XML is neither modified nor included in the published directory or staged Git files.

## Initial verification — 18 September 2026

The original XML's SHA-256 remained `7c504a71fc6a465597136f7d45cd486710b84865c822a69d9cc9221a37467248`. A content comparison checked every source list entry and nested group after the documented punctuation and URL-label changes, all 16 external-link occurrences, and the 17 teaching terms / 19 assignments. Local asset paths, section anchors, unique IDs, balanced HTML tags, and VS Code JSON were checked.

The page was inspected at desktop and narrow mobile widths, including 320 px, with no horizontal overflow. The teaching rows switch from aligned columns to stacked entries. The teaching anchor and keyboard skip link were exercised in the browser.

Nine of the twelve unique external URLs returned successful responses to automated HEAD checks. Both arXiv links returned HTTP 406 and the ScienceDirect link returned HTTP 403, so those three destinations could not be confirmed by that check. Their original source URLs are retained. Print styles are included; inspect the browser's print preview before relying on a particular paper size or printer layout.
