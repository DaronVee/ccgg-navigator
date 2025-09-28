# CCGG Navigator - Technical Documentation & Deployment Guide

## Purpose
The CCGG Navigator is a web-based resource discovery tool for the CCGG (Community with Custom GPTs for online entrepreneurs) that helps members find the right learning path based on their goals. It serves as both a member resource and a marketing tool to showcase the community's value to potential members.

## Key Features
- **Goal-based navigation**: Users select their objective and receive a personalized learning path
- **JSON-driven content**: All modules, paths, and configurations are managed via JSON
- **No authentication required**: Public access for both members and prospects
- **Mobile responsive**: Works seamlessly on all devices
- **Annual membership incentives**: Subtle promotion of premium content

## Technical Architecture

### Stack
- **Frontend**: Pure HTML, CSS, JavaScript (no frameworks)
- **Data**: JSON configuration file
- **Hosting**: Static site (no backend required)
- **Dependencies**: None (completely self-contained)

### File Structure
```
ccgg-navigator/
├── index.html              # Main application file
├── ccgg-config-v3.json    # Configuration and content
└── README.md              # Documentation
```

### How It Works
1. User loads `index.html`
2. JavaScript reads module and path data from embedded configuration
3. User selects a goal
4. App generates personalized roadmap from JSON data
5. Modules link directly to Skool classroom content

## Content Management via JSON

### JSON Structure
```json
{
  "modules": {
    "module-id": {
      "title": "Module Name",
      "outcome": "What users will achieve",
      "status": "live|coming-soon",
      "access": "all|annual",
      "url": "https://link-to-content"
    }
  },
  "paths": {
    "goal-id": {
      "goal": "User goal description",
      "modules": ["module-1", "module-2", "module-3"]
    }
  }
}
```

### Adding a New Module
1. Add module definition to `modules` object
2. Include in relevant paths
3. No code changes needed

### Creating a New Path
1. Add new goal button in HTML (one-time)
2. Define path in JSON `paths` object
3. List module IDs in order

### Marking Content as Annual-Only
Set `"access": "annual"` in module definition

## Maintenance Guide

### Common Updates

**Update Module Title/Description:**
Edit the module in `ccgg-config-v3.json`

**Change Module Order in Path:**
Reorder module IDs in the path's `modules` array

**Add Annual Content:**
Set module's `access` to `"annual"`

**Update Module URL:**
Change the `url` field in module definition

**Mark Module as Coming Soon:**
Set `"status": "coming-soon"`

## Deployment Instructions

### Recommended: Netlify (Free Tier)

1. **Prepare Files**
   - Ensure `index.html` contains the latest code
   - Verify `ccgg-config-v3.json` has current content

2. **Deploy to Netlify**
   ```bash
   # Via Netlify CLI
   npm install -g netlify-cli
   netlify deploy --dir=. --prod
   
   # Or drag & drop folder to netlify.com
   ```

3. **Custom Domain (Optional)**
   - Add custom domain in Netlify settings
   - Point DNS to Netlify servers

### Alternative: GitHub Pages (Free)

1. Create GitHub repository
2. Upload files to repository
3. Enable GitHub Pages in Settings
4. Access at `https://[username].github.io/[repo-name]`

### Alternative: Vercel (Free Tier)

1. Install Vercel CLI: `npm i -g vercel`
2. Run `vercel` in project directory
3. Follow prompts for deployment

## Update Process

### Manual Update
1. Edit `ccgg-config-v3.json` locally
2. Test changes by opening `index.html`
3. Redeploy to hosting service

### Automated Update (CI/CD)
1. Push changes to GitHub
2. Connect repo to Netlify/Vercel
3. Auto-deploys on commit

## URLs and Access

### Development
Open `index.html` directly in browser

### Production Examples
- Netlify: `https://ccgg-navigator.netlify.app`
- GitHub Pages: `https://[org].github.io/ccgg-navigator`
- Vercel: `https://ccgg-navigator.vercel.app`

### Sharing
Share the production URL with:
- CCGG members (via Skool community)
- Prospects (in marketing materials)
- Social media audiences

## Troubleshooting

**Modules not showing:**
- Check module ID matches in paths
- Verify JSON syntax is valid

**Links not working:**
- Ensure URLs include `https://`
- Check Skool links are accessible

**Annual badges missing:**
- Verify `access: "annual"` is set
- Check spelling of access level

## Security Considerations
- No sensitive data in JSON
- All content is public
- Links to Skool require membership
- No user data collected

## Performance
- Loads instantly (< 100KB total)
- No external dependencies
- Works offline after first load
- Mobile-optimized

## Browser Support
- Chrome 90+
- Safari 14+
- Firefox 88+
- Edge 90+
- Mobile browsers

## Version History
- v3.1: Current version with annual benefits
- v3.0: Added support resources
- v2.0: Introduced JSON configuration