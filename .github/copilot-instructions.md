# Copilot Instructions

## Requirements

All projects use **Bootstrap**, **CodeKit**, and **AWS CLI**. Do not suggest alternative frameworks or build tools.

## File Structure

All source files live under `src/`:

- Kit/HTML pages: `src/*.kit`, `src/page-name/index.kit`
- Kit partials (use `_` prefix): `src/assets/partials/_partial-name.kit`
- SCSS partials (use `_` prefix):
    - Page-specific: `src/assets/scss/pages/_page-name.scss`
    - Reusable components: `src/assets/scss/components/_component-name.scss`
- JavaScript:
    - Page-specific: `src/assets/js/pages/page-name.js`
    - Reusable components: `src/assets/js/components/component-name.js`
- Media/images: `src/assets/media/`
- Fonts: `src/assets/fonts/`

## HTML

- IDs and classes use kebab-case: `my-class`, `my-id`
- Use **meaningful, descriptive names** — avoid generic names like `div-1` or `box-2`; prefer `icon-wrapper` or `details-area`
- Attribute order: `id` → `class` → `type`/`name` → `data-*` → `src`/`href`/`for`/`value` → `title`/`alt` → `role`/`aria-*` → `tabindex` → `style`
- Separate class lists with a single space, no leading/trailing spaces
- Apply Bootstrap utility classes directly in markup for spacing, typography, color, display, and layout before creating custom classes
- Use banner-style comments for major page sections, and plain comments for sub-groups within a section:
    ```html
    <!-- ******************** INTRO ******************** -->
    <header id="intro">
    <!-- Logo/Navigation -->
      <div id="logo">...</div>
      <nav>...</nav>
    </header>

    <!-- ******************** MAIN SECTION ******************** -->
    <main id="main-section">
    <!-- Blog post -->
      <article>
        <h1>...</h1>
        <p>...</p>
      </article>
    <!-- Sidebar -->
      <aside>...</aside>
    </main>
    ```
- Add comments to indicate major images and their purpose
- Add internal file link comments at the top of each Kit/HTML file using the `isotechnics.commentlinks` format:
    ```html
    <!-- [[src/assets/scss/pages/_index.scss]] -->
    <!-- [[src/assets/js/pages/index.js]] -->
    ```
    Always use the full path from root, including the full filename and `_` prefix for SCSS partials.

## Kit

- Kit variables use camelCase: `myVariable`, `pageTitle`
- Kit variable declaration syntax: `<!-- $myVariable = value -->`
- Kit variable output syntax: `<!-- $myVariable? -->`
- Kit partial import syntax: `<!-- @import assets/partials/partial-name -->`
- Kit partial files use the `_` prefix: `_partial-name.kit`

## SCSS

- Prefer Bootstrap's built-in utility classes, components, and variables over writing custom CSS — only write custom SCSS when Bootstrap cannot achieve the desired result
- Match variable names to class names: `.font-secondary { font-family: $font-secondary; }`
- Use background shorthand as base, then override specific properties only
- Group shared `::before`/`::after` styles together, then differentiate below
- Add comments on pseudo-elements and dynamic classes describing design intent
- Page-specific styles go in `src/assets/scss/pages/`, reusable components in `src/assets/scss/components/`
- All partial files must use the `_` prefix: `_my-partial.scss`

## JavaScript

- Variables use camelCase: `myVariable`, `menuIsOpen`
- Page-specific scripts go in `src/assets/js/pages/`, reusable scripts in `src/assets/js/components/`
- Comment non-obvious logic only — do not over-comment
- Use `//` for single-line and `/* */` for multi-line comments

## Accessibility

- Prefer native HTML over ARIA
- All images must have `alt` attributes (empty `alt=""` for decorative)
- Decorative SVGs must use `aria-hidden="true" focusable="false"`
- Buttons and links must have descriptive labels — avoid "Click here" or unlabeled icon controls
- Use Bootstrap's `visually-hidden` class for icon-only controls and repeated CTAs
- New tab links must include `rel="noopener noreferrer"` and a visually hidden "(opens in new tab)" notice
- Never apply `aria-hidden="true"` to focusable elements
- Use `<button>` and `<a href="">` for interactive elements — never clickable `<div>` elements
- Forms must always use `<label>` — never rely on placeholder text as a label
- Prefer `aria-labelledby` (referencing existing visible text) over `aria-label` when possible
- Pre-merge: verify Tab-only navigation, run Lighthouse accessibility audit, and spot-check with a screen reader
- Full test 2


