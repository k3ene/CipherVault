# CipherVault Tech Solutions — Website PoE

A five-page responsive website built for CipherVault Tech Solutions, a fictional cybersecurity and digital protection company, as part of a Portfolio of Evidence (PoE) submission.

## Tech stack

- HTML5
- CSS3 (custom properties, Flexbox/Grid, no framework)
- Vanilla JavaScript (no libraries or build tools)

## Included

- 5 required core pages: Home, About Us, Services, Enquiry, Contact
- Sitemap
- Responsive CSS (breakpoint at 800px)
- JavaScript service filtering and form validation
- 5 website images in `images/`
- 5 low-fidelity wireframe images in `wireframes/`
- Proposal document in `Document/`
- references website on mobile/tablet images in `Document/`
- README and changelog

## Project structure

```
CipherVault_PoE_Project/
├── index.html
├── about.html
├── services.html
├── enquiry.html
├── contact.html
├── sitemap.html
├── css/
│   └── style.css
├── js/
│   └── script.js
├── images/
├── wireframes/
├── Document/
│   └── Proposal.pdf
└── README.md
```

## How to view the site

This is a static site — no build step or server required.

1. Download/clone the repository.
2. Open `index.html` directly in a browser (double-click it, or right-click → Open with → your browser).
3. Navigate the site using the nav bar; all pages and assets are linked with relative paths, so the folder structure above must stay intact.

## Website images

1. `hero-cybersecurity.jpg` — Home
2. `cybersecurity-protection.jpg` — Home / Services / Enquiry
3. `about-digital-security.jpg` — About
4. `team-ciphervault.jpg` — About
5. `map-locations.jpg` — Contact

## Notes

The organisation, staff, addresses and contact details are fictional for an educational project. The five website images were cropped from the supplied CipherVault project artwork and placed into the appropriate pages.

## Changelog

### v1.1 — UI/UX polish pass
- Fixed a bug where the "Home" nav link never received its active state on the homepage (`data-page` mismatch between `index.html` and `script.js`).
- Fixed the sitemap page incorrectly reporting itself as the home page for nav-highlighting purposes.
- Added hover/active states to buttons and cards (elevation, shadow, gold border accent).
- Added a subtle scroll-reveal fade-in for cards.
- Added a restrained ambient glow behind the hero image (CSS-only).
- Improved mobile navigation: smoother open animation, auto-closes after a link is tapped.
- Added visible keyboard focus states (`:focus-visible`) across nav links, buttons, and form fields for accessibility.
- Added `prefers-reduced-motion` support so all animation can be disabled by user/OS preference.
- Minor spacing and typography refinements (section padding, card padding, heading letter-spacing).

### v1.0 — Initial build
- Created five-page responsive website.
- Added image assets and alt text.
- Added JavaScript search/filter and form validation.
- Added sitemap, proposal and wireframes.
