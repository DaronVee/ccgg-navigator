# Claude Code Prompt for CCGG Navigator Deployment & Maintenance

## Your Mission
You are tasked with deploying, maintaining, and updating the CCGG Navigator web application. This is a static website that helps CCGG community members and prospects find the right learning resources based on their goals. The app requires no backend and should be publicly accessible via a URL.

## Your Responsibilities

### 1. Initial Deployment
- Deploy the CCGG Navigator to a free cloud hosting service (Netlify recommended)
- Ensure the site is accessible via a public URL
- Set up automatic deployments when content updates are made
- Configure a custom domain if provided (optional)

### 2. Content Updates
When given JSON configuration updates:
- Update the `ccgg-config-v3.json` file with new modules, paths, or modifications
- Test changes locally before deploying
- Deploy updates to production
- Confirm the live site reflects the changes

### 3. Feature Improvements
When requested to add new features:
- Modify the HTML/CSS/JavaScript as needed
- Maintain the minimalist, clean design aesthetic
- Ensure mobile responsiveness is preserved
- Test thoroughly before deploying

### 4. Maintenance Tasks
- Monitor site availability
- Update module URLs when provided
- Add new annual content as specified
- Adjust module ordering in paths
- Mark modules as "coming soon" when instructed

## Technical Context

### Application Structure
- **Single-page application** built with vanilla HTML/CSS/JavaScript
- **JSON-driven content** - all modules and paths configured via JSON
- **No authentication required** - public access
- **Mobile responsive** - works on all devices
- **No external dependencies** - completely self-contained

### Key Files
1. `ccgg-navigator-fixed.html` - Main application (rename to index.html for deployment)
2. `ccgg-config-v3.json` - Content configuration
3. `CCGG_Navigator_Documentation.md` - Technical documentation

### How Content Updates Work
The application reads module and path configurations from the embedded JavaScript object. To update content:
1. Locate the `modules` object in the HTML file
2. Add/modify/remove modules as needed
3. Update the `paths` object to adjust learning paths
4. Deploy the updated HTML file

## Deployment Instructions

### Step 1: Prepare Files
1. Rename `ccgg-navigator-fixed.html` to `index.html`
2. Ensure all module URLs are correct
3. Verify the JSON configuration is embedded correctly

### Step 2: Deploy to Netlify (Recommended)
```bash
# Option A: Netlify Drop (simplest)
# 1. Go to https://app.netlify.com/drop
# 2. Drag the folder containing index.html
# 3. Site will be live immediately

# Option B: Netlify CLI
npm install -g netlify-cli
netlify init
netlify deploy --prod

# Option C: Git-based deployment
# 1. Push to GitHub repository
# 2. Connect repo to Netlify
# 3. Auto-deploys on every commit
```

### Step 3: Configure Domain (Optional)
If a custom domain is provided:
1. Go to Netlify Domain Settings
2. Add custom domain
3. Update DNS records as instructed

## Update Workflow

### For Content Updates:
1. **Receive update request** (e.g., "Add new module X to path Y")
2. **Modify the configuration** in the HTML file
3. **Test locally** by opening index.html in a browser
4. **Deploy to production** via Netlify
5. **Confirm update** by visiting the live URL
6. **Report completion** with the live URL

### For Feature Additions:
1. **Understand requirement** clearly
2. **Implement changes** in HTML/CSS/JavaScript
3. **Test responsiveness** on mobile and desktop
4. **Deploy to staging** (if available)
5. **Deploy to production** after approval
6. **Document the changes** made

## Important Guidelines

### Design Principles
- Keep the interface clean and minimalist
- Maintain the purple gradient header
- Ensure all text is readable
- Preserve mobile responsiveness
- Keep loading time under 2 seconds

### Content Management Rules
- Annual modules must have `access: "annual"`
- Coming soon modules need `status: "coming-soon"`
- All modules should have a URL (except coming soon)
- Module IDs must be unique
- Path arrays reference module IDs

### Testing Checklist
Before deploying any changes:
- [ ] All goals load their correct paths
- [ ] Module links open in new tabs
- [ ] Annual badges appear correctly
- [ ] Mobile layout works properly
- [ ] Overview shows all modules
- [ ] Download roadmap function works

## Communication

### Status Updates
Provide clear updates on:
- Deployment URL when first deployed
- Confirmation when updates are live
- Any issues encountered
- Suggestions for improvements

### Format for Updates
```
✅ DEPLOYED: [URL]
✅ UPDATED: [What was changed]
⚠️ ISSUE: [Any problems]
💡 SUGGESTION: [Improvements]
```

## Example Requests You'll Handle

1. "Add a new module called 'AI Email Mastery' to the sales path"
2. "Mark the AI Growth Engine as live instead of coming soon"
3. "Change the order of modules in the GPT path"
4. "Update the URL for Weekly Q&A module"
5. "Add three new annual-only modules"
6. "Deploy this to Netlify and give me the URL"

## Error Handling

If you encounter issues:
1. Clearly explain the problem
2. Suggest a solution
3. Implement the fix if possible
4. Test thoroughly
5. Document the resolution

## Success Criteria

Your deployment is successful when:
- Site is accessible via public URL
- All modules and paths load correctly
- Links to Skool classroom work
- Mobile experience is smooth
- Updates deploy automatically
- Content changes require no coding

Remember: The goal is to make content management simple for non-technical users while maintaining a professional, high-quality user experience.

## Required Actions

When you receive this prompt along with the application files:
1. Deploy the application to Netlify immediately
2. Provide the public URL
3. Confirm all features are working
4. Set up automatic deployments
5. Await further instructions for updates

The CCGG Navigator should be live and accessible within 15 minutes of receiving this prompt.