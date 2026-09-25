# Berelian Halls

> Official website of Berelian Halls — a luxury event and hospitality venue in Qazvin, Iran.

**برلیان** یک وب‌سایت استاتیک دو زبانه برای معرفی مجموعه تالارهای برلیان، فضاهای برگزاری مراسم، خدمات، نمونه‌کارها، منوها و راه‌های ارتباطی است.

🌐 **Website:** https://berelianhalls.com

---

## Overview

Berelian Halls is a static, responsive website built for the official web presence of the Berelian event venue in Qazvin.

The website provides dedicated pages for:

* Home
* About the venue
* Our work / event portfolio
* Our spaces / halls
* One Dining
* Menus
* Contact
* Persian and English content

The project focuses on a visual, image-driven presentation suitable for an event and hospitality brand.

---

## Features

### Website

* Responsive design for desktop, tablet and mobile
* Persian RTL interface
* English pages
* Responsive navigation
* Hero video presentation
* Image-based venue sections
* Event and portfolio galleries
* Hall / venue presentation
* Menu presentation
* Contact page
* Direct telephone links
* SEO metadata
* Open Graph metadata
* Twitter Card metadata
* Schema.org structured data
* Smooth scrolling
* Scroll-based animations

### Visual Design

The visual system uses:

* Tailwind CSS
* AzarMehr font
* Custom gold accent color
* Full-width image sections
* Responsive typography
* Background/parallax sections
* AOS animations
* Local image and video assets

---

## Technology Stack

| Technology         | Purpose                             |
| ------------------ | ----------------------------------- |
| HTML5              | Page structure                      |
| Tailwind CSS 3.4.x | Styling and responsive layout       |
| JavaScript         | Client-side interactions            |
| AOS                | Scroll animations                   |
| CSS                | Custom styling and font definitions |
| Nginx              | Static web server                   |
| Docker             | Containerized static hosting        |

Tailwind is configured to scan HTML and JavaScript files in the repository:

```text
./**/*.{html,js}
```

The project also defines the `AzarMehr` font family in Tailwind configuration.

---

## Repository Structure

```text
BerelianHalls/
│
├── .github/
│   └── workflows/
│
├── .vscode/
│
├── en/
│   └── English website pages and assets
│
├── fonts/
│   └── AzarMehr font files
│
├── images/
│   └── Website images and visual assets
│
├── our-space/
│   └── Individual hall pages
│
├── our-work/
│   └── Event / portfolio related pages
│
├── videos/
│   └── Hero and website videos
│
├── about.html
├── contactus.html
├── index.html
├── menu.html
├── one-dining.html
├── our-space.html
├── our-work.html
│
├── input.css
├── output.css
├── tailwind.config.js
│
├── docker-compose.yml
├── package.json
├── package-lock.json
├── .gitignore
├── LICENSE
└── README.md
```

---

## Requirements

For local development you need:

* Git
* Node.js
* npm
* Docker (optional, only required for containerized local serving)

Tailwind CSS is installed as a development dependency.

---

## Installation

Clone the repository:

```bash
git clone https://github.com/iranpsc/BerelianHalls.git
```

Enter the project directory:

```bash
cd BerelianHalls
```

Install dependencies:

```bash
npm ci
```

If `package-lock.json` is intentionally changed, use:

```bash
npm install
```

and commit the corresponding lockfile changes.

---

## Tailwind CSS

The source stylesheet is:

```text
input.css
```

The generated stylesheet is:

```text
output.css
```

Tailwind is configured through:

```text
tailwind.config.js
```

For a one-time CSS generation:

```bash
npx tailwindcss -i ./input.css -o ./output.css
```

For development with automatic regeneration:

```bash
npx tailwindcss -i ./input.css -o ./output.css --watch
```

### Important

`output.css` is consumed directly by the HTML pages.

If a contribution changes:

```text
input.css
tailwind.config.js
HTML class names
```

the generated CSS must be regenerated and the resulting `output.css` change must be reviewed.

---

## Local Development

Because the project is a static website, no application server or database is required.

You can serve the repository with any static HTTP server.

For example, using Python:

```bash
python -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

Do not use `file://` URLs for development when testing navigation, media, relative assets or browser behavior.

---

## Docker

The repository includes a Docker Compose configuration using Nginx Alpine.

Start the container:

```bash
docker compose up -d
```

The container serves the repository as static files through Nginx.

The current Compose configuration mounts the repository read-only into:

```text
/usr/share/nginx/html
```

Inside the container, Nginx listens on port:

```text
80
```

If you need the website to be directly accessible from the host machine, configure an explicit host-to-container port mapping in the Compose configuration rather than assuming `expose` publishes the port.

Stop the container:

```bash
docker compose down
```

---

## Website Pages

### Main Website

```text
/index.html
```

The homepage contains:

* navigation;
* hero video;
* venue introduction;
* hall highlights;
* contact section;
* portfolio content;
* responsive sections.

### About

```text
/about.html
```

Contains information about:

* Berelian;
* the venue;
* suppliers;
* team;
* clients;
* collaboration.

### Our Work

```text
/our-work.html
```

Contains event and portfolio categories such as:

* Weddings
* Iftar
* عقد
* Corporate events
* Memorial events
* Gatherings and conferences

### Our Spaces

```text
/our-space.html
```

Contains the venue/hall presentation.

Individual hall pages are located under:

```text
/our-space/
```

### One Dining

```text
/one-dining.html
```

Contains the One Dining presentation.

### Menu

```text
/menu.html
```

Contains the available menu content.

### Contact

```text
/contactus.html
```

Contains contact information and communication options.

---

## Internationalization

The project contains Persian and English page structures.

Persian pages use:

```html
<html dir="rtl" lang="fa">
```

English pages should use the corresponding English language direction and language declaration.

When modifying multilingual pages:

* keep equivalent navigation between languages;
* update both language versions when the same content changes;
* keep `hreflang` relationships synchronized;
* verify relative paths;
* verify canonical URLs;
* verify language-specific metadata;
* verify that translated pages point to the correct translated destination.

Do not assume that changing a Persian page automatically updates the English version.

---

## SEO

The website includes SEO-related metadata including:

* `<title>`
* meta description
* robots
* canonical URLs
* Open Graph
* Twitter Cards
* `hreflang`
* Schema.org JSON-LD

When changing page content, review the corresponding metadata.

### Structured Data

Structured data must describe the actual venue and actual website content.

Do not introduce placeholder:

* addresses;
* phone numbers;
* coordinates;
* social profiles;
* opening hours;
* business information.

All structured data must match the real business information.

---

## Images and Videos

The website uses local visual assets from:

```text
images/
videos/
```

Before adding a new asset:

* use an appropriate format;
* optimize large images;
* avoid unnecessarily large dimensions;
* use descriptive filenames where practical;
* provide meaningful `alt` text for content images;
* avoid duplicating existing assets;
* verify mobile loading performance.

Hero videos should be reviewed for:

* file size;
* autoplay behavior;
* mobile compatibility;
* muted playback;
* poster image;
* loading impact;
* network usage.

Large media files can have a significant effect on page performance.

---

## CSS Guidelines

Prefer Tailwind utility classes for layout and component styling when the existing design system supports the requirement.

Custom CSS should be added to:

```text
input.css
```

when a utility class is not appropriate or when a reusable project-level rule is required.

Avoid introducing duplicate styles for the same behavior.

Keep:

* typography;
* spacing;
* colors;
* responsive breakpoints;
* animations

consistent with the existing visual system.

---

## JavaScript Guidelines

Keep JavaScript focused on behavior that cannot be implemented cleanly with HTML and CSS.

Before adding JavaScript:

1. Check whether the behavior can be implemented with existing markup.
2. Reuse existing patterns where possible.
3. Avoid unnecessary global variables.
4. Avoid duplicate event listeners.
5. Avoid unnecessary DOM queries.
6. Clean up timers/listeners when applicable.
7. Preserve keyboard accessibility.
8. Avoid blocking the initial page render.

Interactive behavior should remain compatible with the static hosting model.

---

## Accessibility

All contributions should preserve accessible behavior.

Check:

* semantic HTML;
* heading hierarchy;
* meaningful link text;
* `alt` text;
* button labels;
* keyboard navigation;
* focus states;
* sufficient contrast;
* mobile navigation;
* video controls where appropriate;
* reduced-motion considerations.

Do not use an element with an `href` only as a visual button when a real `<button>` is appropriate.

---

## Performance

This is an image- and video-heavy website, so performance is an important part of every contribution.

Avoid:

* unnecessarily large images;
* unnecessary video downloads;
* duplicate assets;
* unused CSS;
* unnecessary third-party libraries;
* blocking JavaScript;
* excessive animations;
* loading resources that are not required for the current page.

When changing the hero or major visual sections, test:

* mobile;
* desktop;
* slow network;
* first load;
* repeat load.

---

## Security

This project is primarily a static website.

Nevertheless:

* never commit credentials;
* never commit private keys;
* never commit API secrets;
* do not place sensitive information in HTML;
* do not expose internal infrastructure details unnecessarily;
* review external scripts before adding them;
* use trusted HTTPS sources for third-party resources.

Static files are publicly accessible once deployed. Anything committed to the repository should therefore be treated as potentially public.

---

## Git Workflow

Create a dedicated branch for each change.

Recommended naming:

```text
feature/<description>
fix/<description>
refactor/<description>
docs/<description>
style/<description>
performance/<description>
seo/<description>
```

Examples:

```text
feature/update-contact-section
fix/mobile-navigation
fix/hreflang-links
seo/fix-venue-schema
performance/optimize-hero-video
docs/update-project-readme
```

Keep branches focused and short-lived.

---

## Commit Convention

Use clear, focused commit messages.

Recommended format:

```text
<type>: <description>
```

Examples:

```text
feat: add new hall section
fix: correct mobile navigation links
fix: update contact information
perf: optimize hero video loading
seo: fix venue structured data
style: improve responsive hall layout
docs: update project documentation
refactor: simplify navigation markup
```

Avoid:

```text
update
changes
fix
test
final
new version
```

---

## Pull Requests

Before opening a Pull Request:

1. Verify the affected pages locally.
2. Regenerate Tailwind CSS if required.
3. Check both Persian and English versions.
4. Test internal links.
5. Test images and videos.
6. Test mobile navigation.
7. Review SEO metadata.
8. Review structured data.
9. Check for accidental generated or unrelated changes.
10. Review the complete diff.

The Pull Request should explain:

* what changed;
* why it changed;
* which pages are affected;
* how it was tested;
* whether CSS was regenerated;
* whether SEO/schema changed;
* whether deployment configuration changed.

---

## Deployment

The repository contains Docker configuration for Nginx-based static hosting.

Deployment should be performed from an approved branch or release process.

Before deployment:

```bash
git status
git diff
```

Verify:

* required HTML files exist;
* `output.css` is up to date;
* images exist;
* videos exist;
* relative links work;
* multilingual links work;
* Docker configuration is valid.

After deployment, verify:

* homepage;
* navigation;
* English pages;
* contact page;
* menu;
* venue pages;
* portfolio;
* images;
* videos;
* responsive layout.

---

## Troubleshooting

### Tailwind classes are not working

Regenerate CSS:

```bash
npx tailwindcss -i ./input.css -o ./output.css
```

Check:

```text
tailwind.config.js
input.css
output.css
```

### Changes are not visible

Hard refresh the browser and verify that the generated `output.css` was actually updated.

### Images are missing

Check:

* relative path;
* filename capitalization;
* file extension;
* directory name;
* deployment path.

### English page is broken

Check:

* corresponding file under `en/`;
* relative asset paths;
* navigation links;
* `hreflang`;
* canonical URL.

### Docker page is not reachable

Check:

```bash
docker compose ps
```

and verify that the Compose configuration exposes/publishes the required host port.

---

## Project Status

The project is an actively maintained static website for Berelian Halls.

The repository should be considered the source of truth for:

* website markup;
* styling source;
* generated CSS;
* static assets;
* website content;
* Docker static-serving configuration.

Production deployment infrastructure outside this repository is not automatically represented by the local Docker configuration.

---

## Contributing

Contributions should follow the project's contribution guidelines.

See:

```text
CONTRIBUTING.md
```

Before opening a Pull Request, make sure the change is:

* scoped;
* tested;
* responsive;
* accessible;
* SEO-safe;
* multilingual-safe;
* performance-conscious.

---

## License

This project is distributed under the license provided in:

```text
LICENSE
```

See the license file in the repository for the complete terms.

---

## Repository

GitHub:

https://github.com/iranpsc/BerelianHalls

Website:

https://berelianhalls.com
