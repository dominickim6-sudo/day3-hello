# Design System Strategy: The Midnight Monolith

## 1. Overview & Creative North Star
The Creative North Star for this design system is **"The Midnight Monolith."** 

This isn't just a portfolio; it is a cinematic, editorial experience. We are moving away from the "standard dashboard" look. Instead, we treat the 220px sidebar as a fixed architectural anchor and the main content as a flowing gallery. The aesthetic balances the technical precision of a code editor with the high-contrast drama of a fashion lookbook. We achieve this through "Atmospheric Depth"—using layers of darkness rather than lines to define space—and "Type as Texture," where massive headlines serve as visual elements themselves.

---

## 2. Colors: Tonal Architecture
We use a monochromatic dark base to allow the **Primary (#ffb2b7)** and **Accent (#e94560)** colors to feel like light sources in a dark room.

*   **The "No-Line" Rule:** Prohibit 1px solid borders for sectioning. To separate the sidebar from the main content, use a shift from `surface_container` (#1c2026) to `surface` (#10141a). Boundaries are felt through tonal transitions, not drawn with strokes.
*   **Surface Hierarchy & Nesting:** 
    *   **Level 0 (The Void):** `surface_container_lowest` (#0a0e14) for the deepest background areas.
    *   **Level 1 (The Base):** `surface` (#10141a) for the main scrollable canvas.
    *   **Level 2 (The Raised):** `surface_container` (#1c2026) for cards and sidebar.
*   **The "Glass & Gradient" Rule:** Floating elements (like the KakaoTalk FAB or navigation highlights) should use a `surface_variant` (#31353c) at 60% opacity with a `20px` backdrop-blur. 
*   **Signature Textures:** Apply a subtle linear gradient to the `primary_container` (#fc536d) buttons, transitioning from the accent color to a slightly deeper shade to simulate a premium, matte-metallic finish.

---

## 3. Typography: Editorial Authority
The contrast between the geometric **Manrope** and the functional **Inter** creates a "Tech-Luxury" hybrid.

*   **Display-lg (Manrope, 3.5rem):** Reserved for project titles. Use tight letter-spacing (-0.04em) to make the type feel like a solid block.
*   **Headline-md (Manrope, 1.75rem):** Used for section headers (e.g., "Resume," "Journal"). These should always be `on_surface`.
*   **Body-md (Inter, 0.875rem):** The workhorse for descriptions. Use `on_surface_variant` to keep the hierarchy clear and reduce eye strain in dark mode.
*   **Label-sm (Inter, 0.6875rem):** All-caps with 0.1em letter-spacing for "Overlines" or dates in the timeline to provide a "technical blueprint" feel.

---

## 4. Elevation & Depth: Atmospheric Layering
We do not "box" content. We "layer" light.

*   **The Layering Principle:** Place a `surface_container_high` (#262a31) card on top of the `surface` (#10141a) background. This creates a natural "lift" without needing a single pixel of border.
*   **Ambient Shadows:** For floating elements, use a shadow: `0 20px 40px rgba(0, 0, 0, 0.4)`. The shadow color must be `surface_container_lowest` (#0a0e14), never pure black, to keep the dark theme feeling "airy."
*   **The "Ghost Border" Fallback:** If a divider is essential for accessibility, use the `outline_variant` (#5a4042) at **15% opacity**. It should be a suggestion of a line, not a statement.
*   **Interaction Glow:** When hovering over a project card, apply a subtle inner-glow using the `primary` (#ffb2b7) color at 5% opacity to simulate the card "charging" with light.

---

## 5. Components

### Sidebar (The Monolith)
*   **Background:** `surface_container` (#1c2026).
*   **Interaction:** Active links use a `primary` left-border (2px) and a `primary_container` ghost-fill. Avoid icons in boxes; use raw glyphs for a cleaner silhouette.

### Project Cards
*   **Structure:** No borders. Use `surface_container_low` (#181c22). 
*   **Imagery:** Images should have a slight `0.8` opacity, hitting `1.0` on hover. Use `md` (0.375rem) rounded corners to maintain a sharp, modern edge.

### Vertical Timeline (The Pulse)
*   **The Line:** Do not use a solid 1px line. Use a 2px wide gradient transitioning from `outline_variant` to `transparent`.
*   **Nodes:** Use `primary` (#ffb2b7) rings with a `primary_fixed` glow effect.

### Contact Form & KakaoTalk
*   **Inputs:** Use `surface_container_highest` (#31353c) with a "Ghost Border" that turns `primary` only on focus.
*   **KakaoTalk Button:** Do not use the standard bright yellow. Use a `tertiary_container` (#89929c) base with the Kakao icon in `on_tertiary_fixed`, transitioning to a muted gold on hover to maintain the high-end palette.

---

## 6. Do’s and Don’ts

### Do:
*   **DO** use whitespace (64px+) between sections to allow the dark theme to "breathe."
*   **DO** use `surface_bright` (#353940) for very small UI elements like tooltips to ensure they pop against the dark background.
*   **DO** align text to a strict baseline grid to maintain the editorial "structured" look.

### Don’t:
*   **DON'T** use 100% white (#ffffff) for text. Use `on_surface` (#dfe2eb) to prevent "halving" (text glowing and blurring) on OLED screens.
*   **DON'T** use standard "Drop Shadows" on cards. Rely on color-shifting (`surface` vs `surface_container`) to define the shape.
*   **DON'T** use generic "Read More" buttons. Use text-links with a `primary` underline that grows on hover.