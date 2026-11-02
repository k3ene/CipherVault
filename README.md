# CipherVault Tech Solutions – Website PoE

> **Module:** WEDE5020 – Web Development (Introduction)  
> **Student name:** Khumo Boyd Selolo
> **Student number:** ST10509276 
> **Live site:**  
> **Repository:** (https://github.com/k3ene/CipherVault)

---

## 1. Project overview

CipherVault Tech Solutions (Pty) Ltd is a **hypothetical** South African cybersecurity business that helps individuals and small businesses protect their digital information through consulting, awareness training, risk assessments, password guidance and backup advice. The organisation, staff, addresses and contact details are fictional and exist for this educational project only.

The website is a five-page, responsive, accessible and search-engine-optimised site built with HTML5, CSS3 and vanilla JavaScript (no frameworks), plus the Leaflet library for the interactive map (Agafonkin, n.d.).

### Website goals and objectives

- Increase public awareness of CipherVault and its services.
- Generate customer enquiries and consultation bookings.
- Educate visitors about cybersecurity threats and prevention.
- Build trust through clear content and professional branding.

### Key performance indicators (from the approved proposal)

| KPI | Target |
| --- | --- |
| Website visitors | About 5 000 in the first six months |
| Customer enquiries | At least 100 per month |
| Enquiry-to-client conversion | Minimum 10% |
| Newsletter growth | 20% per quarter |
| Customer satisfaction | Above 90% |

### Timeline and milestones

| Week | Activity |
| --- | --- |
| 1 | Project planning and requirement analysis |
| 2 | Research and wireframe development |
| 3 | User interface design |
| 4 | Front-end development |
| 5 | Integration and feature work |
| 6 | Testing and debugging |
| 7 | Final review, deployment and documentation |



---

## 2. Sitemap and folder structure

```text
Home (index.html)
├── About Us (about.html)
├── Services (services.html)
├── Enquiry (enquiry.html)
└── Contact (contact.html)
Also: sitemap.html (visual sitemap), 404.html (error page)
```

```text
CipherVault_PoE_Project/
├── index.html  about.html  services.html  enquiry.html  contact.html
├── sitemap.html            # visual sitemap page
├── 404.html                # friendly error page (used by GitHub Pages)
├── robots.txt              # crawler instructions
├── sitemap.xml             # XML sitemap for search engines
├── css/style.css           # single external stylesheet
├── js/
│   ├── data.js             # services, pricing rules and tips (single source of truth)
│   └── script.js           # all interactivity (commented by section)
├── images/                 # site images + favicon.svg
├── wireframes/             # low-fidelity wireframes (Part 1)
├── Document/               # Part 1 proposal
└── README.md
```

---

## 3. Part 1 details – Foundation

- Five core pages created with semantic HTML5 (`header`, `nav`, `main`, `section`, `article`, `footer`).
- Consistent navigation menu on every page, with the current page highlighted.
- File and folder structure organised into `css`, `js`, `images`, `wireframes` and `Document`.
- Website Project Proposal and five low-fidelity wireframes included.
- Content is original text written for the fictional organisation. Images are listed in the table below.

| Image file | Used on | Alt text purpose |
| --- | --- | --- |
| `hero-cybersecurity.jpg` | Home, About gallery | Shield protecting digital systems |
| `cybersecurity-protection.jpg` | Home, Enquiry, About gallery | Hands protecting a security shield |
| `about-digital-security.jpg` | About, About gallery | Laptop showing digital security |
| `team-ciphervault.jpg` | About, About gallery | The CipherVault team |
| `map-locations.jpg` | Contact (fallback only) | Stylised map with two pins |



---

## 4. Part 2 details – Visuals and responsive design

- One external stylesheet (`css/style.css`) linked from every page, with a CSS reset, design tokens (CSS variables), typography (Poppins headings, Inter body) and a navy-and-gold colour scheme.
- Layout built with CSS Grid and Flexbox.
- Hover, focus and active states on links, buttons, cards and form fields.
- Responsive breakpoints at 1000px, 800px and 480px: multi-column layouts collapse to a single column, the navigation becomes a toggle menu on mobile, and images scale fluidly.

> **TODO (Part 2 evidence):** add screenshots of the site at desktop, tablet and mobile sizes from your **live** site (browser developer tools device toolbar), and link them here, for example `screenshots/home-mobile.png`.

---

## 5. Part 3 details – Functionality and SEO

### 5.1 Interactive elements

| Feature | Where | How it works |
| --- | --- | --- |
| Accordion (FAQ) | Services | Buttons toggle panels with `aria-expanded`; one panel open at a time. |
| Tabs ("How we work") | About | Click or use arrow keys, Home and End; uses `role="tablist"`. |
| Modal dialog | Services | "Details" buttons open a native `<dialog>` filled from `data.js` (Mozilla Developer Network, n.d.a). |
| Gallery with lightbox | About | Thumbnails open a larger view with previous/next buttons, arrow keys, captions and a counter. Links work without JavaScript. |
| Interactive map | Contact | Leaflet map with two office markers, popups, "Show on map" and "Show both offices" buttons. A static image is shown if the map cannot load. |
| Animations and transitions | All pages | Card reveal on scroll (IntersectionObserver), hover transitions, modal and accordion fades. All disabled for users who prefer reduced motion. |
| Rotating security tip | Home | A daily tip, with a button to cycle through more. |

### 5.2 Dynamic content and search

The Services page builds its cards from the `SERVICES` array in `js/data.js`, using DOM methods (not `innerHTML`). Visitors can:

- **Search** by any words (all words must match name, category, description or keywords).
- **Filter** by category.
- **Sort** by name (A–Z, Z–A) or price (low–high, high–low).

A live result count and a "no results" message with a reset button are included. The enquiry form's service list is generated from the same data, so prices and names always match.

### 5.3 Forms and validation

Both forms use `novalidate` with custom JavaScript validation, based on the HTML5 constraint-validation approach (Mozilla Developer Network, n.d.b). Errors appear under each field, are announced to screen readers (`role="alert"`, `aria-invalid`), and are re-checked as the user corrects them.

| Validation | Rule |
| --- | --- |
| Name | 2–60 letters, spaces, hyphens, apostrophes |
| Email | Must match a valid email pattern |
| Phone (optional) | South African format, e.g. `011 555 0142` or `+27 11 555 0142` |
| Quantity | Whole number 1–500 |
| Preferred date | After today, weekdays only, within 12 months |
| Message | Enquiry 10–500 characters, contact 10–1000 characters, with live counter |
| Consent | Must be ticked |

**Enquiry form (`enquiry.html`)** – once valid, the input is processed and the visitor receives a response about **cost and availability**:

- Price = base price + extra units × per-unit price.
- Discounts: individual/student 10%, non-profit/school 15%. Priority booking adds 25% and halves the waiting time.
- VAT of 15% is added (South African Revenue Service, n.d.).
- Availability is calculated from today in **working days** and compared with the preferred date. The visitor is told if the date is available or what the earliest date is.

**Contact form (`contact.html`)** – once valid, the details are compiled into an email (recipient chosen by the selected office, subject, and formatted body). A preview is shown, and the **Send email** button opens the visitor's own email app with everything filled in using a `mailto:` link. Recipient addresses are set in `OFFICE_EMAILS` at the top of `js/script.js`.

### 5.4 Search engine optimisation (SEO)

Following Google Search Central guidance (Google Search Central, n.d.a; n.d.b; n.d.c):

- **Title tags and meta descriptions:** unique for every page.
- **Meta keywords:** page-specific keywords on every page.
- **Header tags:** one `h1` per page, with `h2`/`h3` used in order.
- **Image optimisation:** descriptive file names, meaningful `alt` text, `width`/`height` attributes and `loading="lazy"` below the fold.
- **URL structure:** short, clean, descriptive file names (`services.html`, `enquiry.html`).
- **Internal linking:** navigation, footer links, calls to action, and links between related pages.
- **Mobile-friendly:** responsive design with a viewport tag.
- **Local SEO:** Johannesburg and Pretoria offices described in JSON-LD structured data (Schema.org, n.d.) and on the Contact page.
- **robots.txt** and **sitemap.xml** created (Sitemaps.org, n.d.).
- **Open Graph tags** and a canonical link on each page.
- **Social media / backlinks (off-page plan):** share the live link on LinkedIn and relevant community groups, and ask local business directories to link to the site.

### 5.5 Page speed and security

- Scripts use `defer`; images are lazy-loaded and dimensioned to prevent layout shift; fonts use `display=swap`.
- A Content-Security-Policy meta tag limits scripts, styles, fonts, images and map tiles to the sources the site actually uses (Mozilla Developer Network, n.d.c).
- The Leaflet files are loaded with Subresource Integrity hashes.
- All user-entered text is displayed with `textContent`, so it can never run as HTML.
- Input length limits, `autocomplete` attributes and a referrer policy are set.

### 5.6 Accessibility

Skip link, visible keyboard focus, labelled form controls, error messages tied to fields, ARIA patterns for the accordion and tabs (W3C Web Accessibility Initiative, n.d.a; n.d.b), keyboard-operable lightbox and modal, reduced-motion support, and darker gold text on light backgrounds to meet the contrast guideline (W3C Web Accessibility Initiative, n.d.c).

---

## 6. Running the website locally

1. Open the project folder in Visual Studio Code.
2. Install the **Live Server** extension and choose *Open with Live Server* on `index.html` (or double-click `index.html`).
3. An internet connection is needed for Google Fonts and the map tiles.

## 7. Testing

The checks below were run with automated browser tests in Chromium on 2 November 2026.

| Test | Result |
| --- | --- |
| Every page loads with no console errors | Passed |
| Services search, filter and sort | Passed |
| Modal, accordion, tabs, lightbox (mouse and keyboard) | Passed |
| Enquiry validation (invalid and valid input) and quote totals | Passed |
| Contact validation and compiled email link | Passed |
| No horizontal scrolling at 390px wide on every page | Passed |


## 8. Deployment



1. Push the project to the GitHub repository (the repository root must contain `index.html`).
2. On GitHub: **Settings → Pages → Build and deployment → Deploy from a branch → `main` / `(root)` → Save** (GitHub, n.d.).
3. Wait for the green "Your site is live" message and copy the link into the top of this README.
4. Replace `https://YOUR-USERNAME.github.io/ciphervault` in all `.html` files, `robots.txt` and `sitemap.xml` with your real link.

## 9. Known limitations

- The website has no server. The contact form therefore opens the visitor's email app (`mailto:`) rather than sending the email itself, and the enquiry is processed in the browser. Nothing is stored.
- Marker positions on the map are approximate because the offices are fictional.

---

## 10. Changelog

### Part 3 – 2 November 2026

#### Feedback from Part 2



| Feedback received | Change made | File(s) |
| --- | --- | --- |
| *(example) Navigation not clear on mobile* | *Added toggle menu with Escape-to-close* | `css/style.css`, `js/script.js` |

#### New features and improvements

- **Added** `js/data.js` holding the services catalogue, pricing rules and security tips.
- **Rewrote** `js/script.js` into commented sections (navigation, services, accordion, tabs, lightbox, forms, map, animation).
- **Services page:** cards now generated dynamically; added search, category filter, sorting, result count, "no results" message and a details modal.
- **Services page:** added an FAQ accordion.
- **About page:** added "How we work" tabs and an image gallery with a lightbox.
- **Home page:** added a rotating security tip.
- **Contact page:** replaced the static map image with an interactive Leaflet map with two office markers; kept the image as a fallback; added "Show on map" buttons.
- **Enquiry form:** added phone, client type, quantity, preferred date and booking speed; custom validation with inline error messages; instant quote (price, discounts, VAT) and availability response.
- **Contact form:** added office, phone and consent fields; custom validation; compiled email preview with a "Send email" `mailto:` link, copy button and character counter.
- **SEO:** unique titles, meta descriptions and keywords for every page; canonical and Open Graph tags; JSON-LD local business data; descriptive alt text; image dimensions and lazy loading; created `robots.txt`, `sitemap.xml` and `images/favicon.svg`.
- **Security:** added Content-Security-Policy, referrer policy, Subresource Integrity on Leaflet, and safe text rendering.
- **Accessibility:** skip link, `aria-current`, `aria-expanded`, form labels linked to errors, improved gold-on-white text contrast.
- **Fixes:** unified the service name "Digital Risk Assessment" across pages; corrected the Sitemap page footer email (was `Sandton@…`); made footer email a working link; added `name`, `type` and `autocomplete` attributes to all form fields (some inputs had none); added a 404 page.
- **Responsive:** added breakpoints for the new components (gallery, tabs, modal, lightbox, quote table, map).

### Part 2 (feedback from Part 1 and CSS work)



### Part 1 – Initial build (September 2026)

- Created five-page responsive website.
- Added image assets and alt text.
- Added JavaScript search/filter and form validation.
- Added sitemap, proposal and wireframes.

---

## 11. AI usage

AI tools were used during Part 3. Details, the prompts used and the screenshots are in the AI disclosure annexe: [`AI_DISCLOSURE.md`](AI_DISCLOSURE.md). The AI tool is referenced as Anthropic (2026) in the reference list.

---

## 12. References

Harvard style, adapted for the IIE. Listed alphabetically.

Agafonkin, V. n.d. *Leaflet quick start guide*. [Online]. Available at: https://leafletjs.com/examples/quick-start/ [Accessed 2 November 2026].

Anthropic. 2026. *Claude Sonnet 5.5* [Large language model]. [Online]. Available at: https://claude.ai [Accessed 2 November 2026].

CodingLab. 2022. *Button click animation in HTML CSS & JavaScript*. [Video]. 28 December. Available at: https://www.youtube.com/watch?v=F7iFnhSZe7o [Accessed 17 September 2026].

Freefrontend. n.d. *CSS 3D: free examples and code snippets*. [Online]. Available at: https://freefrontend.com/css-3d-examples/ [Accessed 17 September 2026].

GitHub. n.d. *Creating a GitHub Pages site*. [Online]. Available at: https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site [Accessed 2 November 2026].

Google. 2024. *Google Fonts API: getting started*. [Online]. Available at: https://developers.google.com/fonts/docs/getting_started [Accessed 7 August 2026].

Google. 2025a. *Firebase documentation*. [Online]. Available at: https://firebase.google.com/docs [Accessed 7 August 2026].

Google. 2025b. *Firebase fundamentals*. [Online]. Available at: https://firebase.google.com/docs/guides [Accessed 7 August 2026].

Google. 2026. *Material Design 3*. [Online]. Available at: https://m3.material.io/ [Accessed 7 August 2026].

Google Search Central. n.d.a. *Build and submit a sitemap*. [Online]. Available at: https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap [Accessed 2 November 2026].

Google Search Central. n.d.b. *Introduction to robots.txt*. [Online]. Available at: https://developers.google.com/search/docs/crawling-indexing/robots/intro [Accessed 2 November 2026].

Google Search Central. n.d.c. *SEO starter guide*. [Online]. Available at: https://developers.google.com/search/docs/fundamentals/seo-starter-guide [Accessed 2 November 2026].

Mozilla Developer Network. n.d.a. *HTMLDialogElement: showModal() method*. [Online]. Available at: https://developer.mozilla.org/en-US/docs/Web/API/HTMLDialogElement/showModal [Accessed 2 November 2026].

Mozilla Developer Network. n.d.b. *Client-side form validation*. [Online]. Available at: https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation [Accessed 2 November 2026].

Mozilla Developer Network. n.d.c. *Content-Security-Policy (CSP) header*. [Online]. Available at: https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy [Accessed 2 November 2026].

OpenStreetMap contributors. n.d. *Copyright and licence*. [Online]. Available at: https://www.openstreetmap.org/copyright [Accessed 2 November 2026].

OWASP Foundation. 2026. *OWASP Foundation*. [Online]. Available at: https://owasp.org/ [Accessed 7 August 2026].

Schema.org. n.d. *ProfessionalService*. [Online]. Available at: https://schema.org/ProfessionalService [Accessed 2 November 2026].

Sitemaps.org. n.d. *Sitemaps XML format*. [Online]. Available at: https://www.sitemaps.org/protocol.html [Accessed 2 November 2026].

South African Revenue Service. n.d. *Value-Added Tax (VAT)*. [Online]. Available at: https://www.sars.gov.za/types-of-tax/value-added-tax/ [Accessed 2 November 2026].

W3C. 2026. *Web standards*. [Online]. Available at: https://www.w3.org/standards/ [Accessed 7 August 2026].

W3C Web Accessibility Initiative. n.d.a. *Accordion pattern*. [Online]. Available at: https://www.w3.org/WAI/ARIA/apg/patterns/accordion/ [Accessed 2 November 2026].

W3C Web Accessibility Initiative. n.d.b. *Tabs pattern*. [Online]. Available at: https://www.w3.org/WAI/ARIA/apg/patterns/tabs/ [Accessed 2 November 2026].

W3C Web Accessibility Initiative. n.d.c. *Understanding Success Criterion 1.4.3: Contrast (Minimum)*. [Online]. Available at: https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html [Accessed 2 November 2026].
