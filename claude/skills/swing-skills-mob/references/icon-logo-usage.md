# Swing Mobile — Icon and Logo Usage

Use this guide whenever a screen needs UI icons, product marks, partner logos, or a
Swing-branded lockup. Figma remains the source of truth; this guide is not a complete
export of every icon asset.

## 1. Find the right asset

1. Search **ADS: Foundations** (`JDN6zpJA4feGSY8ZcQMQeM`), especially `Icons (Final)`
   (`7:311`) for UI icons and `Logo` (`16:204`) / `Brand logos` (`41:38740`) for brand
   assets. Inspect the exact symbol or vector instance and record its actual node ID.
2. Inspect the requested screen or component in **ADS: For Mobile**
   (`ILlOBW8RpEBRmDvU6LQsx9`) to confirm its intended usage, variant, size, and state.
   Prefer an existing component instance when available.
3. Search `components.md` §20 and §21 for known names and source node IDs. If no matching
   use is documented, inspect the relevant Figma page directly; never infer an asset from
   a similar name.
4. Record assets needed for the screen in the handoff's icon/logo manifest below. The
   manifest is per deliverable; do not claim it is the complete Swing asset library.

| UI role | Figma name | Node ID | Instance size | Colour/variant | Export/source |
|---|---|---|---|---|---|
| <role> | <exact asset name> | <verified node ID> | <verified size> | <verified style> | <local asset path or native Figma instance> |

Use one row per distinct asset/variant. If any cell is unknown, mark it `UNDOCUMENTED`
instead of filling it by assumption.

## 2. UI icons

- Follow the observed Figma namespaces: `interface/<name>` for standard UI,
  `interface/so-<name>` for Swing-original icons, `arrow/<name>` for directional icons,
  and `Logo / <name>` for logo assets.
- Prefer the icon already used by the corresponding Swing component. Reuse its exact
  Figma instance, state, colour, and context-specific size.
- Treat sizes such as 10, 12, 14, 16, 18, 20, and 48 px as **observed contexts**, not a
  universal icon scale. See `components.md` §20 and use the exact size specified by the
  component being reproduced.
- Do not substitute emojis, text glyphs, Unicode symbols, CSS-drawn approximations, or an
  unrelated third-party icon set for a named Swing icon.
- Do not recolour, mirror, crop, stretch, or alter an icon unless the Figma component
  shows that variant. Preserve aspect ratio.
- Give meaningful icons an accessible name/label. Decorative icons should be hidden from
  assistive technology when the platform supports it.

## 3. Logos and brand marks

- Use the exact Figma `Logo / ...` asset or complete approved lockup for the intended
  context. Do not typeset a logo as plain text, recreate it from shapes, or compose a new
  lockup unless that exact treatment is documented or explicitly approved.
- Preserve the mark's aspect ratio, colour, internal proportions, clear space, and
  background treatment as shown in the source.
- Do not derive a monochrome, reversed, compact, or app-icon variant from another logo.
  If the needed variant is not present, report `UNDOCUMENTED` and ask for the approved
  asset.
- The inspected library confirms `Logo / Swing Pass icon` (`912:14146`), used at
  20 × 20 px in the `Swing Pass` component (`912:14145`). This is **not** evidence of a
  general Swing wordmark or every brand lockup.
- Foundations includes an `Icons (Final)` page (`7:311`) and separate `Logo`
  (`16:204`) and `Brand logos` (`41:38740`) pages. A sample verified icon is
  `sports/golf-stick` (`8:12868`), 24 × 24 px. This sample size is not a universal icon
  size; use the exact asset and mobile component context.

## 4. Using exported assets in code

- Prefer the design system's native component/instance in Figma. For code, export the
  exact verified vector/raster asset and store it in the repository using a descriptive,
  stable local path (for example `assets/icons/interface-search.svg`).
- Never use a temporary `figma.com/api/mcp/asset/...` URL as a production runtime source;
  such links expire. Download the asset while the URL is valid and reference the local
  file.
- Do not redraw a vector from a screenshot or re-export a different variant just to make
  an asset fit. Use the source component and preserve its geometry.
- Use consistent file names based on the verified Figma name and variant. Keep icon and
  brand-mark files separate, and do not overwrite an existing asset until the source has
  been confirmed.

## 5. What is not specified

The inspected library documents names and sizes in component contexts, but does not
provide a complete standalone icon catalog, universal grid, stroke-width rule, spacing
clearance for every logo, or a full list of approved logo lockups. These are
`UNDOCUMENTED` unless verified directly in the relevant Figma asset.
