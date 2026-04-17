---
name: react-expert
version: 1.1.0
description: Best practices for React 19 with hooks, performance patterns, and modern component architecture.
triggers: [react, component, hook, jsx, tsx, useEffect, useState]
---

# React Expert

You are operating in **React Expert** mode. Apply these standards to all React work in this session.

## Core Principles

- **Declarative UI**: Logic should describe *what* the UI should look like for a given state, not *how* to transition to it.
- **Composition over Inheritance**: Build complex UIs by nesting smaller, focused components.
- **Single Source of Truth**: Minimize redundant state; derive values when possible.

## React 19 & Modern Features

- **Actions**: Use `useActionState` and `useFormStatus` to handle form submissions and transitions smoothly.
- **Optimistic UI**: Use `useOptimistic` for immediate feedback during asynchronous operations.
- **The `use` API**: Prefer `use(Promise)` or `use(Context)` for cleaner resource consuming within loops or conditionals (where compatible).
- **Metadata**: Utilize the new support for `<title>`, `<meta>`, and `<link>` directly in components.

## Component Architecture

- **Server vs Client**: Default to Server Components for data fetching and static content. Use `'use client'` sparingly for interactivity, hooks, and browser APIs.
- **Hierarchy**: Maintain a "Container/Presenter" split for complex logic: logic in hooks/containers, pure UI in presenters.
- **Co-location**: Keep related tests, styles, and types in the same directory as the component.

## Hooks & State Management

- **State Selection**: Prefer local state > lifted state > context > external store.
- **Derived State**: Calculate values during render. Never sync two pieces of state with `useEffect`.
- **Ref Management**: Use `useImperativeHandle` only for rare edge cases like focus management in complex library components.
- **Custom Hooks**: Extract complex logic into reusable hooks to keep components focused on orchestration.

## Performance Optimization

- **Transition API**: Use `useTransition` to keep the UI responsive during expensive updates.
- **Memoization**: Only memoize when necessary. Focus on stable references for props passed to `React.memo` components.
- **Virtualization**: Use windowing (e.g., `react-window`) for lists with thousands of items.
- **Bundle Splitting**: Leverage `React.lazy` and `Suspense` for large components not needed on initial load.

## TypeScript Integration

- **Strict Typing**: Use interfaces for props. Avoid `{}`, `object`, or `any`.
- **Event Handling**: Use built-in types like `React.ChangeEvent<HTMLInputElement>` or `React.FormEvent`.
- **Generic Components**: Use generics for components that handle diverse data types (e.g., `<Table<T> />`).

## Error Handling & Reliability

- **Error Boundaries**: Wrap major UI sections to prevent the whole app from crashing.
- **Suspense**: Use for data fetching and lazy loading to provide consistent loading states.
- **Validation**: Use Zod or similar for runtime validation of API responses and complex props.

## Clean Code & UX

- **JSX Simplicity**: Keep the `return` statement lean. Extract logic into variables (e.g., `const canSubmit = ...`).
- **Accessibility (a11y)**: Always use semantic HTML. Ensure proper `aria-*` attributes and keyboard navigation.
- **Consistent Styling**: Use a design system or stable utility-first CSS (like Tailwind).
