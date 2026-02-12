## Rules

1. Use strict TypeScript typing; avoid `any` unless absolutely necessary
2. Prefer existing components (shadcn/ui, `components/ui/`, `components/common/`) over creating new ones
3. Prefer no hard-coded colors, font sizes, or spacing; use Tailwind theme values or CSS variables
4. Avoid unnecessary code comments; code should be self-documenting
5. Keep components small and focused; separate UI, state, and business logic
6. Maintain backwards compatibility when modifying shared components; add optional props rather than changing existing behavior

## React Performance
- Wrap expensive child components with `memo()` and use `useMemo`/`useCallback` for non-primitive props.
- Hoist non-primitive default prop values to module-level constants (e.g., `const NOOP = () => {}`) — inline defaults break `memo()`.
- Derive state during render; never use `useEffect` + `setState` for values computable from props/state.