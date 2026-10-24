# SeedSort calculator

Static seed-flow calculator preserving the original dark interface and three sliders. Open `index.html` directly in a browser. No build step, backend, external assets, or dependencies are required.

## Calculations

- seeds/s = (kg/h × 1,000,000) / (mg/seed × 3600)
- seeds/channel/s = seeds/s ÷ channels
- interval_ms = 1000 ÷ seeds/channel/s
- seeds_in_8.33ms = seeds/s × 0.00833

At 800 kg/h, 40 mg/seed, and 32 channels, the unrounded results are 5555.555556 seeds/s, 173.611111 seeds/channel/s, 5.76 ms, and 46.277778 seeds per 8.33 ms. The UI rounds counts to integers and the interval to two decimals.

The displayed equation uses grams consistently: 800,000 g/h ÷ (3600 × 0.04 g/seed). This corrects a unit mismatch in the original formula label; calculation logic is unchanged.

## GitHub Pages

Intended repository: https://github.com/H-G11/seedsort-calculator

Intended public URL: https://h-g11.github.io/seedsort-calculator/

Publish the repository's `main` branch, `/` (root), using GitHub Pages' “Deploy from a branch” setting. `.nojekyll` marks the site as plain static files. These URLs are targets, not confirmation of deployment.

## Validation

The actual embedded script passed direct execution with a simulated DOM for all 97,344 permitted slider combinations, including minimum and maximum values and each input listener. Checks covered all four results, displayed formula, labels, finite values, and slider fill percentages.

Browser testing and deployment are pending: this execution environment blocks socket creation and Chromium startup, cannot resolve GitHub hosts, and cannot start the installed `gh` launcher because its CLI download requires network access. Visual responsiveness, native slider interactions, browser console errors, GitHub authentication, repository state, and the public deployment have not been verified.
