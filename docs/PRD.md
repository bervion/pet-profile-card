# Pet Profile Card - PRD

## Project Overview
- **Project Name:** Pet Profile Card
- **Type:** Static Website (Workflow Test)
- **Core Functionality:** Display a single pet profile card with photo, info, and dark/light mode
- **Target Users:** Pet owners wanting to showcase their pets

## Tech Stack
- HTML + Tailwind CSS (static, CDN)
- No backend required

## Requirements

### 1. Card Layout
- Single card centered on page
- Max-width: 400px
- Rounded corners
- Card contains:
  - Pet photo (Unsplash cat image)
  - Pet name (prominent)
  - Age
  - Breed
  - Personality traits
  - Interests/hobbies

### 2. Visual Design
- Light mode: light background, dark text
- Dark mode: dark background, light text
- Clean, modern aesthetic

### 3. Interactions
- Hover effect: scale(1.05) + shadow-lg
- Transition duration: 0.3s
- Dark/Light mode toggle button
- Mode preference persisted to localStorage (key: `pet-profile-theme`)

### 4. Responsive
- Mobile: < 640px
- Tablet: 640px - 1024px
- Desktop: > 1024px
- Card scales appropriately on each breakpoint

## Out of Scope
- Multiple pets
- Backend/database
- User authentication
- Pet photo upload

## Success Criteria
1. Card displays correctly on all breakpoints
2. Dark/Light mode toggle works
3. Theme persists after page refresh
4. Hover animation smooth
5. No console errors
