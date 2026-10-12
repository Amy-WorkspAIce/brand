<img src="banners/amy-workspaice-banner-github.svg" alt="Amy-WorkspAIce: the digital workspace of the future" width="100%">

# Amy-WorkspAIce brand

The single source of truth for how every Amy-WorkspAIce app looks and sounds: the brand book
(below), design tokens, fonts, logos and banners. Apps copy from here; they don't invent their own.

| Path | What |
|---|---|
| [`tokens/tokens.json`](tokens/tokens.json) | Design tokens: colors (dark and light), type, spacing, radii, clipped corners, glows. **Edit this**, then run `python scripts/build_css.py`. |
| [`tokens/tokens.css`](tokens/tokens.css) | Generated CSS custom properties (`--night-000`, `--magenta`, `--font-sans`, `--space-4`, …) plus `.cut-sm` / `.cut-md`. |
| [`fonts/`](fonts/) | Audiowide, Chakra Petch, JetBrains Mono as WOFF2, with [`fonts.css`](fonts/fonts.css). |
| [`logos/`](logos/) | The Orbit mark, lockups, wordmarks, app icons ([usage](logos/README.md)). |
| [`banners/`](banners/) | README and website banners ([usage](banners/README.md)). |
| [`reference/`](reference/) | Reference screens: the color scheme on a real workspace view, the logo sheet, the cover. |

## Using it in an app

1. Copy `tokens/tokens.css`, `fonts/` and the logos you need into the app (vendored, so
   self-hosted installs work offline and on private networks; no font CDN).
2. Load `fonts.css` and `tokens.css` before the app's own CSS, and style only with the variables.
3. Dark is the default. Set `data-theme="light"` on `<html>` for light, or leave `data-theme`
   off to follow the system.
4. When the brand changes here, re-copy the files. Each app's README says which brand commit it
   was last synced from.

The source design system (editable, with live previews) is a Claude design-system artifact owned
by the founder; this repo is the published copy.

## Licensing

- Fonts: SIL Open Font License 1.1 ([Audiowide](https://fonts.google.com/specimen/Audiowide/license),
  [Chakra Petch](https://fonts.google.com/specimen/Chakra+Petch/license),
  [JetBrains Mono](https://github.com/JetBrains/JetBrainsMono/blob/master/OFL.txt)).
- The name, the Orbit mark, logos and banners identify the Amy-WorkspAIce project. They are not
  covered by the apps' open-source licenses; forks distributed under another name should replace them.

---

# Brand book

Amy-WorkspAIce is the digital workspace of the future: chat, docs, files and calendar in one place, with Amy, its AI, built into all of it. The code is open source, so teams that want to can also run their own copy on their own servers, but that is a side option, not the headline. The brand is **retro sunset, future city**: an 80s synthwave sun sinking behind a cyberpunk skyline, seen through a HUD. It is built for dark mode first. Keep it basic: one sun, one neon accent at a time, lots of night.

## Name and voice

- Write the name exactly `Amy-WorkspAIce`: capital A, hyphen, capital W, capital `AI`. Never "Amy Workspace", "AMY-WORKSPAICE" in running text, or "Amy-Workspace".
- `Amy` alone means the assistant. She speaks in the first person, but only inside chat ("I found three docs that mention the Q3 budget."). Everywhere else the interface speaks as the product: "Your files", "Model loaded", "Couldn't reach the server. Retry".
- Tone: plain, confident, a little playful. Short sentences. No hype words ("revolutionary", "seamless", "unlock"), no exclamation marks in system copy, no emoji in the interface.
- Sentence case for buttons, titles and menus. Uppercase only through the `label` and `readout` styles.
- The tagline is "The digital workspace of the future", in sentence case and without a period when it stands alone. Lead with the workspace and Amy; mention open source and self-hosting second, as a supporting line (`OPEN SOURCE  //  SELF-HOSTABLE`), never as the headline.
- Readouts are the one place for terminal-style flavor: `SYS://AMY  ONLINE`, `INDEXING  1,204 FILES`. Keep them true and terse; never decorative nonsense.

## Color

- Dark is the primary theme; light exists for docs, print and people who need it. Design every screen in dark first, then check light.
- Grounds step up in four levels: `night-000` page, `night-100` cards and sidebars, `night-200` inputs and code, `night-300` hover and selection. Depth comes from these steps, not from shadows.
- Text: `ink` for primary text, `ink-muted` for supporting text, `ink-faint` for captions and placeholders (never on `night-300`).
- `magenta` is the brand. It fills the **one** primary action per screen (label in `on-magenta`), marks the active nav item and colors the hyphen in the wordmark. Don't use it for large backgrounds.
- `cyan` belongs to **Amy**. Use it for anything the AI says, does or suggests: her chat bubbles (`cyan-soft` ground), the "Ask Amy" button (`cyan` fill, `on-cyan` label), AI-generated badges. It also serves as `link` and `focus`. Don't use cyan for ordinary user actions.
- `solar` and `sunset` are the sun. Use them in illustration, charts and highlights. `warning` is `solar`.
- Status colors (`success`, `warning`, `danger`) always come with an icon or a word. `danger` is close to `magenta` in lightness, so a destructive button is outlined in `danger` with `danger` text, never a magenta-like fill.
- **Banded, never blended.** No gradients anywhere. When something needs to fade (a sky, a sun, a progress bar), step it in flat bands with dark slices between, like the logo's sun.
- Every text pair named in a token's note passes 4.5:1 in both themes. Control outlines use `line-strong` (3:1). `line` is only for decorative hairlines.

## Type

- `display` family (Audiowide): only the logo, hero headlines (`display-xl`) and page titles on marketing and empty states (`display`). Never in dense UI or body copy.
- `sans` family (Chakra Petch): the whole interface: `h1`, `h2`, `body`, `body-strong` for buttons, and `label` for nav groups and table headers, uppercase.
- `mono` family (JetBrains Mono): `code` for commands, paths and IDs; `readout` for status lines, uppercase.
- The fonts ship as files in `fonts/` (all SIL Open Font License). Serve them with the app instead of loading them from a CDN, so self-hosted copies look the same offline and on private networks.

## Shape, space and effects

- 4px grid: `space-1` to `space-12`. Cards pad `space-4`; panels pad `space-6`.
- Corners are sharp: `radius-0` by default, `radius-sm` for inputs and chips, `radius-md` for chat bubbles and menus.
- The cyberpunk accent is the **clipped corner**. Cut the top-left and bottom-right corners of filled shapes: `cut-sm` on filled buttons, badges and the active nav item, and `cut-md` on cards and dialogs. Use `clip-path: polygon(var(--cut-sm) 0, 100% 0, 100% calc(100% - var(--cut-sm)), calc(100% - var(--cut-sm)) 100%, 0 100%, 0 var(--cut-sm));`. Clip-path also cuts away outlines and focus rings, so outlined controls keep square corners.
- Glow is rare and means something. `focus-ring` goes on every focused control. `glow-cyan` goes on Amy's avatar and live bubble while she is thinking or speaking. `glow-magenta` is the hover for the primary action. `shadow-pop` is only for floating menus and dialogs.
- HUD corner brackets (cyan, square caps) frame hero images, banners and empty states. Never put them in dense UI.
- Scanlines are optional on hero imagery, at 10% black or less. Never put them over text or UI.

## Logo

- The mark is the **Orbit**: a sliced synthwave sun (solar, sunset, magenta, with slices that thicken downward) circled by a tilted cyan ring with a single node on it. The sun is the workspace; the ring and its node are Amy, always in orbit around your work. The ring passes behind the sun and in front of it, and every gap is real transparency, so the mark sits on any ground.
- Use `amy-workspaice-lockup.svg` (mark and wordmark) by default on dark grounds, and `amy-workspaice-lockup-light.svg` on light grounds. Use the stacked lockup for square spaces and the mark alone for avatars, favicons and small spaces.
- In the wordmark, `Amy-Worksp` and `ce` are `ink`, the hyphen is `magenta` and `AI` is `cyan`. Don't recolor the parts, retype the name in another font or set the wordmark without the mark at sizes below 120px wide.
- Clear space is half the sun's diameter on every side. Minimum sizes: the lockup is 160px wide and the mark is 24px wide. Below 24px, use `amy-workspaice-app-icon-32.png`.
- Use single-ink versions when color isn't available: `mark-mono-white` and `lockup-mono-white` on dark grounds or on a `magenta` fill, and `mark-mono-ink` on light grounds.
- Don't stretch, rotate or outline the mark, add gradients or drop shadows to it, change the ring's tilt, add more nodes or place the full-color mark on mid-tone or photographic grounds.
- The app icon is the Orbit floating over a magenta grid floor on a `night-100` tile with clipped corners and two cyan HUD ticks. Use it for app launchers, PWA icons and favicons.

## Banners

- `amy-workspaice-banner-github.svg` (1280×320) goes at the top of READMEs and docs. `amy-workspaice-banner-hero.svg` (1920×640) goes at the top of the website. Both have PNG twins at 2× for places that can't take SVG.
- All text in the banners and logos is outlined, so they render the same everywhere, including GitHub's image proxy. In a README: `<img src="docs/amy-workspaice-banner-github.svg" alt="Amy-WorkspAIce: the digital workspace of the future" width="100%">`.
- The scene is fixed: a banded night sky, the sliced sun right of center with the Orbit's ring around it, a low skyline with a few lit windows, the cyan horizon, a magenta grid floor, HUD corners and one readout top right. Keep the lockup, the tagline and the `OPEN SOURCE  //  SELF-HOSTABLE` line on the left, over plain sky.

## Iconography

- There's no custom icon set yet. Until there is, use one outline set with a 1.5px stroke and square caps (Tabler or Lucide), at 16px or 20px.
- Icons take `ink-muted`; they take `ink` when active and `cyan` when they belong to Amy. Status icons take their status color.
- No emoji in the interface.
