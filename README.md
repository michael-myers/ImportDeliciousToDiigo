# ImportDeliciousToDiigo
An "Import Bookmarks" script for Diigo that fixes what they will not (bookmarks with descriptions over 255 characters).

Diigo.com is a bookmarks (and annotations, web page snapshot, etc.) hosting service on the web. Users of competing services (e.g., Delicious.com or Del.icio.us) can export their bookmark collection to a file (in the HTML-like Netscape Bookmark File Format, documented here: https://msdn.microsoft.com/en-us/library/aa753582.aspx), and re-import it to Diigo using https://www.diigo.com/tools. But Diigo's implementation of its import feature has a known (but undocumented) limitation: bookmark "descriptions" are truncated to 255 characters. The major competing service, Delicious, allows for at least 1000 character descriptions. Diigo's own bookmarking tools (for creating or editing bookmarks) do not have any such restriction, so there is no reason for the 255 limitation except negligence. Diigo users have been asking for this limitation to be fixed since at least 2010! http://feedback.diigo.com/forums/76543-bugs/suggestions/1325555-my-bookmarks-tags-imported-from-delicious-but-th#comments But even paid accounts are affected by the limitation.

Users with thousands of bookmarks to import cannot be expected to manually import them, or fix them one-by-one after a broken Diigo import.

This script, which is implemented in plain JavaScript (no external frameworks or dependencies) in a single HTML file exemplifying its use, reads in a "Delicious format" bookmarks file and imports it into the user's Diigo account. The user will be prompted by their browser to authenticate (HTTP Basic Authentication) to their Diigo account. The script itself does not handle the user's credentials. All communications with Diigo.com use their HTTPS API.

# Usage Instructions
Open the HTML file in a modern web browser, click on the button, and provide your bookmarks file. You may be prompted by the browser for your Diigo credentials. Sit back and wait for the import to finish.

# Known Limitations
This script relies on the Diigo API, whose documentation states that URLs and Descriptions for bookmarks are limited to "250" characters, but this limit is not actually enforced in practice. That may change in the future. The other issue is that "created on" dates cannot be specified using the Diigo API, so these dates will be lost (bookmarks will have a creation time of when you ran this script).

# Acknowledgements
The file parsing code is a fork of "nsBookmark" from https://github.com/hohogpb/NETSCAPE-Bookmark.js
