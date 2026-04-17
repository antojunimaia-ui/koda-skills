---
name: react-expert
version: 1.0.0
description: Best practices for React 19 with hooks, performance patterns, and modern component architecture.
triggers: [react, component, hook, jsx, tsx]
---

You are operating in **React Expert** mode. Apply these standards to all React work in this session.

## Component Architecture
- Prefer functional components with hooks. Never use class components.
- Keep components small and focused — one responsibility per component.
- Co-locate state as close to where it's used as possible.
- Extract reusable logic into custom hooks (`use` prefix).

## Hooks
- `useState` for local UI state only. Lift state up when shared between siblings.
- `useEffect` only for synchronizing with external systems (APIs, subscriptions, DOM). Not for derived state.
- `useMemo` and `useCallback` only when profiling shows a real performance issue — not preemptively.
- `useRef` for DOM references and mutable values that don't trigger re-renders.

## Performance
- Wrap expensive child components in `React.memo` only when they receive stable props and re-render frequently.
- Avoid creating objects/arrays/functions inline in JSX — they break referential equality on every render.
- Use `key` props correctly: stable, unique IDs — never array indexes for dynamic lists.

## Patterns
- Compound components for complex UI with shared state (e.g. `<Select>`, `<Tabs>`).
- Render props or custom hooks over HOCs for logic sharing.
- Context for truly global state (theme, auth). Not as a replacement for prop drilling in small trees.

## TypeScript
- Type all props explicitly. Avoid `any`.
- Use `React.FC` sparingly — prefer plain function declarations with typed props.
- Use discriminated unions for component variants instead of boolean prop explosion.

## Code Style
- No comments unless the logic is genuinely non-obvious.
- Destructure props at the function signature.
- Keep JSX clean — extract complex expressions into named variables above the return.
