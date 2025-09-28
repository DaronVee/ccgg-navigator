# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

The CCGG Navigator is a static web application that helps CCGG (Community with Custom GPTs) members find personalized learning paths based on their goals. It's a single-page application built with vanilla HTML, CSS, and JavaScript - no frameworks, build tools, or dependencies.

## Key Architecture

### Single-File Application
- **Primary file**: `index.html` (745 lines) - Contains all HTML, CSS, and JavaScript
- **Configuration**: `ccgg-config-v3.json` - External JSON for content management
- **No build process**: Open `index.html` directly in browser for local testing

### Data Architecture
The application uses a dual-configuration approach:
1. **Embedded config** in `index.html` - JavaScript object with modules and paths
2. **External config** in `ccgg-config-v3.json` - Separate JSON file (not currently used by the HTML)

**Important**: The application currently reads from the embedded JavaScript CONFIG object in `index.html`, not from the external JSON file. Updates must be made to the embedded config.

### Content Structure
```javascript
CONFIG = {
    modules: {
        'module-id': {
            title: 'Module Name',
            outcome: 'Learning outcome',
            time: 'Duration',
            status: 'live|coming-soon',
            access: 'all|annual',
            url: 'https://link-to-content'
        }
    },
    paths: {
        'goal-id': {
            goal: 'User goal description',
            modules: ['module-1', 'module-2', 'module-3']
        }
    }
}
```

## Development Commands

### Local Testing
```bash
# Open the application locally
open index.html
# OR on Windows
start index.html
```

### Content Updates
1. Modify the CONFIG object in `index.html` (around line 400-567)
2. Test by opening `index.html` in browser
3. Deploy updated file to hosting

### No Build/Lint/Test Commands
This project has no package.json, build tools, or testing frameworks. All testing is manual via browser.

## Common Tasks

### Adding a New Module
1. Add module definition to `CONFIG.modules` object in `index.html`
2. Add module ID to relevant path arrays in `CONFIG.paths`
3. Test locally by opening `index.html`

### Creating a New Learning Path
1. Add goal button in HTML (one-time change to DOM structure)
2. Define path in `CONFIG.paths` object
3. List module IDs in desired order

### Marking Content as Annual-Only
Set `access: 'annual'` in module definition - this adds special badges

### Module Status Management
- `status: 'live'` - Available now
- `status: 'coming-soon'` - Shows "COMING SOON" badge, module not clickable

## Deployment

### Recommended: Netlify
```bash
# Drag-and-drop deployment
# 1. Go to https://app.netlify.com/drop
# 2. Drag folder containing index.html
# 3. Site goes live immediately

# OR via CLI
npm install -g netlify-cli
netlify deploy --dir=. --prod
```

### File Structure for Deployment
```
ccgg-navigator/
├── index.html              # Main application (all code)
├── ccgg-config-v3.json    # External config (not currently used)
└── CLAUDE.md              # This file
```

## Code Organization within index.html

### CSS (lines 8-300)
- Responsive design with mobile-first approach
- Purple gradient header theme
- Module card styling with status badges

### HTML Structure (lines 300-400)
- Header with CCGG branding
- Goal selection buttons
- Dynamic roadmap container
- Annual benefits section

### JavaScript (lines 400-745)
- CONFIG object with all content data
- Goal selection and path generation logic
- Dynamic roadmap building
- Annual benefits loader

## Content Management Rules

### Module Properties
- **Required**: `title`, `outcome`, `status`, `access`
- **Optional**: `time`, `url` (omit URL for coming-soon modules)
- **Access levels**: `'all'` (all members) or `'annual'` (premium only)

### Path Configuration
- Paths reference module IDs in the desired learning order
- First module in path gets "Start here" badge (unless it's 'start-here' module)
- Module order determines roadmap sequence

## Testing Checklist

Before deploying changes, verify:
- [ ] All goal buttons load their correct module paths
- [ ] Module links open in new tabs to Skool classroom
- [ ] Annual badges appear on premium modules
- [ ] Mobile layout works properly (test on phone/tablet)
- [ ] "Coming soon" modules show proper status
- [ ] Overview page displays all modules correctly

## URLs and Links

### Content Links
All module URLs point to Skool classroom content requiring CCGG membership. Links use specific markdown parameters for tracking.

### External References
- Main community: https://www.skool.com/ccgg
- AI Tools document: Google Docs (linked in config)

## Performance Notes

- Entire application < 100KB
- No external dependencies or API calls
- Works offline after first load
- Instant page loads (static content only)