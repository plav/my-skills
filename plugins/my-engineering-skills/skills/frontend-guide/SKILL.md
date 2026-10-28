---
name: frontend-guide
description: Checklist for building user interfaces. Use when building or reviewing UI components, managing state, fetching data in the browser, handling forms, checking accessibility or responsiveness, or improving front-end performance.
---

# Frontend

## Checklist
- Where does each piece of state live? (local, shared, server, URL)
- Loading, empty and error states for every fetch
- Accessible: semantic HTML, labels, keyboard navigation, contrast
- Works on mobile and desktop
- Inputs validated on the client for UX and on the server for safety
- Measure performance before optimising

## State
- Local: belongs to one component
- Shared: lift up or use a store only when several components need it
- Server state: cache with a data-fetching library; don't copy it into local state
- URL: filters, tabs, pages, so they survive refresh and can be shared
- Derive values instead of storing duplicates

## Components
- Small, focused, reusable where it genuinely helps
- Props in, events out; avoid reaching into other components
- Keep business logic out of UI components where practical

## Accessibility
- Use real elements (button, a, label) before ARIA
- Every input has a label; images have alt text
- Everything usable by keyboard; visible focus
- Colour contrast and not relying on colour alone
- Test with a screen reader and an automated checker

## Forms
- Clear labels and error messages next to the field
- Disable double submit; show progress

## Performance
- Bundle size, image size, unnecessary re-renders are common culprits
- Lazy-load heavy parts; paginate long lists
- Track Core Web Vitals

## Further reading
- MDN Web Docs: https://developer.mozilla.org/en-US/
- web.dev Learn: https://web.dev/learn
- WCAG overview: https://www.w3.org/WAI/standards-guidelines/wcag/
