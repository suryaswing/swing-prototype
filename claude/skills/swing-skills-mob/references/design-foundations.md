# Swing Design Foundations

Use **ADS: Foundations** as the source for Swing's foundational visual assets and
primitives, and **ADS: For Mobile** for how those foundations are applied to mobile
components, layouts, and states. Both files are authoritative within their scope.

## Official Figma sources

| File | Figma key | Responsibility |
|---|---|---|
| [ADS: Foundations](https://www.figma.com/design/JDN6zpJA4feGSY8ZcQMQeM/ADS--Foundations?node-id=8-12868) | `JDN6zpJA4feGSY8ZcQMQeM` | Base palette, elevation, icon and brand/logo assets |
| [ADS: For Mobile](https://www.figma.com/design/ILlOBW8RpEBRmDvU6LQsx9/ADS--For-Mobile?node-id=149-4844) | `ILlOBW8RpEBRmDvU6LQsx9` | Mobile components, layout, typography usage, and interaction states |

### Foundations page map

These page names and IDs were inspected in the Foundations file:

| Page | Node ID | Use |
|---|---|---|
| Colors | `3:168` | Inspect named color families and shades |
| Elevation | `24:2` | Inspect elevation/shadow examples |
| Icons (Final) | `7:311` | Search for approved UI icon assets |
| Brand logos | `41:38740` | Search for brand and third-party logo assets |
| Logo | `16:204` | Inspect Swing's logo and brand rationale |

## Verified foundation examples

The `PURPLE` palette frame (`10:229`) exposes these exact values:

| Shade | Value | Source node |
|---|---|---|
| `PURPLE/700` | `#360087` | `16:20` |
| `PURPLE/600` | `#4900B8` | `10:230` |
| `PURPLE/500` | `#5C00E6` | `10:233` |
| `PURPLE/300` | `#B284F9` | `10:236` |
| `PURPLE/100` | `#E6DCFA` | `10:239` |
| `PURPLE/50` | `#F9F3FF` | `10:242` |

The inspected palette frame does not show `PURPLE/400` or `PURPLE/200`; do not infer
their values. A verified icon example is `sports/golf-stick` (`8:12868`), shown at
24 × 24 px. This is an example, not a universal icon size.

The `Logo` page contains an `Eagle Logo Philosophy` frame (`16:211`) titled “Swing's
Eagle Logo.” This confirms the page's brand context, but does not by itself establish
which logo lockup, clear-space rule, color treatment, or size is appropriate for every
product context. Inspect the exact logo variant before use.

## Rules for applying foundations to Mobile

1. Inspect the live Foundation source for the exact base token or asset relevant to the
   task; do not rely solely on this snapshot.
2. Inspect the Mobile library for the component or screen context that applies it.
   A color shade or asset existing in Foundations does not prove that every Mobile
   component uses or supports it.
3. Keep the two sources' roles distinct: Foundations establishes the base visual
   vocabulary; Mobile establishes mobile-specific component variants, dimensions,
   layout, and interaction behavior.
4. If the files disagree or a Mobile usage cannot be found, report the discrepancy or
   mark the usage `UNDOCUMENTED`. Do not silently override a component specification.
5. Cite the Figma file and node IDs for values and assets included in a deliverable.
   Re-verify relevant values in Figma before each design task.

The color values currently captured from both sources are indexed in
[design-tokens.md](./design-tokens.md) and [color-system.md](./color-system.md).
Icon and logo selection/export rules are in [icon-logo-usage.md](./icon-logo-usage.md).
