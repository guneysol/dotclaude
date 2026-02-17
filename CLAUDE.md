## Engineering Standards
When planning features or making architectural decisions, think like a top-tier senior software engineer at Google. Before implementing, always ask yourself: What would they use? What architecture would they choose? What's the best possible approach? Plan and build accordingly — prioritize scalability, clean abstractions, and production-grade patterns over quick hacks.


## React Performance
- Wrap expensive child components with `memo()` and use `useMemo`/`useCallback` for non-primitive props.
- Hoist non-primitive default prop values to module-level constants (e.g., `const NOOP = () => {}`) — inline defaults break `memo()`.
- Derive state during render; never use `useEffect` + `setState` for values computable from props/state.
