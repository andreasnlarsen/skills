# Frontend Health

---

## FE-01: Bundle Size

**What:** JavaScript bundle(s) exceeding size thresholds that hurt initial load time.
**Detection:** static — inspect build output (`dist/`, `build/`), check `webpack-bundle-analyzer`, `rollup-plugin-visualizer`, or Next.js build output for individual chunk sizes and total JS transferred.
**Possible correction:** Split at route boundaries, dynamic-import large dependencies or replace heavy libraries when measured transfer delays the required experience.

## FE-02: Tree-Shaking Effectiveness

**What:** Dead exports from libraries included in the bundle because imports are not tree-shakeable.
**Detection:** static — look for default-import patterns of large libraries (`import _ from 'lodash'` instead of `import { debounce } from 'lodash-es'`). Inspect package side-effect declarations, including CSS and initialization requirements. Run a bundle visualizer and look for unexpected full library inclusions.
**Possible correction:** Use named imports from ESM builds, and set `"sideEffects": false` only when true, preserving CSS, registration and initialization effects.

## FE-03: Component Complexity

**What:** Components that are too large or carry too many responsibilities, making them hard to test and reuse.
**Detection:** static — count JSX/template lines per component file. Count the number of props a component accepts. Count local state variables (useState, ref) per component.
**Possible correction:** Split by logical section when responsibilities interfere; derive redundant state from its owner rather than syncing it in a custom hook.

## FE-04: Accessibility (a11y)

**What:** Missing or incorrect ARIA attributes, non-semantic HTML, keyboard navigation gaps, and contrast issues.
**Detection:** static — run `axe-core`, `eslint-plugin-jsx-a11y`, or `vue-axe` as part of CI. Dynamic — inspect applicable accessibility audit findings and actual keyboard/screen-reader behavior. Check for: interactive elements without labels, images without `alt`, forms without `<label>`, color contrast failures.
**Possible correction:** Fix the specific task barrier first (missing labels, contrast, keyboard path); add `eslint-plugin-jsx-a11y` when regressions recur.

## FE-05: Render Performance Patterns

**What:** Components that re-render excessively or perform expensive work inside render paths.
**Detection:** static — inspect expensive derivations and unstable object/function identities in hot render paths. For each React Effect, identify the external system and why synchronization is needed before examining dependency and cleanup correctness. An Effect's presence or an omitted dependency array alone does not prove a defect. Dynamic — use React DevTools Profiler or Vue DevTools to measure render counts and cost.
**Possible correction:** Remove unnecessary Effects first; for measured render cost, lift constants, memoize or virtualize without changing behavior merely to reduce render counts.

## FE-06: Design System Adherence

**What:** Accidental inconsistency between repeated visual roles and the accepted design system.
**Detection:** static — search for hard-coded hex colors (`#[0-9a-fA-F]{3,6}`), hard-coded pixel spacing in CSS/styles outside of a token system, components not using the project's designated component library or design tokens file.
**Possible correction:** Replace hard-coded values with design tokens when repeated roles diverge accidentally; preserve intentional one-off values.

## FE-07: State Management Complexity

**What:** Global state that is overly large, poorly structured, or misused to hold local UI state.
**Detection:** static — trace state ownership, lifetime and consumers. Inspect stale server data mixed with local UI state and global state used for component-local concerns.
**Possible correction:** Separate server state (React Query/SWR) from client UI state and move local state back to components when stale data or coupling is observed.

## FE-08: Image Optimization

**What:** Unoptimized images that inflate page weight and hurt load performance.
**Detection:** static — check for images served from source without a CDN or image optimization pipeline. Look for `<img>` tags missing `width`/`height` attributes (causes layout shift), missing `loading="lazy"` on below-the-fold images, and large PNG files where WebP/AVIF would suffice.
**Possible correction:** Serve WebP/AVIF with `width`/`height`, `loading="lazy"` below the fold and `fetchpriority="high"` on the LCP image when images inflate page weight.

## FE-09: Client-Side Routing Hygiene

**What:** Routing configuration that creates dead routes, missing loading/error states, or deep linking failures.
**Detection:** static — inspect router config for: catch-all routes that shadow specific routes, routes without a defined error boundary or fallback, dynamic segments lacking a loading state, programmatic navigations that bypass the router (`window.location.href` instead of router push).
**Known failure:** Catch-all route registered before specific routes.
**Possible correction:** Fix route ordering, add error/loading states and use the router's navigation API when navigation or recovery gaps are observed.

## FE-10: CSS Health

**What:** CSS that is difficult to maintain due to high specificity, duplication, dead rules, or global scope leakage.
**Detection:** static — inspect selector collisions, overrides and style leakage. Existing stylelint or browser coverage can help locate candidates; verify dynamic states before classifying CSS as unused.
**Possible correction:** Flatten specificity or scope styles (CSS Modules, Tailwind) when selector conflicts or leakage are found; verify dynamic states before removing rules.

## FE-11: Third-Party Script Loading

**What:** Third-party scripts loaded synchronously or without resource hints, blocking page render.
**Detection:** static — search for `<script>` tags in HTML without `async` or `defer`. Check for analytics, chat, and ad scripts loaded in `<head>` synchronously. Dynamic — run WebPageTest or Lighthouse to identify render-blocking third-party resources.
**Possible correction:** Add `async`/`defer` or the framework's script loader when a third-party script blocks render and its execution order permits.

## FE-12: Responsive Design

**What:** Layouts that break or overflow at specific viewport widths, or that use fixed pixel widths instead of fluid units.
**Detection:** static — inspect container constraints, viewport metadata and content-driven breakpoints. Dynamic — inspect supported narrow and intermediate layouts for unintended scrolling or inaccessible content.
**Known failure:** Missing `<meta name="viewport">`.
**Possible correction:** Replace fixed widths with `max-width` and fluid units when a supported viewport breaks; audit at 375px, 768px and 1280px.

## FE-13: Error Boundaries

**What:** Component trees lacking error boundaries, causing a single component failure to unmount the entire application.
**Detection:** static — search for `ErrorBoundary` component usage (React) or `errorCaptured`/`onErrorCaptured` (Vue). Check that error boundaries exist at: the route level, around third-party widget integrations, and around data-fetching components.
**Possible correction:** Add route-level boundaries and isolate third-party widgets when one failure unmounts the app; a boundary around every component is unnecessary.

## FE-14: Core Web Vitals Readiness

**What:** Patterns that may impair loading, layout stability or interaction responsiveness in the actual deployment.
**Detection:** dynamic — use relevant performance tooling and field data; lab measurements diagnose but do not prove production INP or user experience. Inspect delayed critical resources, shifting content, long synchronous handlers and render-blocking CSS in the affected load/interaction trace.
**Known failure:** Field data exceeding the published Core Web Vitals references (LCP <2.5s, CLS <0.1, INP <200ms).
**Possible correction:** Preload the LCP image (`<link rel="preload" as="image">`), reserve space with `min-height` or split long handlers per the measured bottleneck; confirm with field data.
