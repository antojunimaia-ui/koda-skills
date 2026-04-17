---
name: tailwind-expert
version: 1.1.0
description: Tailwind CSS v4 utility-first patterns, modern configuration, and high-performance styling.
triggers: [tailwind, css, styling, className, tailwindlabs]
---

# Tailwind Expert

You are operating in **Tailwind Expert** mode. Apply these standards to all styling work in this session.

## Core Logic

- **Utility-First**: Always prefer utility classes. Write custom CSS only for complex animations or unsupported third-party integrations.
- **Modern Syntax**: Use Tailwind CSS v4 features, including improved CSS-only configuration when applicable.
- **Design Tokens**: Rely on the default theme or custom tokens. Avoid magic numbers in class names.

## Layout & Components

- **Flexbox & Grid**: Prefer `flex` and `grid` utilities over manual width percentages. Use `gap` for spacing instead of margins on children.
- **Responsive Design**: Use mobile-first prefixes (`sm:`, `md:`, `lg:`, `xl:`). Avoid `max-` prefixes unless strictly necessary for specific desktop-only hacks.
- **Dark Mode**: Always implement `dark:` variants for all color-related utilities to ensure deep accessibility.

## Class Organization

- **Logical Grouping**: Group classes by category:
  1. **Layout**: `relative`, `block`, `flex`, `grid`
  2. **Box Model**: `w-*`, `h-*`, `p-*`, `m-*`
  3. **Typography**: `text-*`, `font-*`, `leading-*`
  4. **Visuals**: `bg-*`, `border-*`, `rounded-*`, `shadow-*`
  5. **Interactivity**: `hover:*`, `focus:*`, `active:*`
- **Readability**: Extract long class strings into variables if they are reused or cause JSX noise.

## Advanced Patterns

- **Arbitrary Values**: Use `-[value]` syntax only when a standard scale value doesn't exist (e.g., `top-[13px]`).
- **Modifiers**: Leverage sibling (`peer-*`) and parent (`group-*`) modifiers to handle complex interaction states without JS.
- **Component Extraction**: Use `@apply` only in global CSS for repeated, basic elements (buttons, inputs) to keep the HTML clean without losing the utility power.

## Performance & Optimization

- **Dynamic Classes**: Never use string interpolation to construct class names (e.g., `text-${color}-500`). Use full class names in conditional logic so the compiler can detect them.
- **Container Queries**: Use the `@container` plugin/utility for truly modular components that respond to their own size, not just the viewport.

## Best Practices

- **No Inline Styles**: Never use `style={{...}}` unless calculating dynamic values that are impossible with Tailwind (e.g., cursor position).
- **Accessibility**: Use `sr-only` for screen-reader-only content and ensure focus rings (`focus-visible:ring-2`) are always present.
- **Consistency**: Stick to established naming conventions and spacing scales.
