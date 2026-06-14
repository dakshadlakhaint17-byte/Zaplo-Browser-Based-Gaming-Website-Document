# Build a Browser-Based Gaming Website - Zaplo

# Context

Build a modern browser-based gaming website called **Zaplo** that lets visitors instantly discover and play a curated collection of HTML5 and WebGL games directly from their web browser, with an emphasis on multiplayer and `.io` style titles.

The goal is to create a fast, neon-styled gaming hub where casual gamers can find and play games within two clicks of landing, then share any game with a friend in one click - no downloads, no sign-ups, no friction.

The website should prioritize:

- instant play
- a multiplayer and .io flavor in the catalog
- a "Share to Play" feature that copies a game link to the clipboard
- speed and mobile responsiveness
- clean and maintainable code

This is not a social platform, not a real-time multiplayer service, and not a developer submission portal.

The final site should feel like a neon arcade hub that visitors share with friends.


Only commercially usable assets may be used in the build.

---

# Goal

Build a browser-based gaming website branded as:

```text
Zaplo - One click. One game. Zero wait.
```

The site must:

1. Display a curated catalog of 20 HTML5 and WebGL games across 6 categories.
2. Let any visitor click a game and play it instantly inside the browser.
3. Sort and filter games by category and search by title without page reloads.
4. Provide a "Share to Play" button on every game page that copies the game URL with `?ref=share` to the clipboard.
5. Run smoothly on desktop, tablet, and mobile devices.
6. Serve Google AdSense ads and track behavior through Google Analytics 4.
7. Be deployment-ready on standard static hosting with no special server requirements.

The site should be fully usable without any sign-up or account creation.

---

# Site Structure Requirements

Build exactly:

```text
4 page templates + 4 static pages
```

The site must follow this structure:

## Page 1 - Home Page (`index.html`)

Include:

Title:

```text
Zaplo - One click. One game. Zero wait.
```

Requirements:

- top navigation bar with logo, 6 category links, and a search bar
- "Now Playing" hero section with one large featured game tile
- "Trending" row of 6 game cards
- "Multiplayer Picks" row of 6 game cards
- "Browse by Category" grid of 6 category tiles
- one Google AdSense banner above the footer
- footer with About, Contact, Privacy, Terms links

Avoid:

- pop-ups or modals on landing
- auto-playing audio or video

---

## Page 2 - Category Page (`category.html?cat=multiplayer`)

Show:

- filtered grid of game cards based on the `cat` URL parameter
- category title and short description at the top
- search input that filters the visible grid in real time
- breadcrumb showing `Home > Category Name`

Requirements:

- client-side filtering only - no page reloads
- grid that reflows from 4 columns on desktop to 3 on tablet to 2 on mobile
- empty-state message if no games match

Do NOT include:

- pagination
- infinite scroll
- server-side filtering

---

## Page 3 - Game Detail Page (`game.html?slug=tank-arena`)

Include the actual playable game.

Layout:

- one AdSense banner above the iframe
- game embedded in a 16:9 iframe at the top
- fullscreen toggle button on the iframe
- game title, short description, and controls hint below
- a "Share to Play" button below the title
- "More Like This" strip of 4 related game cards

Requirements:

- game must load within 3 seconds on a 4G connection
- fullscreen must work on iOS Safari, Chrome Android, and desktop browsers
- "Share to Play" must copy `zaplo.gg/game.html?slug=<slug>&ref=share` to the clipboard
- a "Link copied" toast must appear for 2 seconds on a successful copy
- fire GA4 `game_start` event on iframe load
- fire GA4 `game_end` event on tab close or game change
- fire GA4 `share_click` event on share button click

---

## Static Pages (About, Contact, Privacy, Terms)

Include:

- one column, max-width 720 px
- same header and footer as the rest of the site
- pure text content with H1, H2, paragraph styling only

Requirements:

- privacy policy must disclose GA4 cookies, Microsoft Clarity, and any analytics tools in use
- contact page uses a simple `mailto:hello@zaplo.gg` link only (no form)
- terms page covers acceptable use and disclaimer

---

# Content Requirements

The site must:

- use short, casual headings
- avoid technical or corporate tone
- describe each game in under 60 words
- explain controls in one short line
- support quick scanning over deep reading

Each game card must:

- show a 480×270 px thumbnail
- show the game title (max 26 characters displayed)
- show one category badge
- show an "MP" badge if the game is multiplayer
- link to the game detail page on click

Each game entry must include:

- title
- slug (URL-safe identifier)
- thumbnail image
- category
- short description (under 60 words)
- controls hint (one line)
- iframe or embed URL
- multiplayer flag (true or false)
- up to 4 related games (by category or manual selection)

### Not Allowed

- lorem ipsum in production
- game descriptions over 60 words
- long onboarding or marketing paragraphs
- multi-step explainer text

---

# Visual Requirements

Use visuals to support play, not decoration.

Allowed visuals:

- game thumbnails
- category badges
- multiplayer (MP) badge
- icons 
- one logo wordmark
- one Open Graph card per page
- empty-state illustrations 

Suggested direction:

Home page:

- dark navy background with a subtle lime grid pattern
- glowing accent border on the "Now Playing" tile on hover
- large rounded game cards with a soft tilt on hover

Game page:

- dark surface behind the iframe to reduce glare
- magenta glow on the "Share to Play" button when copied

Category page:

- consistent card sizing
- predictable hover state

Visual style must remain:

- neon
- dark
- consistent across pages

### Not Allowed

- decorative stock photos
- 3D renders unrelated to gameplay
- animated GIFs in the layout (only inside game iframes)
- mascots or characters that distract from games

---

# Design Requirements

Visual style:

- neon
- dark
- modern arcade
- mobile-first

The site should resemble:

- a neon arcade kiosk
- a casual gaming hub for teens and college students
- something between CrazyGames and a curated .io catalog

Avoid:

- casino or gambling aesthetics
- enterprise dashboard layouts
- cluttered sidebars
- dark-pattern monetization

---

# Typography Requirements

Use clean, readable fonts only.

Recommended:

Display / headings:

- Space Grotesk
- Sora

Body text:

- Inter
- Roboto

Requirements:

- single display font + single body font (max two families)
- consistent size scale: 14, 16, 22, 28, 36, 48
- visible body text at all viewport sizes
- minimum 16 px body on mobile
- use `font-display: swap` or self-host fonts

### Not Allowed

- script fonts
- decorative fonts
- handwritten fonts
- more than two font families

---

# Color Requirements

Use no more than:

```text
3 dominant brand colors
```

plus background and text neutrals.

Suggested palette:

| Usage      | Name          | HEX       |
| ---------- | ------------- | --------- |
| Primary    | Electric Lime | `#B6FF3C` |
| Secondary  | Plasma Purple | `#8B5CF6` |
| Accent     | Hot Magenta   | `#FF2E93` |
| Background | Carbon Black  | `#0A0A12` |
| Surface    | Slate Panel   | `#1A1A2E` |
| Text       | Bright White  | `#FAFAFF` |

Requirements:

- WCAG AA contrast on all text
- consistent accent usage (Lime = CTA, Purple = links/active states, Magenta = share and hot tags)
- dark theme by default for V1

### Not Allowed

- rainbow palettes
- neon clashes
- gradient overload
- inconsistent CTA colors

---

# Layout & Spacing Requirements

Pages must maintain:

- 12-column grid on desktop, 4-column on mobile
- 16 px base spacing scale
- max content width of 1280 px
- breathing room around game cards (gap ≥ 16 px)

Requirements:

- one primary CTA per visible fold
- consistent card sizing across pages
- header height fixed at 80 px desktop / 64 px mobile

### Avoid

- horizontal scroll on mobile
- overlapping cards
- inconsistent gutters
- text touching the screen edge

---

# Game Categories

The site must support exactly:

1. Action
2. Multiplayer
3. .io
4. Racing
5. Puzzle
6. Shooting

---

# Responsiveness & Performance Requirements

Site must:

- pass Lighthouse Mobile Performance ≥ 85
- render first paint in under 2 seconds on 4G
- work on screens from 320 px wide upward
- load no more than 220 KB of JavaScript outside game iframes

Requirements:

- defer all non-critical scripts
- lazy-load game thumbnails below the fold
- self-host fonts or use `font-display: swap`
- no console errors on any page

---

# Share to Play Requirements

## Behavior

- a "Share to Play" button appears on every game detail page, below the game title
- clicking the button copies `zaplo.gg/game.html?slug=<slug>&ref=share` to the clipboard
- a "Link copied" toast appears for 2 seconds on a successful copy
- a "Copy failed" toast appears for 2 seconds if the copy is blocked

## Technical

- primary copy method is `navigator.clipboard.writeText()`
- fallback copy method is a hidden textarea with `document.execCommand('copy')`
- a `share_click` GA4 event fires on every click, with the game slug as a parameter
- a visitor landing on a `?ref=share` link plays the game directly on the game detail page

---

# SEO Requirements

- SEO-friendly URLs (e.g. `/game/tank-arena`, `/category/multiplayer`)
- unique `<title>` and `<meta description>` on every page
- Open Graph tags on game detail and category pages
- `sitemap.xml` covering all public-facing pages
- `robots.txt` allowing all crawlers
- canonical tags on filtered or parameterized views

---

# Analytics Requirements

Integrate on every page:

- Google Analytics 4 site tag
- Microsoft Clarity for heatmaps

Custom GA4 events:

| Event | Trigger |
| ---------------- | ---------------------------------- |
| `game_start` | Game iframe loads |
| `game_end` | User leaves game page |
| `share_click` | User clicks Share to Play |
| `category_click` | User selects a category |
| `search_used` | User submits a search query |

Requirements:

- GA4 tag must fire on every page
- defer non-critical analytics scripts
- privacy policy must disclose all tracking tools in use

### Not Allowed

- pop-up ads
- redirect ads
- crypto mining scripts
- email harvesting

---

# Monetization Requirements

- Google AdSense only
- one ad slot on the home page, one above the game iframe on the game detail page
- ad code may be present before AdSense approval is granted

### Not Allowed

- pop-up ads
- interstitial ads
- auto-redirect ads

---

# Asset Usage Requirements

Owner will provide:

- logo concept and brand palette
- the 20 shortlisted games
- all page copy and game descriptions
- the domain `zaplo.gg`, AdSense account, and GA4 property

Developer will produce:

- all HTML, CSS, and JavaScript
- game thumbnails (480×270 PNG)
- empty-state illustrations
- `sitemap.xml` and `robots.txt`

Not Allowed:

- copyrighted brand assets (Mario, Sonic, Pac-Man, Disney, etc.)
- ripped or cracked games
- watermarked or unlicensed game assets
- assets with unclear ownership


---

# Deliverables

Submit exactly:

## Live Website

Quantity:

```text
1
```

Accepted hosts:

- Vercel
- Netlify
- Cloudflare Pages

---

## Source Code Repository

Quantity:

```text
1
```

Accepted formats:

- GitHub repository (public or private)
- a ZIP archive of the same repo

Must include:

- `README.md` with setup and deploy instructions
- complete `/games/` folder or `games.json` catalog file
- all HTML, CSS, and JS files
- `sitemap.xml` and `robots.txt`

---

## Brand Kit

Quantity:

```text
1 folder
```

Must include:

- logo in SVG and PNG (transparent, 512 px and 1024 px)
- favicon
- Open Graph card image (1200 × 630)
- color palette reference

---

# Required Delivery Structure

```text
Zaplo_Website/

├── live/
│   └── live_url.txt

├── source/
│   ├── zaplo-repo/
│   │   ├── index.html
│   │   ├── category.html
│   │   ├── game.html
│   │   ├── about.html
│   │   ├── contact.html
│   │   ├── privacy.html
│   │   ├── terms.html
│   │   ├── 404.html
│   │   ├── assets/
│   │   │   ├── css/
│   │   │   ├── js/
│   │   │   ├── thumbs/
│   │   │   ├── sounds/
│   │   │   └── og/
│   │   ├── games/
│   │   ├── data/
│   │   │   └── games.json
│   │   ├── sitemap.xml
│   │   ├── robots.txt
│   │   ├── README.md
│   └── zaplo-repo.zip

├── brand/
│   ├── logo.svg
│   ├── logo-512.png
│   ├── logo-1024.png
│   ├── favicon.ico
│   └── og-card.png

```

---

# Scope Restrictions

Do NOT include:

1. User accounts, login, or sign-up (public-facing)
2. Backend, API, or database
3. Admin panel or CMS
4. Real-time multiplayer matchmaking over the network
5. Leaderboards or achievement system
6. Chat or friend system
7. Subscription plans or payment integration
8. Native iOS or Android apps
9. Multi-language support
10. AI-powered recommendations
11. Comments, ratings, or reviews
12. Email collection or newsletter forms
13. Pop-up ads or interstitial ads
14. Crypto or Web3 integrations
15. WordPress, Wix, or any third-party page builder
16. In-house game development

---

# Acceptance Criteria

Final delivery is accepted only when ALL of the following are true:

1. All 20 games load without console errors and are playable end-to-end on Chrome, Firefox, Safari, and Edge.
2. Category filtering and search work client-side without page reloads.
3. The "Share to Play" button copies the correct URL with `?ref=share` and shows a 2-second toast.
4. Lighthouse Mobile Performance ≥ 85.
5. First Contentful Paint under 2 seconds on simulated 4G.
6. GA4 captures `game_start`, `game_end`, `share_click`, `category_click`, and `search_used` events.
7. AdSense code is present on the home page and every game detail page.
8. `sitemap.xml` covers all public-facing pages and `robots.txt` is present.
9. About, Privacy Policy, Terms, and Contact pages are live.
10. `README.md` includes working setup and deploy instructions.
11. No horizontal scroll on any viewport from 320 px upward.
12. Fullscreen gameplay works on iOS Safari, Chrome Android, and desktop.

---

# Delivery Terms

Single-delivery project.

Revisions are not required unless:

- a listed deliverable is missing
- the site fails to load on a mainstream browser
- the "Share to Play" feature does not copy the correct URL
- GA4 events are not firing
- Lighthouse Mobile Performance falls below 70
- any acceptance criterion above is unmet at handover

Final delivery is accepted only after:

- live site is reachable at the provided URL (zaplo.gg)
- complete source repository or ZIP is handed over
- brand kit folder is included
- all acceptance criteria above are met

---

# Final Goal

The final result should function as:

```text
A fast, neon, share-friendly browser arcade with 20 games and a working
Share to Play loop that lets any visitor discover, play, and share HTML5
games instantly, with no account and no downloads.
```

The website should:

- load instantly on any modern device
- let any visitor play within two clicks of landing
- let any visitor share a game link in one click
- monetize cleanly through one AdSense banner per page
- look like a neon arcade without looking childish
- remain deployable on a free or low-cost hosting tier
- serve as a real, usable product ready for launch
