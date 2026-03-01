# Pet Profile Card - Architecture Blueprint

## Tech Stack
- **Frontend:** HTML5 + Tailwind CSS (CDN)
- **No backend** - static file, file:///index.html
- **No database** - localStorage only

## Project Structure
```
pet-profile-card/
├── docs/
│   ├── PRD.md
│   └── ARCHITECTURE_BLUEPRINT.md
├── dev/
│   └── index.html
└── qc/
    └── (test files)
```

## Implementation Details

### HTML Structure
- Single `index.html` file
- Tailwind via CDN (v3.4.x)
- Unsplash image for cat photo

### CSS Approach
- Tailwind utility classes
- Custom CSS in `<style>` tag for:
  - Dark mode transition
  - Hover animation (scale + shadow)

### JavaScript
- Inline script for:
  - Dark/Light mode toggle
  - localStorage persistence (`pet-profile-theme`)
  - Theme initialization on page load

### Responsive Breakpoints
- Mobile: < 640px (w-full, max-w-xs)
- Tablet: 640px - 1024px (max-w-md)
- Desktop: > 1024px (max-w-lg)

## Card Components
1. **Photo Section:** 200x200px rounded-full image
2. **Info Section:** Name, Age, Breed
3. **Personality:** Tag list
4. **Hobbies:** Tag list
5. **Theme Toggle:** Sun/Moon icon button

## Dark Mode
- CSS class `.dark` on `<html>` element
- Tailwind dark: prefix
- localStorage key: `pet-profile-theme`
- Values: `light` | `dark`

## Hover Animation
```css
.card {
  transition: transform 0.3s, box-shadow 0.3s;
}
.card:hover {
  transform: scale(1.05);
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
}
```

## Acceptance Criteria
- [ ] Card displays centered on page
- [ ] Pet info displays correctly (photo, name, age, breed, personality, hobbies)
- [ ] Dark/Light mode toggle works
- [ ] Theme persists after refresh
- [ ] Hover animation smooth (scale 1.05 + shadow)
- [ ] Responsive on mobile/tablet/desktop
- [ ] No console errors

## Risks
- None (static HTML, no backend)
- Low risk: image loading from external CDN

## Timeline
- Dev: 1-2 hours
- QC: 30 minutes
- Total: Same day delivery
