JERZY — LIFE, COLLECTED
Working bilingual WordPress website. Published to https://jerzy.us/ with owner approval on 2026-10-30.
Owner dashboard: https://jerzy.us/wp-admin/admin.php?page=jerzy-gallery
See HOSTINGER-DEPLOYMENT.txt and live-test-results.json for deployment verification.

INSTALLABLE PACKAGES
jerzy-gallery.zip is the gallery plugin.
jerzy-journal.zip is the matching theme.
The complete source is in wordpress/; all ordinary content is stored by WordPress separately.

QUICK REVIEW
The current development session serves http://127.0.0.1:8770/.
Owner controls: http://127.0.0.1:8770/wp-admin/admin.php?page=jerzy-gallery
The LOCAL runtime automatically signs this computer into a temporary owner account. This is a development-only WordPress Playground feature; it is not included in the theme or plugin and must never be exposed to the Internet.

START A FRESH LOCAL PREVIEW
Install Node.js 22 or 24 if absent. In this directory run npm install, then npm run preview.
This installs the official WordPress Playground development runtime, binds the server to 127.0.0.1, and stores the local WordPress database and private files under .local/.
A fresh source checkout begins with ten empty albums. The original working preview uses illustrative Unsplash photos and MDN CC0 video, explicitly labeled as samples. These are not Jerzy's travel photographs and are not included in the installable packages.
On Windows, if the runtime reports read-only database errors, clear the Read-only attribute from directories within this project's .local directory before restarting. Do not delete the database.
No separate PHP or MySQL installation is needed for the local preview. Production uses Hostinger's native PHP and MySQL.

ARCHITECTURE
Custom WordPress theme plus independent gallery plugin. No paid theme or plugin dependency. PHP 8.1+; tested with PHP 8.3 in local WordPress. Production uses MySQL; local validation uses SQLite through the official Playground runtime. Hostinger/MySQL validation remains a deployment-stage check.
Albums and media are WordPress custom post types. Bilingual content is stored in post metadata. Comments use WordPress moderation. Owner access requires manage_options. The design layer and media records are separate, so updating the theme does not remove uploaded media.
Private gallery files are stored outside public_html and served through access-checked PHP requests. The default path is a sibling directory named jerzy-private-media; JL_MEDIA_DIR may set another path outside the web root.
Photo uploads create optimized full-size and thumbnail derivatives when a WordPress image editor is available. Images load lazily; videos support byte-range requests. Very large libraries will benefit from pagination and dedicated media delivery as a later scaling improvement.

SOURCE OWNERSHIP
All custom source is supplied under GPL-2.0-or-later. Runtime WordPress dependencies retain their own licenses. Do not commit .local/, uploaded media, database exports, wp-config.php, tokens, or passwords. The GitHub repository holds source, not a website deployment.

Read OWNER-GUIDE.txt for daily use and HOSTINGER-DEPLOYMENT.txt before any deployment.

OPTIONAL SAMPLE DATA AND TESTS
With the local preview running, use python scripts/download-samples.py from this directory to download the labeled Unsplash/MDN samples. In the preview terminal type seed, then test. The source test suite creates and removes only its own QA records. Type check for PHP syntax and runtime details. No production data should be used in this local fixture environment.

GITHUB BACKUP
The browser upload contains a versioned source ZIP plus the owner and deployment guides. Extract the source ZIP to obtain the full directory structure; the installable plugin/theme ZIPs can also be downloaded separately. The connector could read but could not write this new repository, so this initial source backup was committed through the browser.
