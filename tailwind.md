# Tailwind CSS — Simple 8th Grade Notes

## Table of Contents

- [1. Tailwind Fundamentals](#1-tailwind-fundamentals)
- [2. Installation & Setup](#2-installation--setup)
- [3. Core Concepts](#3-core-concepts)

---

## 1. Tailwind Fundamentals

What is Tailwind CSS

- Tailwind CSS is a toolkit of small, ready-made CSS classes you can use directly in HTML. Instead of writing long CSS rules, you add short utility classes like `bg-blue-500`, `p-4`, or `text-center` to style elements.

Utility-first concept

- Utility-first means building UI by combining many small classes, each doing one thing (like padding or color). Think of Lego blocks: each class is a block that you stack to make a final design.

Tailwind vs Bootstrap vs plain CSS

| Aspect         |                                        Tailwind |                                         Bootstrap | Plain CSS                                |
| -------------- | ----------------------------------------------: | ------------------------------------------------: | ---------------------------------------- |
| How you style  |          Use many small utility classes in HTML | Use pre-built components and some utility classes | Write custom CSS rules in separate files |
| Learning curve | Easy to start, takes practice for best patterns |          Easy to start, components handle most UI | Can be hard—need CSS knowledge           |
| Customization  |                        Very flexible via config |         Customizable but components have defaults | Fully flexible but manual                |
| File size      |             Small when purged of unused classes |        Can be large if unused components included | Depends on what you write                |

Pros & cons

- Pros:

  - Fast to prototype: compose utilities directly in HTML.
  - Consistent design: uses the same spacing and colors from the config.
  - Small final CSS when unused classes are removed (purging).

- Cons:
  - HTML can look long and busy with many classes.
  - Beginners may repeat patterns (can be fixed with components).

When to use Tailwind

- Use Tailwind when you want fast styling, a consistent design system, and small final CSS. It's great for custom designs, building prototypes, and apps where you need precise control.

---

## 2. Installation & Setup

CDN usage

- Quick test: include this in the HTML `<head>` to try Tailwind fast (not for production):

```html
<script src="https://cdn.tailwindcss.com"></script>
```

- Good for learning and tiny demos. For real projects, install with a build tool so you can configure and purge unused styles.

Tailwind with Vite (simple steps)

1. Create project with Vite (choose `vanilla`, `react`, etc.).
2. Install Tailwind packages:

```bash
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

3. Add `@tailwind` directives to your CSS (e.g., `src/index.css`):

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

4. Configure `tailwind.config.js` `content` paths (see below).

Tailwind with React

- With Vite React, follow the Vite steps above and import the CSS in `main.jsx` or `index.js`:

```js
import "./index.css";
```

- With Create React App (CRA), you can add PostCSS and Tailwind similarly (CRA needs extra setup or use CRACO for older versions).

# Tailwind CSS — Simple 8th Grade Notes

## Table of Contents

- [1. Tailwind Fundamentals](#1-tailwind-fundamentals)
- [2. Installation & Setup](#2-installation--setup)
- [3. Core Concepts](#3-core-concepts)
- [4. Layout](#4-layout)
- [5. Flexbox](#5-flexbox)
- [6. Grid](#6-grid)
- [7. Spacing](#7-spacing)

---

## 1. Tailwind Fundamentals

What is Tailwind CSS

- Tailwind CSS is a toolkit of small, ready-made CSS classes you can use directly in HTML. Instead of writing long CSS rules, you add short utility classes like `bg-blue-500`, `p-4`, or `text-center` to style elements.

Utility-first concept

- Utility-first means building UI by combining many small classes, each doing one thing (like padding or color). Think of Lego blocks: each class is a block that you stack to make a final design.

Tailwind vs Bootstrap vs plain CSS

| Aspect         |                                        Tailwind |                                         Bootstrap | Plain CSS                                |
| -------------- | ----------------------------------------------: | ------------------------------------------------: | ---------------------------------------- |
| How you style  |          Use many small utility classes in HTML | Use pre-built components and some utility classes | Write custom CSS rules in separate files |
| Learning curve | Easy to start, takes practice for best patterns |          Easy to start, components handle most UI | Can be hard—need CSS knowledge           |
| Customization  |                        Very flexible via config |         Customizable but components have defaults | Fully flexible but manual                |
| File size      |             Small when purged of unused classes |        Can be large if unused components included | Depends on what you write                |

Pros & cons

- Pros:

  - Fast to prototype: compose utilities directly in HTML.
  - Consistent design: uses the same spacing and colors from the config.
  - Small final CSS when unused classes are removed (purging).

- Cons:
  - HTML can look long and busy with many classes.
  - Beginners may repeat patterns (can be fixed with components).

When to use Tailwind

- Use Tailwind when you want fast styling, a consistent design system, and small final CSS. It's great for custom designs, building prototypes, and apps where you need precise control.

---

## 2. Installation & Setup

CDN usage

- Quick test: include this in the HTML `<head>` to try Tailwind fast (not for production):

```html
<script src="https://cdn.tailwindcss.com"></script>
```

- Good for learning and tiny demos. For real projects, install with a build tool so you can configure and purge unused styles.

Tailwind with Vite (simple steps)

1. Create project with Vite (choose `vanilla`, `react`, etc.).
2. Install Tailwind packages:

```bash
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

3. Add `@tailwind` directives to your CSS (e.g., `src/index.css`):

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

4. Configure `tailwind.config.js` `content` paths (see below).

Tailwind with React

- With Vite React, follow the Vite steps above and import the CSS in `main.jsx` or `index.js`:

```js
import "./index.css";
```

- With Create React App (CRA), you can add PostCSS and Tailwind similarly (CRA needs extra setup or use CRACO for older versions).

Tailwind with Next.js

1. Install packages:

```bash
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

2. Add `@tailwind` to `styles/globals.css`:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

3. Update `tailwind.config.js` `content` to include Next.js folders, for example:

```js
module.exports = {
  content: [
    "./pages/**/*.{js,ts,jsx,tsx}",
    "./components/**/*.{js,ts,jsx,tsx}",
    "./app/**/*.{js,ts,jsx,tsx}",
  ],
  theme: { extend: {} },
  plugins: [],
};
```

tailwind.config.js (what to know)

- `content`: tells Tailwind which files to scan for class names. Use globs to include pages, components, and templates.
- `theme`: customize colors, spacing, fonts, and more.
- `plugins`: add extra features like forms, typography, etc.

Example minimal config:

```js
module.exports = {
  content: ["./src/**/*.{html,js,jsx,ts,tsx}"],
  theme: { extend: {} },
  plugins: [],
};
```

Content paths (quick guide)

- Use glob patterns to match files where you write HTML or JSX. Examples:
  - `./src/**/*.{js,ts,jsx,tsx,html}` — all files under `src`.
  - `./pages/**/*.{js,ts,jsx,tsx}` — Next.js pages.

PostCSS setup

- Tailwind uses PostCSS to transform its directives into real CSS. The `-p` flag when running `tailwindcss init -p` creates a `postcss.config.js` with:

```js
module.exports = { plugins: { tailwindcss: {}, autoprefixer: {} } };
```

This is enough for most setups.

---

## 3. Core Concepts

Utility classes

- Utilities do one thing. Examples:

| Utility      | Effect                                      |
| ------------ | ------------------------------------------- |
| `p-4`        | padding: 1rem (adds space inside element)   |
| `m-2`        | margin: 0.5rem (adds space outside element) |
| `text-lg`    | larger text size                            |
| `bg-red-500` | red background color                        |

Mobile-first approach

- Tailwind follows mobile-first responsive design. Base styles apply to all screens; prefixes add rules for larger screens.

- Prefixes example:
  - `sm:` — small screens and up
  - `md:` — medium screens and up
  - `lg:` — large screens and up

Example: `text-base md:text-lg lg:text-xl` means:

- On small phones: `text-base`.
- On medium screens (tablets) and larger: `text-lg`.
- On large screens (desktop) and larger: `text-xl`.

Responsive design philosophy

- Start with the smallest screen style, then add changes for wider screens using prefixes. This ensures good default for mobile and improved layout for bigger screens.

Hover / focus / active states

- Tailwind uses state prefixes:
  - `hover:bg-blue-500` — change background on hover.
  - `focus:ring` — show focus ring when an element is focused (good for accessibility).
  - `active:scale-95` — slightly shrink button when clicked.

Example button classes:

```html
<button
  class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-500 active:scale-95 focus:outline-none focus:ring-2"
>
  Click me
</button>
```

Dark mode (class & media)

- Two common ways to enable dark mode:

1. `media` (system preference)

- Uses the user's system setting (light or dark). In `tailwind.config.js`:

```js
module.exports = { darkMode: "media" };
```

2. `class` (manual toggle)

- You control dark mode by adding a `dark` class to an ancestor (often `<html>` or `<body>`).

```js
module.exports = { darkMode: "class" };
```

- Use dark variants: `dark:bg-gray-800 dark:text-white`

Example:

```html
<div class="bg-white dark:bg-gray-900 text-black dark:text-white">
  Content for both modes
</div>
```

---

## 4. Layout

Container

- `container` centers and gives a max width that changes with screen size. Use it to keep page content readable.

Box sizing

- `box-border` vs `box-content`: controls whether padding is included in width/height (`box-border`) or added to it (`box-content`). Tailwind has `box-border` and `box-content` utilities.

Display (block, inline, flex, grid)

- `block`, `inline`, `inline-block`, `flex`, `inline-flex`, `grid` are utilities to change how elements behave.

Float & clear

- `float-left`, `float-right`, `float-none` to float elements. Use `clear-left`, `clear-right`, `clear-both` to stop floats from affecting an element.

Object fit & position

- `object-fit` utilities: `object-contain`, `object-cover`, `object-fill`, `object-none`, `object-scale-down` for images/videos.
- Positioning utilities: `static`, `relative`, `absolute`, `fixed`, `sticky` and offset helpers like `top-0`, `left-1`.

Overflow

- `overflow-auto`, `overflow-hidden`, `overflow-scroll`, `overflow-visible` to control scroll and clipping.

Visibility

- `visible` and `invisible` hide or show elements without changing layout (invisible keeps the space).

---

## 5. Flexbox

flex

- `flex` makes a container use flex layout. `inline-flex` keeps it inline.

flex-direction

- `flex-row` (default), `flex-row-reverse`, `flex-col`, `flex-col-reverse` set the main axis.

flex-wrap

- `flex-wrap`, `flex-nowrap`, `flex-wrap-reverse` control whether items wrap to the next line.

justify-content

- `justify-start`, `justify-center`, `justify-end`, `justify-between`, `justify-around`, `justify-evenly` control horizontal distribution on the main axis.

align-items

- `items-start`, `items-center`, `items-end`, `items-stretch`, `items-baseline` align along the cross axis.

align-content

- `content-start`, `content-center`, `content-end`, `content-between`, `content-around`, `content-evenly` handle multi-line flex containers.

flex-grow / flex-shrink / flex-basis

- `flex-grow` / `flex-grow-0` control how items grow.
- `flex-shrink` / `flex-shrink-0` control shrinking.
- `basis-1/2`, `basis-1/3`, `basis-auto` control the initial size (flex-basis).

order

- `order-1` `order-2` etc. change visual order of items.

gap

-- `gap-4`, `gap-x-2`, `gap-y-6` set spacing between flex items (very handy; replaces margins in many cases).

---

## 6. Grid

grid

- `grid` turns a container into a grid layout.

grid-template-columns / rows

- `grid-cols-3` creates 3 equal columns. Use `grid-cols-2 md:grid-cols-4` for responsiveness.
- `grid-rows-3`, `grid-rows-none` for rows.

grid-auto-flow

- `grid-flow-row`, `grid-flow-col`, `grid-flow-dense` control how items are placed automatically.

col-span / row-span

- `col-span-2`, `row-span-3` make items span multiple tracks.

gap

- `gap-4`, `gap-x-2`, `gap-y-6` set spacing between grid items.

place-items / place-content

- `place-items-center` centers items inside each cell.
- `place-content-center` centers the whole grid content inside the container.

Grid quick examples

| Layout need            | Classes example                         |
| ---------------------- | --------------------------------------- |
| 2-column responsive    | `grid grid-cols-1 md:grid-cols-2 gap-6` |
| Item spans two columns | `col-span-2` on the item                |

---

## 7. Spacing

Padding

- `p-4`, `px-2`, `py-3`, `pt-1` control padding. `p-` is all sides, `px-` horizontal, `py-` vertical.

Margin

- `m-4`, `mx-2`, `my-3`, `mt-1` control margin. Use `auto` versions like `mx-auto` to center blocks.

Space between

- `space-x-4` and `space-y-4` add consistent spacing between children elements (no extra wrapper margins needed).

Negative spacing

- `-mt-4`, `-ml-2` allow pulling elements closer or overlapping. Use carefully.

Simple spacing rules

- Spacing scales use Tailwind's scale (e.g., `1`→0.25rem, `2`→0.5rem, `4`→1rem). Use consistent spacing to keep design neat.

---

## 8. Sizing

Width

- `w-` utilities set width: `w-0`, `w-1/2`, `w-full`, `w-screen`, and fixed sizes like `w-64`.

Min / Max width

- `min-w-0`, `min-w-full`, `max-w-xs`, `max-w-lg` help control shrink/grow and readable content widths.

Height

- `h-` utilities: `h-8`, `h-16`, `h-full`, `h-screen` set element heights.

Min / Max height

- `min-h-0`, `min-h-screen`, `max-h-64` limit element heights for layouts and scroll areas.

Aspect ratio

- Use `aspect-w-16 aspect-h-9` with the `@tailwindcss/aspect-ratio` plugin, or `aspect-video`, `aspect-square` utilities to keep media at the right ratio.

---

## 9. Typography

Font family

- `font-sans`, `font-serif`, `font-mono` pick basic families. Use `theme.extend.fontFamily` in config for custom fonts.

Font size

- `text-sm`, `text-base`, `text-lg`, `text-xl` control size. Combine with responsive prefixes like `md:text-xl`.

Font weight

- `font-light`, `font-normal`, `font-semibold`, `font-bold` adjust thickness.

Line height

- `leading-none`, `leading-tight`, `leading-normal`, `leading-loose` control spacing between lines.

Letter spacing

- `tracking-tight`, `tracking-normal`, `tracking-wide` adjust letter spacing.

Text alignment

- `text-left`, `text-center`, `text-right`, `text-justify` align text.

Text color

- `text-gray-700`, `text-red-500` set color. Use `dark:text-gray-200` for dark mode.

Text decoration

- `underline`, `line-through`, `no-underline` control decoration.

Text transform

- `uppercase`, `lowercase`, `capitalize`, `normal-case` control casing.

Line clamp

- Use the `line-clamp` plugin (e.g., `line-clamp-3`) to truncate text after N lines with an ellipsis.

---

## 10. Backgrounds

Background color

- `bg-white`, `bg-gray-100`, `bg-blue-500` set colors. Combine with `hover:bg-...` and `dark:bg-...`.

Background image

- Use `bg-[url('/path/image.jpg')]` or define classes in CSS for complex images.

Gradient backgrounds

- `bg-gradient-to-r from-indigo-500 via-purple-500 to-pink-500` creates gradients.

Background size

- `bg-auto`, `bg-cover`, `bg-contain` control sizing.

Background position

- `bg-center`, `bg-top`, `bg-bottom`, `bg-left`, `bg-right` set image position.

Background repeat

- `bg-repeat`, `bg-no-repeat`, `bg-repeat-x`, `bg-repeat-y` control repeating.

Background attachment

- `bg-fixed`, `bg-local`, `bg-scroll` control whether background scrolls with content.

---

## 11. Borders

Border width

- `border`, `border-2`, `border-4`, `border-0` set thickness.

Border color

- `border-gray-200`, `border-red-500` choose colors. Use `dark:border-gray-700` for dark mode.

Border style

- `border-solid`, `border-dashed`, `border-dotted`, `border-double` control style.

Border radius

- `rounded`, `rounded-md`, `rounded-full`, `rounded-t-lg` control corner rounding.

Divide utilities

- `divide-y`, `divide-x`, combined with `divide-gray-200` add separators between children.

Ring utilities

- `ring`, `ring-2`, `ring-offset-2`, `ring-blue-500` create focus rings (useful for accessibility and focus states).

---

If you want, I can now add a sample `tailwind.config.js` or small React/Next.js examples.

Quick flex cheat table

| Need           | Use these classes                  |
| -------------- | ---------------------------------- |
| Row, centered  | `flex items-center justify-center` |
| Column, spaced | `flex flex-col justify-between`    |
| Wrap items     | `flex flex-wrap gap-4`             |

---

## 12. Effects

Box shadow

- Shadows add depth. Use `shadow-sm`, `shadow`, `shadow-md`, `shadow-lg` to make elements look raised. Combine with `hover:shadow-lg` for interactive effects.

Opacity

- `opacity-100` (fully visible) down to `opacity-0` (invisible). Use `hover:opacity-90` to gently fade on hover.

Mix blend mode

- Controls how colors mix with what's behind them. `mix-blend-multiply` darkens, `mix-blend-screen` lightens. Useful for overlays and creative effects.

Background blend mode

- `bg-blend-multiply`, `bg-blend-overlay` let layered backgrounds and gradients combine in different ways.

Filter

- Filters change an element's appearance: `filter blur-sm`, `filter grayscale`, `filter brightness-75`. Enable with `filter` class then add specific filters like `blur-md`.

Backdrop filter

- Blurs or changes what's behind an element. `backdrop-blur-sm` softens background behind a translucent panel. Requires browser support or the `backdrop-filter` plugin.

Quick tips

- Use subtle shadows and small blur amounts for best results. Combine opacity with transform and transition for smooth hover effects.

---

## 13. Tables

Table layout

- `table-auto` lets the browser size columns automatically. `table-fixed` sets columns to fixed widths for consistent layouts.

Border collapse

- `border-collapse` merges adjacent borders (classic table look). `border-separate` keeps borders apart and uses `border-spacing` for gaps.

Table styling utilities

- Style rows and cells using utilities: `text-sm` for smaller text, `px-4 py-2` for padding, `bg-gray-50` for striped headers, and `divide-y` for row separators.

Accessible table notes

- Always use `<thead>` and `<tbody>` and include header cells (`<th>`) to help screen readers.

Simple table patterns

- Use `min-w-full divide-y divide-gray-200` on the table and `bg-gray-50` for the header to create a clean default table.

---

## 14. Transforms

Scale

- `scale-95`, `scale-100`, `scale-105` change element size visually. Use with `transition` for smooth scaling.

Rotate

- `rotate-0`, `rotate-6`, `rotate-45`, `-rotate-45` rotate elements. Useful for icons or decorative elements.

Translate

- `translate-x-1`, `translate-y-2`, `-translate-x-1` move an element left/right/up/down. Use small values for micro-interactions.

Skew

- `skew-x-6`, `skew-y-3` slant elements. Good for stylized banners or cards but use sparingly.

Transform origin

- `origin-center`, `origin-top`, `origin-bottom-right` change the pivot point for rotate/scale transforms.

Example: button with transform

```html
<button
  class="transform hover:scale-105 hover:-translate-y-1 transition duration-200"
>
  Press
</button>
```

---

## 15. Transitions & Animation

Transition property

- `transition` enables a set of common properties. Use `transition-colors` if only colors should animate.

Transition duration

- `duration-150`, `duration-300`, `duration-700` control how fast the transition runs.

Timing functions

- `ease-linear`, `ease-in`, `ease-out`, `ease-in-out` change animation pacing. `ease-out` feels natural for hover effects.

Delay

- `delay-75`, `delay-150` wait before starting the transition. Combine with `group-hover` to sequence child animations.

Animate utilities

- Built-in animations: `animate-spin`, `animate-pulse`, `animate-bounce`. Use `motion-safe:` variants to respect user motion preferences.

Custom animations

- Write `@keyframes` in a CSS file and expose a class like `.animate-float`. Register custom timing in `animation` shorthand.

Accessibility tip

- Respect `prefers-reduced-motion` — Tailwind supports `motion-reduce` and `motion-safe` helpers to disable or enable animations.

---

## 16. Interactivity

Cursor

- `cursor-pointer`, `cursor-default`, `cursor-move`, `cursor-wait` change the mouse cursor. Use `cursor-pointer` for clickable items.

Pointer events

- `pointer-events-none` disables clicks and mouse events on an element, while `pointer-events-auto` restores them. Useful when building overlays.

Resize

- `resize`, `resize-x`, `resize-y`, `resize-none` allow users to resize text areas (browser support varies). Pair with `overflow-auto` for scroll behavior.

User select

- `select-none`, `select-text`, `select-all` control whether users can highlight text. Disable selection for icons or draggable controls.

Scroll behavior

- `scroll-smooth` enables smooth scrolling for anchor links. Use `scroll-auto` to reset to instant jumps.

Scroll snap

- `snap-start`, `snap-center`, `snap-end` plus container `snap-x`, `snap-mandatory` create snap-to-item scrolling for carousels and sections.

Quick accessibility notes

- Always ensure interactive elements are focusable (`tabindex` or semantic elements like `<button>`), and provide visible focus styles with `focus:ring`.

---

## 17. SVG

Fill

- `fill-current` makes an SVG use the current text color (`color` or `text-...` classes). Set color with `text-blue-500` to tint icons.

Stroke

- `stroke-current` similarly uses current color for strokes. Use `stroke-2` to set stroke width.

SVG sizing

- Control size with `w-6 h-6` or `w-8 h-8`. Use `w-auto` with `h-6` to preserve aspect ratio.

SVG color control

- Use `text-` color utilities with `fill-current`/`stroke-current` or embed `class` attributes inside the SVG paths.

Simple SVG example

```html
<svg class="w-6 h-6 text-green-500 fill-current" viewBox="0 0 24 24">
  <path d="..." />
</svg>
```

---

## 18. Accessibility

Screen reader utilities

- Use semantic HTML (`<button>`, `<nav>`, `<main>`, `<header>`) before relying on classes. Tailwind doesn't change semantics but pairs well with ARIA utilities.
- Use visually hidden helpers (e.g., `.sr-only` class) to provide text for screen readers without showing it on screen.

Focus utilities

- `focus:outline-none` removes the default outline (use carefully). Prefer `focus:ring` or `focus-visible:ring` to provide visible, accessible focus styles.
- `focus:ring-2 focus:ring-offset-2 focus:ring-blue-500` creates a clear focus indicator.

ARIA attributes

- Add `aria-` attributes to improve screen reader context: `aria-label`, `aria-labelledby`, `aria-hidden`, `aria-expanded`.
- Tailwind does not generate ARIA attributes — add them in your HTML with clear, concise values.

Keyboard navigation support

- Ensure interactive elements are reachable via keyboard (use `<button>`, `<a>`, or `tabindex="0"`).
- Use `focus:` and `focus-visible:` utilities to style focus and guide keyboard users.

Quick rules

- Always provide keyboard access, visible focus, and meaningful ARIA labels where needed.

---

## 19. Responsive Design

Breakpoints

- Tailwind's default breakpoints are mobile-first: `sm`, `md`, `lg`, `xl`, `2xl`. They apply styles at the given minimum width.

sm / md / lg / xl / 2xl

- Typical default sizes: `sm` (640px), `md` (768px), `lg` (1024px), `xl` (1280px), `2xl` (1536px). You can customize these in `tailwind.config.js`.

Responsive prefixes

- Use `sm:`, `md:`, `lg:` etc. before a utility to apply it at that size and up. Example: `p-2 md:p-6`.

Container queries

- Container queries let styles respond to a container's size instead of the viewport. Tailwind has plugins or upcoming support; you can add `@container` rules in CSS or use plugins like `@tailwindcss/container-queries`.

Responsive design tip

- Start with mobile-first base styles, then add `md:` or `lg:` overrides for larger screens.

---

## 20. State Variants

hover, focus, active, visited, disabled

- Prefix utilities with states: `hover:bg-blue-500`, `focus:ring`, `active:scale-95`, `visited:text-purple-600`, `disabled:opacity-50`.

group & peer

- `group` and `group-hover:` let a parent state control child styles. `peer` + `peer-checked:` let sibling elements react (useful for custom checkboxes).

focus-within & focus-visible

- `focus-within:` applies when any child receives focus. `focus-visible:` targets keyboard focus (better for reducing outline noise from mouse clicks).

Best practices

- Combine variants for clarity: `group-hover:opacity-90 hover:opacity-100 transition` for smooth interactions.

---

## 21. Dark Mode

dark variant

- Use `dark:` prefix to apply utilities when dark mode is active, e.g., `dark:bg-gray-900 dark:text-white`.

class-based dark mode

- Set `darkMode: 'class'` in `tailwind.config.js` and toggle a `dark` class on `<html>` or `<body>` to control theme manually.

media-based dark mode

- Set `darkMode: 'media'` to follow the user's OS preference automatically.

Custom dark themes

- Extend the `theme` colors in `tailwind.config.js` to create custom shades for dark mode; use `theme.extend.colors` and refer with `dark:text-custom`.

Tip

- Ensure contrast in dark mode: test text against backgrounds and adjust colors in the config for readability.

---

## 22. Customization

Theme extension

- Use `theme.extend` in `tailwind.config.js` to add new tokens without replacing defaults.

Custom colors

- Add palettes under `theme.extend.colors` and use them as `bg-mycolor-500` or `text-mycolor-700`.

Custom spacing

- Extend `spacing` scale to add values like `72: '18rem'` and use `p-72`.

Custom fonts

- Add font families in `theme.extend.fontFamily` and reference with `font-sans` or your custom key.

Custom breakpoints

- Override `screens` in the config to change responsive breakpoints.

Custom shadows

- Add `boxShadow` entries in `theme.extend.boxShadow` for named shadows used as `shadow-custom`.

Quick example (partial `tailwind.config.js`)

```js
module.exports = {
  theme: {
    extend: {
      colors: { brand: { 450: "#4f46e5" } },
      spacing: { 72: "18rem" },
      fontFamily: { display: ["Oswald", "sans-serif"] },
    },
  },
};
```

---

## 23. Plugins

Official plugins

- Tailwind provides official plugins like `@tailwindcss/forms`, `@tailwindcss/typography`, `@tailwindcss/aspect-ratio`, and `@tailwindcss/container-queries`.

Typography plugin

- `@tailwindcss/typography` (prose) gives readable defaults for long-form content: headings, lists, code blocks.

Forms plugin

- `@tailwindcss/forms` normalizes form element styling and provides utilities to style inputs consistently.

Aspect ratio plugin

- `@tailwindcss/aspect-ratio` provides `aspect-w-`/`aspect-h-` and `aspect-video`, `aspect-square` helpers for media sizing.

Container queries plugin

- `@tailwindcss/container-queries` enables container-based responsive utilities (if supported in your Tailwind version).

Writing custom plugins

- Plugins can add utilities, components, or variants. Use the plugin API to register new classes or hooks into the build.

How to install a plugin (example)

```bash
npm install -D @tailwindcss/typography
```

Then add to `tailwind.config.js`:

```js
module.exports = { plugins: [require("@tailwindcss/typography")] };
```

---

## 24. Directives

`@tailwind`

- Inserts Tailwind’s layers into your CSS file. Use `@tailwind base; @tailwind components; @tailwind utilities;` in your main CSS.

`@apply`

- Lets you compose utility classes inside your own CSS selectors. Example:

```css
.btn {
  @apply px-4 py-2 bg-blue-600 text-white rounded shadow;
}
```

`@layer`

- Use `@layer base/components/utilities` to place custom CSS into Tailwind's build order so it can be purged/overridden correctly.

`base / components / utilities`

- These are the three internal layers Tailwind generates. Put global resets in `base`, reusable classes in `components`, and new utilities in `utilities`.

---

## 25. Advanced Configuration

Presets

- Use `presets` to share a common config across projects. Useful for design systems.

Safelist

- Add `safelist` to `tailwind.config.js` to keep classes that the scanner might miss (dynamic class names).

Prefixing

- `prefix: 'tw-'` adds a prefix to all Tailwind classes to avoid conflicts with other frameworks.

Important flag

- `important: true` or `important: '#app'` forces utilities to be `!important` or scoped, useful to override third-party CSS.

Core plugins enable/disable

- Use `corePlugins` to disable built-in features you don't need (like `preflight`) to reduce weight or avoid conflicts.

---

## 26. Performance & Optimization

Purge / content config

- Configure `content` (formerly `purge`) with globs to point Tailwind at your source files so unused styles are removed in production.

Tree-shaking unused styles

- Tailwind's JIT or build-time purge removes unused utilities — ensure `content` paths include templates, components, and dynamic usage patterns.

Production build

- Run builds with `NODE_ENV=production` (or framework build commands) to generate optimized CSS; Tailwind will remove unused classes and minify output.

Bundle size optimization

- Use `prefix`, `safelist`, and `corePlugins` carefully. Remove unused plugins and keep `content` tight to significantly shrink CSS size.

---

## 27. Tailwind with Frameworks

React + Tailwind patterns

- Import your compiled CSS in `index.js`/`main.jsx`. Use small presentational components and prefer utility composition over inline styles.

Next.js + Tailwind

- Add Tailwind to `styles/globals.css`, configure `tailwind.config.js` content to include `/pages`, `/components`, and `/app` if using app router.

Conditional classes

- Use template literals or helper libs to toggle classes: `className={isActive ? 'bg-blue-500' : 'bg-gray-200'}`.

`clsx` / `classnames`

- `clsx` and `classnames` make conditional composition cleaner: `clsx('p-4', isActive && 'bg-blue-500')`.

---

## 28. Component Patterns

Reusable components

- Create small components (buttons, cards) that accept props for variants and use Tailwind classes inside.

UI patterns

- Keep a pattern library or storybook with common component examples to ensure consistent usage.

Layout components

- Build `Container`, `Grid`, and `Header` components to encapsulate layout concerns and reuse Tailwind utilities.

Design systems

- Extend `theme` with tokens (colors, spacing, fonts) and share via `presets` or a package to keep apps consistent.

---

## 29. Animations

Keyframes

- Define `@keyframes` for complex motions and expose via classes that use the `animation` shorthand.

Custom animation utilities

- Add named animations to `theme.extend.animation` and `keyframes` in `tailwind.config.js` for reuse.

Motion design patterns

- Use subtle, meaningful motion: micro-interactions for feedback, motion hierarchy (primary vs background), and reduce motion for accessibility.

---

## 30. Best Practices

Utility composition

- Favor composing utilities into small components (`@apply` inside `@layer components`) for reuse and readability.

Avoiding class bloat

- Use variant components and helper functions (like `clsx`) instead of repeating long class lists everywhere.

Readability strategies

- Order classes logically (layout -> spacing -> typography -> color -> state) and use comments or component wrappers when needed.

Scalability patterns

- Keep theme tokens consistent, use presets for shared tokens, and create a small set of component patterns rather than many one-off styles.

---

## 31. Debugging

Dev tools

- Use browser devtools to inspect computed styles and class names. Tailwind's class names map to utilities, so inspect the element to see applied rules.

Common mistakes

- Forgetting to include files in `content`, using dynamic class names without safelist, or overriding utilities with custom CSS without proper specificity.

Overriding issues

- If your custom CSS isn't applied, ensure correct `@layer` usage and that your file is loaded after Tailwind layers or uses `!important` appropriately.

Specificity handling

- Tailwind utilities are low-specificity; use component classes or `important` flag when you must override third-party styles.

---
