# Contributing to Berelian Halls

Thank you for contributing to the Berelian Halls website.

This repository contains the static website for **Berelian Halls**, including its HTML pages, Tailwind CSS source, generated CSS, images, videos, fonts, multilingual pages and Docker/Nginx static hosting configuration.

Because this is a public-facing website, contributions should preserve visual consistency, responsive behavior, accessibility, SEO, multilingual navigation and performance.

---

## Table of Contents

* [Project Scope](#project-scope)
* [Repository Structure](#repository-structure)
* [Before You Start](#before-you-start)
* [Development Setup](#development-setup)
* [Tailwind CSS](#tailwind-css)
* [Working With HTML](#working-with-html)
* [Multilingual Pages](#multilingual-pages)
* [Images and Media](#images-and-media)
* [SEO and Structured Data](#seo-and-structured-data)
* [Accessibility](#accessibility)
* [Performance](#performance)
* [Docker](#docker)
* [Branching](#branching)
* [Commit Messages](#commit-messages)
* [Pull Requests](#pull-requests)
* [Testing Checklist](#testing-checklist)
* [Content and Business Information](#content-and-business-information)
* [Security](#security)
* [Review Standards](#review-standards)
* [Contribution Checklist](#contribution-checklist)

---

## Project Scope

BerelianHalls is a static website.

The project does not use:

* React;
* Next.js;
* a backend application;
* a database;
* server-side rendering.

The main technologies are:

```text
HTML
Tailwind CSS
JavaScript
AOS
Nginx
Docker
```

The website is composed of independent HTML pages and static assets.

Do not introduce a frontend framework or backend dependency for a small website change unless there is an explicit architectural decision to do so.

---

## Repository Structure

Important project areas include:

```text
index.html
about.html
contactus.html
menu.html
one-dining.html
our-space.html
our-work.html

en/
fonts/
images/
videos/

our-space/
our-work/

input.css
output.css
tailwind.config.js

docker-compose.yml
package.json
package-lock.json
```

Before changing a page, identify whether an equivalent English page or related nested page also needs to be updated.

---

## Before You Start

Before making a change:

```bash
git status
```

Make sure the working tree is clean or that existing local work is intentionally preserved.

Review the affected page and related pages.

For example, if changing the navigation:

```text
index.html
about.html
contactus.html
menu.html
one-dining.html
our-space.html
our-work.html
en/*
```

should be considered.

Do not update only one page when the same shared navigation exists across multiple pages.

---

## Development Setup

Clone the repository:

```bash
git clone https://github.com/iranpsc/BerelianHalls.git
cd BerelianHalls
```

Install dependencies:

```bash
npm ci
```

For development with automatic Tailwind regeneration:

```bash
npx tailwindcss -i ./input.css -o ./output.css --watch
```

Serve the website through an HTTP server rather than opening HTML files directly with `file://`.

For example:

```bash
python -m http.server 8000
```

Then visit:

```text
http://localhost:8000
```

---

## Tailwind CSS

The project uses Tailwind CSS.

Source:

```text
input.css
```

Configuration:

```text
tailwind.config.js
```

Generated output:

```text
output.css
```

The Tailwind content configuration currently scans:

```text
./**/*.{html,js}
```

When adding Tailwind classes, regenerate the output CSS:

```bash
npx tailwindcss -i ./input.css -o ./output.css
```

Then inspect:

```bash
git diff -- output.css
```

Do not manually edit generated `output.css` to implement a permanent styling change.

Make the source change in:

```text
input.css
```

or the appropriate HTML/Tailwind configuration.

---

## HTML Guidelines

Use semantic HTML where possible.

Prefer:

```html
<header>
<nav>
<main>
<section>
<article>
<footer>
```

over generic containers when the semantic element describes the content.

Maintain:

* one meaningful `<h1>` per page where appropriate;
* logical heading hierarchy;
* valid links;
* descriptive image `alt` attributes;
* accessible buttons;
* valid document structure.

Avoid introducing unnecessary inline styles when an existing Tailwind utility or reusable CSS rule can provide the same result.

---

## Navigation

Navigation is duplicated across multiple static HTML pages.

If the navigation structure changes:

1. Identify every page containing the navigation.
2. Update all affected Persian pages.
3. Update all affected English pages.
4. Verify desktop navigation.
5. Verify mobile navigation.
6. Verify dropdown links.
7. Verify nested hall links.
8. Verify the phone link.
9. Verify language switching.
10. Check for duplicate menu items.

Do not assume that modifying `index.html` automatically updates the other pages.

---

## Multilingual Pages

The website contains Persian and English versions.

Persian pages use RTL:

```html
<html dir="rtl" lang="fa">
```

English pages should use the appropriate English language declaration and direction.

When modifying bilingual content:

```text
Persian source
      ↓
Equivalent English page
      ↓
Navigation
      ↓
hreflang
      ↓
canonical
      ↓
metadata
      ↓
asset paths
```

All of these should remain consistent.

### `hreflang`

When changing a page:

* verify the Persian URL;
* verify the English URL;
* verify both `hreflang` values;
* verify the target actually exists;
* verify the language target is the corresponding page.

Do not create a new `hreflang` URL without checking that the destination exists.

---

## Images and Media

Images and videos are a major part of this project.

Before adding an image:

* compress it where appropriate;
* use an appropriate format;
* avoid unnecessarily large resolution;
* use a descriptive filename;
* provide useful `alt` text;
* check mobile performance.

Before adding video:

* check file size;
* check encoding;
* provide a poster where appropriate;
* use `muted` and `playsinline` when autoplay is required;
* verify mobile behavior;
* verify that autoplay does not unnecessarily degrade performance.

Avoid loading multiple large videos simultaneously when one is sufficient.

---

## Hero Video

The homepage uses a video element and cycles through local video files.

When changing this area, test:

* initial poster;
* autoplay;
* muted playback;
* `playsinline`;
* video source changes;
* video completion;
* mobile behavior;
* slow network behavior;
* browser compatibility.

Do not change hero media without checking page-load performance.

---

## SEO and Structured Data

SEO is part of the website implementation.

When modifying a page, review:

```text
<title>
meta description
canonical
robots
Open Graph
Twitter Card
hreflang
JSON-LD
```

### Structured Data Accuracy

Structured data must contain real business information.

Do not use:

```text
placeholder address
placeholder coordinates
placeholder phone
placeholder social account
placeholder opening hours
```

If business information is uncertain, do not invent it.

Use the verified source of truth provided by the project owner.

### Important

Schema changes should be reviewed separately from visual changes because incorrect structured data can affect how search engines interpret the website.

---

## Accessibility

Every contribution should preserve accessibility.

Check:

### Keyboard

* navigation can be reached with the keyboard;
* dropdowns are usable;
* focus is visible;
* interactive controls are actual controls.

### Images

Use meaningful `alt` text.

Decorative images may use an empty alt attribute when appropriate.

### Links

Avoid ambiguous text such as:

```text
Click here
More
Read more
```

when the surrounding context does not make the destination clear.

### Buttons

Use `<button>` for actions.

Use `<a>` for navigation.

### Motion

Avoid introducing animations that make content difficult to use.

Respect reduced-motion preferences when adding significant motion effects.

---

## Responsive Design

Every UI contribution must be checked at minimum on:

```text
Mobile
Tablet
Desktop
Large Desktop
```

Pay particular attention to:

* navigation;
* dropdowns;
* hero sections;
* typography;
* background images;
* videos;
* galleries;
* buttons;
* phone links;
* footer;
* horizontal overflow.

A change that works only on desktop is not considered complete.

---

## Performance

The project contains many high-resolution visual assets and video files.

Contributors should avoid introducing unnecessary performance costs.

### Avoid

* huge unoptimized images;
* duplicate images;
* duplicate videos;
* unnecessary third-party scripts;
* blocking JavaScript;
* unnecessary animation libraries;
* loading assets that are not used;
* excessive DOM complexity.

### Check

When changing a major page:

* first load;
* mobile network;
* desktop network;
* hero rendering;
* image loading;
* video loading;
* layout stability.

---

## Third-Party Resources

The website currently uses external resources such as AOS from a CDN.

Before adding a new external dependency:

1. Determine whether the functionality already exists locally.
2. Check whether the dependency is actually necessary.
3. Consider performance impact.
4. Consider availability/reliability.
5. Use HTTPS.
6. Avoid adding a library for a small CSS/JavaScript task.

Do not add dependencies simply because they are convenient.

---

## Docker

The repository contains:

```text
docker-compose.yml
```

and uses:

```text
nginx:alpine
```

for static serving.

The current configuration mounts the repository read-only into:

```text
/usr/share/nginx/html
```

When changing Docker configuration:

* verify the YAML;
* verify the mount;
* verify the Nginx document root;
* verify required files exist;
* verify the resulting site works.

Do not add unnecessary services.

---

## Branching

Create a branch for every logical change.

Recommended names:

```text
feature/<description>
fix/<description>
refactor/<description>
style/<description>
performance/<description>
seo/<description>
docs/<description>
```

Examples:

```text
feature/add-hall-gallery
fix/mobile-menu-links
fix/contact-phone
fix/venue-schema
seo/fix-hreflang
performance/optimize-home-video
docs/update-readme
```

Keep branches focused.

---

## Commit Messages

Use concise and descriptive commits.

Recommended format:

```text
<type>: <description>
```

Examples:

```text
feat: add new hall gallery
fix: correct contact page links
fix: update venue phone number
fix: correct English hreflang targets
perf: optimize hero video loading
seo: correct venue structured data
style: improve mobile navigation
docs: add contribution guidelines
```

Avoid:

```text
update
changes
fix
test
final
done
```

A commit should explain the actual change.

---

## Pull Requests

Every meaningful change should be submitted through a Pull Request.

A Pull Request should contain:

### Summary

Explain what was changed.

### Reason

Explain why the change was required.

### Affected Pages

For example:

```text
index.html
about.html
en/index.html
```

### Testing

Explain what was tested.

Example:

```text
- Tested desktop navigation
- Tested mobile navigation
- Tested Persian page
- Tested English page
- Regenerated output.css
- Tested Docker container
```

### SEO Impact

If applicable:

```text
- Updated canonical
- Updated hreflang
- Updated JSON-LD
- Updated Open Graph metadata
```

### Performance Impact

If applicable:

```text
- Reduced hero video loading
- Optimized image assets
- Removed unused external dependency
```

---

## Pull Request Rules

A PR should:

* solve one clearly defined problem;
* avoid unrelated changes;
* contain no secrets;
* avoid unnecessary dependency changes;
* preserve responsive behavior;
* preserve multilingual behavior;
* include required generated CSS changes;
* include relevant documentation changes.

Large refactors should be separated from feature or content changes whenever possible.

---

## Content and Business Information

Business information is production content.

Do not change the following without verified source information:

* phone numbers;
* addresses;
* opening hours;
* social media accounts;
* venue capacity;
* business name;
* legal/company information;
* geographic coordinates.

Do not copy information from unrelated websites and assume it is correct.

If a content value is uncertain, raise an Issue or ask the project owner.

---

## Known Areas Requiring Care

The repository currently contains several areas where changes should be made carefully:

### Navigation

Navigation is duplicated across static pages.

### SEO

Structured data and metadata are page-specific.

### Language Mapping

Persian and English pages must remain aligned.

### Media

Large images and videos can affect performance.

### Generated CSS

`output.css` depends on Tailwind source/configuration.

### Docker

The Docker configuration is intended for static Nginx hosting.

---

## Security

Never commit:

* passwords;
* API keys;
* access tokens;
* private keys;
* cloud credentials;
* deployment secrets;
* personal credentials.

Remember that this is a public repository.

Anything committed to the repository should be considered potentially public.

If sensitive information is accidentally committed:

1. Do not simply delete the file and assume the secret is safe.
2. Notify the project maintainer.
3. Rotate/revoke the affected credential.
4. Follow the repository security process.

---

## Testing Checklist

Before opening a PR, verify:

### HTML

* [ ] Pages load without obvious console errors.
* [ ] Links work.
* [ ] Images load.
* [ ] Videos load.
* [ ] No unexpected horizontal overflow exists.

### Responsive

* [ ] Mobile checked.
* [ ] Tablet checked.
* [ ] Desktop checked.
* [ ] Navigation checked.
* [ ] Dropdowns checked.

### Multilingual

* [ ] Persian page checked.
* [ ] English page checked.
* [ ] Language links checked.
* [ ] `hreflang` checked.
* [ ] Relative asset paths checked.

### SEO

* [ ] Title checked.
* [ ] Description checked.
* [ ] Canonical checked.
* [ ] Open Graph checked.
* [ ] Twitter metadata checked.
* [ ] JSON-LD checked.

### CSS

* [ ] Tailwind source updated where necessary.
* [ ] `output.css` regenerated.
* [ ] Generated diff reviewed.

### Media

* [ ] New images optimized.
* [ ] New videos reviewed for size.
* [ ] Alt text added.
* [ ] Hero behavior tested.

### Docker

If Docker configuration changed:

* [ ] `docker compose` configuration checked.
* [ ] Container starts.
* [ ] Website is served correctly.
* [ ] Static assets are available.

---

## Final Review Checklist

Before requesting review:

```text
git status
git diff
```

Review the complete diff and confirm:

* no accidental files;
* no credentials;
* no debug code;
* no unnecessary formatting changes;
* no unrelated modifications;
* no broken links;
* no incorrect language paths;
* no incorrect business information.

---

## Contribution Principle

Every contribution should improve the project without unnecessarily increasing its complexity.

Prefer:

```text
small
clear
responsive
accessible
SEO-safe
performant
maintainable
```

over:

```text
large
duplicated
framework-heavy
unnecessary
hard to review
```

The website is intentionally static. Preserve that simplicity unless there is a clear architectural reason to change it.

---

## Maintainer Review

Pull Requests may be reviewed for:

1. Correctness
2. Responsive behavior
3. Accessibility
4. SEO
5. Multilingual consistency
6. Performance
7. Security
8. Code quality
9. Maintainability
10. Scope discipline

A contribution may require changes before merge if it introduces regressions in any of these areas.

Thank you for helping maintain Berelian Halls.
