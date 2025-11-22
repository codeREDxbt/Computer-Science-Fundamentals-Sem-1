# Portfolio Site Documentation (Capstone)

## 1. Project Overview
This capstone project is a personal developer portfolio (Lab 3) showcasing skills, projects, and contact form within a modern, responsive, accessible, and animated interface. Built using semantic HTML5 and CSS3 (Flexbox + Grid) with a glassmorphism-inspired dark theme and subtle motion.

## 2. Goals & Value Proposition
- Present professional identity (name, role, social links).
- Demonstrate clean semantic structure for maintainability and accessibility.
- Provide responsive layout for mobile, tablet, and desktop.
- Showcase reusable CSS patterns (variables, utilities, component classes).
- Serve as foundation for future interactive enhancements (routing, dynamic project data).

## 3. Tech Stack
| Layer | Technology | Notes |
|-------|-----------|-------|
| Markup | HTML5 | Semantic sections: `header`, `nav`, `section`, `footer`. |
| Styling | CSS3 | Flexbox (hero), Grid (skills/projects), custom properties (theme). |
| Fonts | Google Fonts | Poppins (300, 400, 600 weights). |
| Images | Local asset | `photo.jpg` avatar. |
| Interaction | Native browser | Basic links & form (no JS yet). |

## 4. Directory Structure (Relevant)
```
Capstone/
	index.html         # Portfolio markup
	style.css          # All styling (variables, layout, animations, responsive)
	photo.jpg          # Profile avatar image (referenced in hero)
	README.md          # Original lab description (Flexbox & Grid focus)
```

## 5. HTML Architecture
| Section | Element(s) | Purpose |
|---------|------------|---------|
| Header | `<header>`, `<nav>`, brand link, `<ul>` nav links | Persistent top navigation, sticky, smooth scroll anchors. |
| Hero | `<section class="hero">` with text + image | Immediate identity & role; animated entry. |
| About | `<section id="about">` | Personal summary (education, interests). |
| Skills | `<section id="skills">` with grid of `.skill-card` | Categorized technical competencies. |
| Projects | `<section id="projects">` with `.project-card` articles | Highlight sample projects + CTA buttons. |
| Contact | `<section id="contact">` form elements | Basic form structure (placeholder submission). |
| Footer | `<footer>` with social links | Attribution, external profiles. |

Semantic correctness: Each major area uses `<h2>` for section headings, descriptive alt text on avatar image, and anchor aria-labels on social links for assistive clarity.

## 6. CSS Architecture
### 6.1 Design Tokens (Custom Properties)
Defined in `:root`:
```
--bg-color, --bg-alt, --primary, --secondary,
--text-color, --text-muted, --border-radius,
--shadow, --transition
```
Purpose: centralize theme for fast iteration (color theming, elevation, motion).

### 6.2 Layout Systems
- Flexbox: `.nav`, `.hero-container` (responsive direction switch), card alignment.
- CSS Grid: `.skills-grid`, `.projects-grid` (auto-fit responsive columns, repeat patterns).
- Container utility: `.container` sets max-width and horizontal centering.

### 6.3 Component Classes
| Component | Classes | Notes |
|-----------|---------|-------|
| Navigation | `.site-header`, `.nav`, `.nav-links`, `.brand` | Sticky header, backdrop blur (glassmorphism). |
| Hero | `.hero`, `.hero-container`, `.hero-text`, `.hero-image`, `.avatar` | Reverse column on mobile → row at ≥768px. |
| Skill Card | `.card.skill-card` | Glass panel with hover elevation + color accent. |
| Project Card | `.card.project-card` | Animated staggered entrance; hover scale + glow. |
| Form | `.contact-form`, `.form-group` | Focus states with color + subtle shadow. |
| Footer | `.site-footer`, `.social-links` | Central alignment, accessible link targets. |
| Buttons | `.btn`, `.submit-btn` | Transition and glow animation on hover. |

### 6.4 Animations
| Name | Purpose | Elements |
|------|---------|---------|
| `fadeInDown` | Intro text entrance | `h1` in hero. |
| `slideInLeft` | Hero text container entrance | `.hero-text`. |
| `slideInRight` | Hero image entrance | `.hero-image`. |
| `float` | Gentle bobbing motion | `.avatar`. |
| `colorChange` | Alternating accent hues | `.highlight`. |
| `fadeInUp` | Staggered card appearance | Skill/Project cards. |
| `glow` | Dynamic button glow loop | `.btn:hover`. |

### 6.5 Responsive Breakpoints
| Breakpoint | Media Query | Adjustments |
|------------|-------------|-------------|
| Mobile | `max-width: 480px` | Hide `.nav-links`; skills grid → 1 column. |
| Tablet/Desktop | `min-width: 768px` | Hero switches to row layout; skills grid → 4 columns; larger heading size. |
Fluid typography applied via `clamp()` in hero heading.

## 7. Design System
| Token | Role | Example |
|-------|------|---------|
| `--primary` | Accent turquoise | Buttons, borders, glow start. |
| `--secondary` | Purple secondary | Headings (h3), colorChange end state. |
| `--border-radius` | Rounded panels | Cards, buttons, avatar border union. |
| `--shadow` | Depth layer | Elevation on interactive components. |
| `--text-muted` | Body copy | Paragraph content for contrast hierarchy. |

Spacing: Sections use `padding: 4rem 0`; grid gaps (1.5rem–2rem) maintain rhythm.

## 8. Accessibility Considerations
- High contrast accent against dark background.
- `aria-label` attributes on social links + brand link.
- Focus states for form inputs (distinct border + glow).
- Semantic headings (single `<h1>`; descending `<h2>` structure for sections).
- Smooth scroll for anchor usability.

Future improvements: add skip-to-content link, keyboard navigation for hidden nav on mobile, form validation messaging.

## 9. Performance Considerations
- Limited external dependencies (single Google Fonts request).
- Local image sized to 250×250 (avoid layout shift; consistent object-fit).
- Animations use transform/opacity (GPU-friendly).
- Reusable gradients reduce asset requests.

Potential optimization: `font-display: swap` in font link, image compression (WebP), minified CSS.

## 10. Responsive Behavior Summary
| Feature | Mobile | Tablet | Desktop |
|---------|--------|--------|---------|
| Navigation | Brand only (links hidden) | Full links visible | Full links visible |
| Hero Layout | Column-reverse (image below) | Row alignment | Row alignment |
| Skills Grid | 1–2 columns | 4 columns at ≥768px | 4 columns |
| Projects Grid | Auto-fit min 280px | Auto-fit scaling | Same, larger viewport space |
| Typography | Scales via clamp | Larger headings | Largest heading size |

## 11. Feature Breakdown
### Navigation
Sticky, glassmorphism header with subtle backdrop blur. Smooth anchor scroll for intra-page navigation.

### Hero Section
Identity (name), role highlight with animated color gradient, introductory paragraph, avatar with float animation.

### Skills Section
Grid of categorized stacks. Hover accent changes with slight scale and shadow for discoverability.

### Projects Section
Staggered animated card entrance enabling visual scanning. Each project includes concise description + CTA.

### Contact Form
Structured inputs with validation attributes (`required`). Currently posts to `#` (placeholder). Focus states enhance clarity.

### Footer
Attribution + external profile links; grouped horizontally; consistent hover accent.

## 12. Deployment Guide
### Option A: GitHub Pages
1. Create repository named `portfolio` (or any name).
2. Commit `index.html`, `style.css`, assets.
3. Enable Pages: Settings → Pages → Deploy from main/root.
4. Access site at `https://<username>.github.io/<repo>/`.

### Option B: Static Host (Netlify/Vercel)
- Drag-drop folder into Netlify dashboard OR push repo → connect.
- Build settings: none (static). Output: root.

### Option C: Local Preview
```bash
python -m http.server 8080
# Visit http://localhost:8080/Capstone/index.html (adjust path)
```

## 13. Setup & Development
| Step | Action |
|------|--------|
| 1 | Clone repo / copy folder. |
| 2 | Open in VS Code (prettier optional). |
| 3 | Launch live server (extension or python server). |
| 4 | Modify content (skills/projects) in `index.html`. |
| 5 | Adjust theme via CSS variables in `:root`. |

## 14. Future Enhancements
| Enhancement | Category | Value |
|-------------|----------|-------|
| Mobile menu (hamburger) | Navigation | Enables full link access <480px |
| Project modal/details | UX | Deep dive without leaving page |
| Dark/light toggle | Theming | User personalization |
| Form backend (EmailJS / API) | Contact | Functional submissions |
| Lazy-loaded project images | Performance | Faster initial render |
| Accessible focus outlines tune | A11y | Better keyboard discoverability |
| CSS extraction to modules | Maintainability | Scalable style architecture |
| Add micro-interactions (scroll reveal) | Engagement | Progressive attention cues |
| Structured data (JSON-LD) | SEO | Rich search results |

## 15. Testing & Validation Checklist
| Area | Test | Expected |
|------|------|---------|
| HTML Structure | W3C validator | No critical errors |
| Accessibility | Lighthouse A11y audit | ≥90 score |
| Performance | Lighthouse perf | ≥85 after optimization |
| Responsive | Manual resize | Layout shifts handled; readable |
| Links | Click each anchor | Correct scroll & external navigation |
| Form | Required fields | Browser prevents empty submission |

## 16. Class Reference (Selected)
| Class | Role |
|-------|------|
| `.container` | Content width constraint & centering |
| `.hero-container` | Flex wrapper controlling hero layout |
| `.skills-grid` | Grid layout for skill cards |
| `.projects-grid` | Auto-fit project cards |
| `.card` | Shared card base styling |
| `.skill-card` / `.project-card` | Specialized card visuals/animations |
| `.highlight` | Emphasized inline text with animated colorChange |
| `.avatar` | Circular profile image styling |
| `.contact-form` | Grid layout for form fields |
| `.social-links` | Horizontal link list in footer |

## 17. Code Snippets
### Responsive Grid Example
```css
.projects-grid {
	display: grid;
	grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
	gap: 2rem;
}
```

### Hero Flex Switch
```css
@media (min-width: 768px) {
	.hero-container { flex-direction: row; justify-content: space-between; }
}
```

## 18. Risks & Mitigations
| Risk | Impact | Mitigation |
|------|--------|-----------|
| Hidden nav on mobile | Limited section access | Implement hamburger toggle |
| Single CSS file growth | Harder maintenance | Modularize into partials later |
| No backend for form | Lost messages | Integrate EmailJS or serverless function |
| Heavy animations added | Performance drop | Keep transforms & throttle effects |

## 19. Attribution
Created by Vinayak Vashisth © 2025 (codeRED). Fonts via Google Fonts (Poppins). No external JS libraries used.

## 20. License & Usage
Personal academic capstone. May be adapted for learning; commercial reuse requires permission.

---
End of consolidated portfolio site documentation.
| Purpose | Timestamped snapshot of a directory (pre-deployment or archival). |
| Inputs | `<source>` (existing dir), `<backup_dir>` (target root). |
| Output | `backup_YYYY-MM-DD_HH-MM-SS` folder inside backup root. |
| Success Indicator | ✓ message including backup size. |
| Failure Modes | Missing source, copy error. |

Flow:
```
Validate args -> Check source -> Ensure backup root -> Timestamp -> Recursive copy -> Size report -> Status
```
Usage:
```bash
./backup_directory.sh /path/to/source /path/to/backups
```
Sample Success:
```
✓ Backup successful: ./backups/backup_2025-11-17_22-30-15 (125M)
```

### 5.2 Monitoring Script (`monitor_resources.sh`)
| Aspect | Details |
|--------|---------|
| Purpose | Periodic logging of CPU %, memory summary, process count. |
| Inputs | `[logfile]` (default: system.log), `[interval]` seconds (default: 10). |
| Output | Appended timestamped blocks. |
| Termination | Ctrl+C interrupt. |

Block Example:
```
[2025-11-17 22:31:05]
CPU: 12.5%
Memory: Mem: 5.1G used / 8.0G total
Processes: 245
---
```
Usage:
```bash
./monitor_resources.sh performance.log 5
```
Considerations: Use external rotation for long runs; parse logs via `grep`, `awk`.

### 5.3 Download Script (`automated_download.sh`)
| Aspect | Details |
|--------|---------|
| Purpose | Resilient file retrieval with retry and integrity check. |
| Inputs | `<URL>`, `<destination_dir>` |
| Config | MAX_RETRIES=3, RETRY_DELAY=5s, timeout=10s per attempt. |
| Success Indicator | ✓ message with file size. |
| Failure Indicator | ✗ after final attempt. |

Flow:
```
Validate args -> URL format check -> Ensure destination -> Extract filename -> Attempt loop { wget -> verify non-empty -> success or retry } -> Final status
```
Usage:
```bash
./automated_download.sh https://example.com/file.zip downloads
```
Success Example:
```
Attempt 1/3: Downloading file.zip...
✓ Download successful: downloads/file.zip (2.3M)
```
Failure Example:
```
Attempt 1/3: Downloading file.zip...
Retrying in 5 seconds...
Attempt 2/3: Downloading file.zip...
Retrying in 5 seconds...
Attempt 3/3: Downloading file.zip...
✗ Download failed after 3 attempts
```

## 6. Architecture Summary
Text Diagram:
```
User Input -> Validation -> Core Operation (loop or single action) -> Artifact (backup/log/file) -> Status Output (✓ / ✗) -> Exit Code
```
Key Patterns: Guard clauses, minimal dependencies, clear timestamps, explicit exit codes.

Design Principles:
| Principle | Effect |
|----------|--------|
| Simplicity | Easy audit & modification |
| Transparency | Human-readable logs/messages |
| Resilience | Retry logic for network volatility |
| Extensibility | Clear structure for flags/features |
| Portability | GNU baseline utilities only |

## 7. Use Cases
| Scenario | Script | Outcome |
|----------|--------|---------|
| Pre-deployment snapshot | Backup | Rollback capability |
| ML training diagnostics | Monitoring | Resource trend insight |
| Dataset acquisition | Download | Reliable retrieval or clear failure |
| Compliance archive | Backup | Traceable historical states |
| Performance regression tracking | Monitoring | Comparative analytics |
| Bootstrap pipeline | Download | Automated dependency fetch |

## 8. Validation & QA
| Test | Method |
|------|-------|
| Backup completeness | Compare source vs backup tree count |
| Monitoring correctness | Inspect log blocks for consistent format |
| Download integrity | Check non-zero file size; option for checksum |
| Error handling | Provide invalid args; expect usage or error messages |
| Retry reliability | Disconnect network mid-download to force retries |

## 9. Security & Safety
| Topic | Recommendation |
|-------|---------------|
| Privilege usage | Limit sudo to installs/config only |
| Backup permissions | Restrict write access, avoid world-readable sensitive data |
| URL trust | Validate sources before automated download |
| Log sensitivity | Protect logs with `chmod 640` if they may include system metadata |

## 10. Future Enhancements (Summary)
| Feature | Benefit |
|---------|--------|
| Compression (tar.gz) | Reduced disk usage |
| SHA256 checksums | Integrity assurance |
| Flags parsing (`getopts`) | Flexible CLI interface |
| Threshold alerts | Proactive resource warnings |
| Log rotation | Prevent uncontrolled growth |
| Parallel downloads | Faster dataset ingestion |
| Differential backups (rsync) | Efficient large directory sync |
| JSON metrics | Dashboard integration |

## 11. Extension Hooks
- Add `--compress` flag in backup script.
- Introduce `--retries`, `--timeout`, `--delay` in download script.
- Provide `--format json` in monitor script.
- Build wrapper orchestrator to chain all three processes.

## 12. Quick Command Cheat Sheet
| Task | Command |
|------|---------|
| Make scripts executable | `chmod +x *.sh` |
| Run backup | `./backup_directory.sh src backups` |
| Run monitoring | `./monitor_resources.sh system.log 10` |
| Run download | `./automated_download.sh URL downloads` |
| View latest log | `tail -n 30 system.log` |
| Count processes | `ps aux | wc -l` |
| Disk usage summary | `du -sh *` |
| Search errors in log | `grep -i error system.log` |

## 13. Maintenance Guidelines
| Action | Frequency | Notes |
|--------|----------|-------|
| Remove old backups | Weekly | Keep last N snapshots |
| Rotate monitoring logs | As needed | Consider size threshold (e.g., >5MB) |
| Validate download endpoints | Quarterly | Remove deprecated URLs |
| Dependency check (`apt upgrade`) | Monthly | Ensure tools updated |

## 14. Academic Context & Attribution
Developed by Vinayak (Roll No: 2501730150, Section C, B.Tech AI & ML) as a capstone demonstration of practical Linux automation capabilities.

## 15. Appendix: Sample Cron Entries
(Use `crontab -e` to schedule)
```
# Nightly backup at 01:30
30 1 * * * /home/user/automation_toolkit/backup_directory.sh /home/user/projects /home/user/backups >> /home/user/backup_cron.log 2>&1

# Resource monitor every 15 min for 2 hours (example wrapper needed)
*/15 * * * * /home/user/automation_toolkit/monitor_resources.sh cron_system.log 60 &
```

---
End of consolidated documentation. Refer to individual docs for deeper granularity where needed.
