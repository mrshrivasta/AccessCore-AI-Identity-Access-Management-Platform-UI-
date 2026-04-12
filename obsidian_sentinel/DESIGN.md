# Design System Strategy: The Sentinel Aesthetic

## 1. Overview & Creative North Star
**Creative North Star: "The Digital Vault"**

Identity and Access Management (IAM) is the bedrock of enterprise security. To move beyond the generic "SaaS dashboard" look, this design system adopts the **Sentinel Aesthetic**. It treats the interface not as a collection of boxes, but as a high-fidelity command center—an environment defined by atmospheric depth, authoritative typography, and a "light-through-glass" philosophy.

The system breaks the standard grid-based monotony through **intentional asymmetry** and **tonal density**. We lean into the high-density requirements of security tools by using sophisticated layering rather than claustrophobic borders. The result is an experience that feels impenetrable yet fluid—conveying "Trust" not through blue buttons, but through professional precision and visual calm.

---

## 2. Colors: Tonal Architecture
The palette is built on deep, nocturnal blues and teals, shifting away from "flat black" to create a sense of infinite digital space.

### The "No-Line" Rule
**Explicit Instruction:** Designers are prohibited from using 1px solid borders for sectioning or layout containment. Structural separation must be achieved through:
1.  **Background Shifts:** Placing a `surface_container_low` section against a `surface` background.
2.  **Shadow-Defined Edges:** Using ambient light to define a boundary.
3.  **Vertical Space:** Leveraging the spacing scale to create mental groupings.

### Surface Hierarchy & Nesting
Treat the UI as a series of physical layers—stacked sheets of obsidian and frosted glass.
*   **Base Layer (`surface` / `#101419`):** The foundation of the application.
*   **Secondary Layer (`surface_container` / `#1c2025`):** Used for primary navigation or sidebar zones.
*   **Tertiary Layer (`surface_container_high` / `#262a30`):** Used for main content cards.
*   **Accent Layer (`surface_container_highest` / `#31353b`):** Reserved for hover states or active selection focus.

### The "Glass & Glow" Rule
To evoke a premium, modern feel, floating elements (modals, dropdowns, popovers) must use **Glassmorphism**:
*   **Background:** `surface_container_low` at 80% opacity.
*   **Backdrop Blur:** 12px to 20px.
*   **Signature Glow:** Use `primary_container` with a 40% opacity glow (rgba(37, 99, 235, 0.4)) as a soft under-glow for critical status indicators or active hero elements.

---

## 3. Typography: Editorial Authority
We utilize a dual-font system to balance technical precision with high-end editorial flair.

*   **Display & Headlines (Manrope):** Chosen for its geometric modernism. Large scales (`display-lg` to `headline-sm`) should use tighter letter-spacing (-0.02em) to feel "locked in" and authoritative.
*   **Body & Labels (Inter):** The industry standard for legibility. At `body-sm` and `label-sm` scales, Inter provides the "high-density" clarity required for audit logs and permission matrices.
*   **Hierarchy as Identity:** Use `tertiary` (`#d2bbff`) for small accent labels or category tags to create a sophisticated "Cyber-Chic" contrast against the deep blue primary tones.

---

## 4. Elevation & Depth: Tonal Layering
In the Sentinel Aesthetic, depth is a function of light, not lines.

*   **The Layering Principle:** Never place two elements of the same surface token next to each other. If a card sits on a background, the card must be at least one tier higher (`surface_container_low` on `surface`).
*   **Ambient Shadows:** Avoid "Drop Shadows." Instead, use **Ambient Occlusion Shadows**:
    *   `Box-shadow: 0 20px 40px rgba(0, 0, 0, 0.4), 0 0 0 1px rgba(141, 144, 160, 0.05);`
    *   This creates a soft lift while the subtle 1% "Ghost Border" ensures the element doesn't bleed into the background on uncalibrated monitors.
*   **The Ghost Border:** If containment is required for high-density data tables, use `outline_variant` at **15% opacity**. Anything more is visual noise.

---

## 5. Components: Precision Primitives

### Buttons
*   **Primary:** Solid `primary_container` (#2563EB). No border. Soft 4px (`DEFAULT`) radius. 
*   **Secondary:** Glass-style. Background: `secondary_container` at 20% opacity. Text: `secondary`.
*   **Tertiary:** No background. Text: `primary`. Subtle underline on hover.

### Cards & Data Lists
*   **Rule:** Forbid divider lines. 
*   **Implementation:** Separate list items by alternating between `surface` and `surface_container_low` backgrounds, or use 12px of vertical "air" between items.
*   **Hover State:** Shift background to `surface_bright` and add the "Signature Glow" as a 2px vertical stripe on the left edge.

### Input Fields
*   **Style:** Minimalist. No bottom border or full box. 
*   **Standard:** Use `surface_container_lowest` with a "Ghost Border" of 10% `outline`. 
*   **Focus State:** The border opacity jumps to 100% `primary`, accompanied by a subtle 4px `primary` outer glow.

### IAM-Specific Components
*   **Access Badges:** Small, pill-shaped chips using `tertiary_container` with `on_tertiary_container` text. These must look like "keys" or "tokens."
*   **Status Orbs:** Instead of simple green/red dots, use 8px blurred orbs (`success` or `error`) to simulate an active LED hardware light.

---

## 6. Do's and Don'ts

### Do
*   **Do** use asymmetrical layouts for dashboards (e.g., a wide 8-column main view with a 4-column "Global Activity" sidebar).
*   **Do** lean into `surface_container_highest` for "active" or "focused" states to create a physical sense of "pressing a button."
*   **Do** use `primary_fixed_dim` for text that needs to be prominent but not jarring.

### Don't
*   **Don't** use 100% white (#FFFFFF) for text. Always use `on_surface` (#E0E2EA) to reduce eye strain in dark mode.
*   **Don't** use default browser scrollbars. Style them to be thin, `surface_variant` tracks with `secondary_fixed_dim` thumbs.
*   **Don't** use "Alert Red" for everything. Use the `secondary` or `outline` tokens for "Warning" states to keep the UI from looking like a Christmas tree; reserve `error` only for total system failures or security breaches.