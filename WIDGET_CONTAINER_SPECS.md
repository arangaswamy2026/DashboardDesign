# Widget Container Specifications

## Overview
Reusable dashboard widget container with fluid width and fixed height. Designed for data visualization and dashboard displays in enterprise security operations interfaces.

---

## Container Dimensions

| Property | Value | Notes |
|----------|-------|-------|
| **Width** | 100% (fluid) | Scales with parent container |
| **Height** | 462px (fixed) | Fixed height for consistent dashboard layout |
| **Border Radius** | 8px | Applied to container corners |
| **Gap** | 12px | Spacing between internal sections |

---

## Container Structure

The widget is composed of **3 fixed-height sections**:

### 1. Header Section (69px)
**Purpose:** Title, context, controls, and actions

**Dimensions:**
- Height: 69px
- Padding: 12px all sides
- Width: 100%
- Border radius: 8px (top corners)

**Background & Borders:**
- Background: `var(--⬛️-surface/model, #f0f2f5)`
- Border: None (inherits container border)

**Layout:**
- Display: flex
- Direction: row
- Gap: 12px
- Items: start-aligned
- Justify: space-between (implied by element placement)

**Child Elements (Left to Right):**

| Element | Dimensions | Purpose |
|---------|-----------|---------|
| SubApp Icon Placeholder | 40×40px | Application/tenant icon |
| Title + Context Text | flex 1 | Widget title (16px, ExtraBold) and tenant/device info (14px, Regular) |
| Period Selector | 96px wide | Dropdown for time range selection (7 Days, etc.) |
| Button Group | 72px wide | View mode toggles (list/graph icons) |
| Overflow Menu | 29×29px | More actions button |

**Typography:**
- Widget Title: Nunito Sans, ExtraBold, 16px, uppercase, `#191c25`
- Context: Nunito Sans, Regular, 14px, `#191c25`

---

### 2. Content Slot (328px)
**Purpose:** Primary data visualization area (graph, table, chart, etc.)

**Dimensions:**
- Height: 328px
- Width: 100%
- Padding: 10px horizontal
- Margin: 0

**Background & Borders:**
- Background: `var(--⬛️-surface/tertiary, #f6f8fe)`
- Border: None

**Layout:**
- Display: flex
- Direction: column
- Items: center-aligned
- Justify: center

**Notes:**
- This is a **slot/placeholder** for dynamic content
- Content is absolutely centered within the space
- Accommodates charts, tables, lists, or custom visualizations

---

### 3. Footer Section (42px)
**Purpose:** Secondary actions and navigation (View More, pagination, etc.)

**Dimensions:**
- Height: 42px
- Padding: 12px all sides
- Width: 100%
- Border radius: 8px (bottom corners)

**Background & Borders:**
- Background: `var(--🔲-border/selected, white)`
- Border: None

**Layout:**
- Display: flex
- Direction: row
- Justify: flex-end
- Gap: 10px
- Items: center-aligned

**Typography:**
- Label: Nunito Regular, 13px, `#4a618f` (secondary text)

---

## Color Palette (Design Tokens)

### Surfaces
| Token | Value | Usage |
|-------|-------|-------|
| `--⬛️-surface/container` | `#ffffff` | Container background |
| `--⬛️-surface/model` | `#f0f2f5` | Header background |
| `--⬛️-surface/tertiary` | `#f6f8fe` | Content area background |
| `--⬛️-surface/contrast` | `#111315` | High-contrast elements (active button) |

### Borders
| Token | Value | Usage |
|-------|-------|-------|
| `--🔲-border/primary` | `#9dafd3` | Container border |
| `--🔲-border/tertiary` | `#cccccc` | Input/control borders |
| `--🔲-border/transparent` | `rgba(17,17,17,0.09)` | Subtle dividers |
| `--🔲-border/selected` | `#ffffff` | Footer background |

### Text
| Token | Value | Usage |
|-------|-------|-------|
| `--🈂️-text/primary` | `#191c25` | Main text |
| `--🈂️-text/secondary` | `#4a618f` | Secondary text (footer labels) |

---

## Typography System

| Role | Font | Weight | Size | Line Height | Letter Spacing | Case |
|------|------|--------|------|-------------|-----------------|------|
| Widget Title | Nunito Sans | ExtraBold (800) | 16px | 1.5 | 0 | UPPERCASE |
| Widget Subtitle | Nunito Sans | Regular (400) | 14px | 1.5 | 0 | Sentence |
| Button/Label | Nunito | Regular (400) | 13px | 100% | 0 | Sentence |
| Content Placeholder | Nunito Sans | Regular (400) | 20px | 1.5 | 0 | Sentence |

**Font Variation Settings:** `"YTLC" 500, "wdth" 100` (applied to Nunito Sans variants)

---

## Spacing System

| Property | Value | Usage |
|----------|-------|-------|
| Container padding | 12px (header/footer) | Outer spacing from section edges |
| Section gap | 12px | Vertical spacing between header, content, footer |
| Element gap | 12px (header) | Horizontal spacing between header controls |
| Content padding | 10px | Horizontal padding within content area |
| Control padding | 6.5px–10px | Internal padding of buttons/inputs |

---

## Border & Radius

| Property | Value | Usage |
|----------|-------|-------|
| Container radius | 8px | All corners |
| Header radius | 8px top-left, 8px top-right | Rounded top corners only |
| Footer radius | 8px bottom-left, 8px bottom-right | Rounded bottom corners only |
| Input/Button radius | 4px–6px | Form controls (inputs, buttons) |

**Container Border:**
- Style: solid
- Width: 1px
- Color: `var(--🔲-border/primary, #9dafd3)`

---

## Component Nesting & Sizing

### Internal Components (Reusable)

| Component | Figma Reference | Dimensions | Purpose |
|-----------|-----------------|-----------|---------|
| Period Selector | 3243:85293 | 96×29px | Time range dropdown |
| Button Group | 4977:194077–194102 | 72×29px | Toggle buttons (List/Graph view) |
| Form Button (Overflow) | 10156:576 | 29×29px | Menu trigger |
| Subapp Icon Container | 10406:8820 | 40×40px | Icon placeholder |

**Reference:** [UUIF 9.2 Button Component](https://uuif-9.2.eng.sonicwall.com/m/components/button)

---

## Responsive Behavior

| Breakpoint | Width | Behavior |
|-----------|-------|----------|
| Mobile | 100% | Scales to container width |
| Tablet | 100% | Scales to container width |
| Desktop | 100% | Scales to container width |

**Height:** Always 462px across all breakpoints.

---

## Accessibility & Semantics

- Container uses semantic HTML structure (sections with clear landmark roles)
- Header contains navigation and title information (role: banner/section)
- Content area is main content region (role: main or article)
- Footer contains secondary navigation (role: contentinfo/section)
- All icons include alt text or aria-labels as needed
- Color contrast: All text meets WCAG AA standards
- Interactive elements: Minimum 44×44px touch target (buttons are 29–72px)

---

## Implementation Notes

### CSS Custom Properties (Design Tokens)

The widget relies on UUIF 9.2 design tokens. Ensure the following CSS variables are defined in your project's theme:

```css
/* Surface tokens */
--⬛️-surface/container: #ffffff;
--⬛️-surface/model: #f0f2f5;
--⬛️-surface/tertiary: #f6f8fe;
--⬛️-surface/contrast: #111315;

/* Border tokens */
--🔲-border/primary: #9dafd3;
--🔲-border/tertiary: #cccccc;
--🔲-border/transparent: rgba(17, 17, 17, 0.09);
--🔲-border/selected: #ffffff;

/* Text tokens */
--🈂️-text/primary: #191c25;
--🈂️-text/secondary: #4a618f;

/* Dimension tokens */
--demension/radios/4: 4px;
--demension/radios/6: 6px;
--demension/radios/22: 22px;
```

### Flexbox Layout

All sections use CSS flexbox. Key properties:
- Header: `flex-direction: row; gap: 12px; align-items: flex-start;`
- Content: `flex-direction: column; gap: 0; align-items: stretch; justify-content: center;`
- Footer: `flex-direction: row; gap: 10px; align-items: center; justify-content: flex-end;`

### Content Slot Strategy

The content area (328px) is a **slot/placeholder** pattern:
- Reserve this space for dynamic content (charts, tables, etc.)
- Content should be centered within the 328px height
- Recommend using a component composition pattern to inject content

---

## Example Usage (React)

```jsx
interface WidgetContainerProps {
  title: string;
  context: string;
  onPeriodChange?: (period: string) => void;
  onViewToggle?: (view: 'list' | 'graph') => void;
  children: React.ReactNode; // Content slot
}

export function WidgetContainer({
  title,
  context,
  onPeriodChange,
  onViewToggle,
  children,
}: WidgetContainerProps) {
  return (
    <div className="widget-container" style={{ height: '462px', width: '100%' }}>
      {/* Header Section */}
      <div className="widget-header">
        {/* Icon, title, controls */}
      </div>

      {/* Content Slot */}
      <div className="widget-content">{children}</div>

      {/* Footer Section */}
      <div className="widget-footer">
        {/* Secondary actions */}
      </div>
    </div>
  );
}
```

---

## Design System Integration

**Design System:** UUIF 9.2
**Reference Host:** `uuif-9.2.eng.sonicwall.com`
**Figma File:** [Unified Dashboard Widget Template](https://www.figma.com/design/LoUaZIsXueeeFKdmzHeTIG/Unified-Dashboard?node-id=10471-6275)
**Figma Node ID:** 10471:6275

---

## Version & Changes

| Version | Date | Notes |
|---------|------|-------|
| 1.0 | 2026-09-24 | Initial specification extraction |
