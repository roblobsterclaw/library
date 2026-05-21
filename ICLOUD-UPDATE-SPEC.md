# Library Dashboard — iCloud Integration Update

## Task
Update `index.html` to add iCloud document links to project cards. The Library is the "map" and iCloud Drive is the "filing cabinet."

## What to Change

### 1. Add `icloudFolder` field to PROJECTS data
Every project that has files in iCloud gets an `icloudFolder` path. This is the subfolder under `JFL Command Center/` in iCloud Drive.

Map these projects to their iCloud folders:
- "TLC (Tuckerton Lumber)" → `icloudFolder: "Active Projects/Tuckerton Lumber"`
- "ReBolt" → `icloudFolder: "Active Projects/ReBolt"`
- "ReBolt Renders" → `icloudFolder: "Renderings and Media/ReBolt Renders"`
- "Firehouse Renderings" → `icloudFolder: "Renderings and Media/Firehouse Renders"`
- "Lobster Press" → `icloudFolder: "Active Projects/Lobster Press"`
- "Ceremony" → `icloudFolder: "Active Projects/Ceremony"`
- "Equipment Scout" → `icloudFolder: "Active Projects/Equipment Scout"`
- "Social Media" → `icloudFolder: "Active Projects/Social Media"`
- "Surfbox" → `icloudFolder: "Active Projects/Surfbox Storage"`
- "Investing Research" → `icloudFolder: "Business Documents/Investing Research"`
- "Reports" → `icloudFolder: "Reports and Rundowns"` (any project with "report" in the name/type)
- "Daily Reports" → `icloudFolder: "Reports and Rundowns"`

### 2. Add a 📁 Documents button to renderCard()
In the `links-row` section of each card, add a new button AFTER the existing Live Site and GitHub buttons:

```html
<a class="link-btn docs" href="https://www.icloud.com/iclouddrive/043dz2esR-W2WOZs-KmdIgb1A#JFL_Command_Center" target="_blank" rel="noopener">📁 Documents</a>
```

- Only show this button if the project has `icloudFolder` set (non-empty string)
- The base iCloud share link is: `https://www.icloud.com/iclouddrive/043dz2esR-W2WOZs-KmdIgb1A#JFL_Command_Center`
- All buttons link to the same iCloud folder (subfolder navigation happens inside iCloud)
- Style the `.link-btn.docs` button with a green/teal color to distinguish from Live Site (blue) and GitHub (gray)

### 3. Mark Document Vault as archived
Change the "Document Vault" project entry's status from "active" to "archived".
Change the "Document Vault (Local Backup)" entry's status to "archived" as well.
Add a note to both: "Superseded by iCloud Drive — files migrated to JFL Command Center on iCloud"

### 4. Update stats
No code change needed — stats auto-calculate from the data.

## Design Rules
- Keep the light theme (#E2E8F0 background, white cards, royal blue accents)
- The docs button should be visually distinct — suggest green/teal (#059669) background with white text
- Mobile-first, responsive — buttons should wrap nicely on small screens
- No external dependencies — everything stays in one self-contained HTML file

## DO NOT
- Change the theme or color scheme
- Add any external dependencies or frameworks
- Remove any existing functionality
- Change the Document Vault password or any sensitive info
