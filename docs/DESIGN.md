# Pet Profile Card — Design Specification

## 1. Project Overview

- **Project:** Pet Profile Card
- **Type:** Single-page static website
- **Core Functionality:** Display a profile card for a pet cat with dark/light mode toggle
- **Target Users:** Pet owners showcasing their cats

---

## 2. Screen Inventory

### 2.1 Main Screen (Single Page)

**Screen ID:** `SCR-001` — Pet Profile Card

**Layout Structure:**
```
┌─────────────────────────────────────────┐
│           Page Container                │
│  ┌───────────────────────────────────┐  │
│  │      Dark/Light Toggle (top-right) │ │
│  └───────────────────────────────────┘  │
│                                         │
│         ┌───────────────────┐           │
│         │                   │           │
│         │    Cat Image     │           │
│         │   (Unsplash)     │           │
│         │                   │           │
│         ├───────────────────┤           │
│         │   Pet Name        │           │
│         │   Breed           │           │
│         │   Age Badge       │           │
│         ├───────────────────┤           │
│         │   Personality     │           │
│         │   (Tags)          │           │
│         ├───────────────────┤           │
│         │   Interests       │           │
│         │   (Icons + Text)  │           │
│         └───────────────────┘           │
│                                         │
└─────────────────────────────────────────┘
```

**Responsive Breakpoints:**
- Mobile: < 640px (card width: 90vw, max 360px)
- Tablet: 640px - 1024px (card width: 400px)
- Desktop: > 1024px (card width: 440px)

---

## 3. Components

### 3.1 Theme Toggle

**Component ID:** `COMP-theme-toggle`

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| icon-sun | string | ☀️ | Icon for light mode |
| icon-moon | string | 🌙 | Icon for dark mode |

**States:**
- Light mode active: Sun icon displayed
- Dark mode active: Moon icon displayed

**Interactions:**
- Click: Toggle between light/dark mode
- Preference saved to localStorage key: `pet-profile-theme`

---

### 3.2 Profile Card

**Component ID:** `COMP-profile-card`

| Prop | Type | Description |
|------|------|-------------|
| imageUrl | string | Unsplash cat image URL |
| petName | string | Name of the cat |
| breed | string | Cat breed |
| age | number | Age in years |
| personality | string[] | Array of personality traits |
| interests | string[] | Array of interests/hobbies |

**States:**
- Default: Normal display
- Hover: Scale 1.02 + shadow increase
- Loading: Skeleton placeholder (optional)

**Interactions:**
- Hover: `transform: scale(1.02)`, shadow expands from `shadow-lg` to `shadow-2xl`
- Transition: 300ms ease-out

---

### 3.3 Age Badge

**Component ID:** `COMP-age-badge`

| Prop | Type | Description |
|------|------|-------------|
| age | number | Age in years |

**Visual:**
- Rounded pill shape
- Primary color background
- White text

---

### 3.4 Personality Tag

**Component ID:** `COMP-personality-tag`

| Prop | Type | Description |
|------|------|-------------|
| trait | string | Personality trait text |

**Visual:**
- Small rounded pill
- Secondary/subtle background
- Muted text color

---

### 3.5 Interest Item

**Component ID:** `COMP-interest-item`

| Prop | Type | Description |
|------|------|-------------|
| icon | string | Emoji icon |
| label | string | Interest label |

**Visual:**
- Flex row: icon + text
- Small gap between icon and text

---

## 4. Design Tokens

### 4.1 Color Palette

| Token | Light Mode | Dark Mode | Usage |
|-------|------------|-----------|-------|
| `--bg-primary` | `#f8fafc` | `#0f172a` | Page background |
| `--bg-card` | `#ffffff` | `#1e293b` | Card background |
| `--text-primary` | `#0f172a` | `#f1f5f9` | Headings, name |
| `--text-secondary` | `#475569` | `#94a3b8` | Body text, labels |
| `--accent-primary` | `#6366f1` | `#818cf8` | Buttons, badges |
| `--accent-secondary` | `#e0e7ff` | `#312e81` | Tags, subtle elements |
| `--border` | `#e2e8f0` | `#334155` | Card border |

### 4.2 Typography

| Token | Font | Size | Weight |
|-------|------|------|--------|
| `--font-display` | System UI / sans-serif | 28px | 700 (bold) |
| `--font-body` | System UI / sans-serif | 16px | 400 (regular) |
| `--font-small` | System UI / sans-serif | 14px | 500 (medium) |
| `--font-micro` | System UI / sans-serif | 12px | 500 (medium) |

### 4.3 Spacing

| Token | Value | Usage |
|-------|-------|-------|
| `--space-xs` | 4px | Tight spacing |
| `--space-sm` | 8px | Small gaps |
| `--space-md` | 16px | Standard padding |
| `--space-lg` | 24px | Section spacing |
| `--space-xl` | 32px | Large gaps |

### 4.4 Border Radius

| Token | Value | Usage |
|-------|-------|-------|
| `--radius-sm` | 8px | Tags, badges |
| `--radius-md` | 12px | Card |
| `--radius-lg` | 16px | Card images |
| `--radius-full` | 9999px | Pill shapes |

### 4.5 Shadows

| Token | Light Mode | Dark Mode |
|-------|------------|-----------|
| `--shadow-card` | `0 4px 6px -1px rgb(0 0 0 / 0.1)` | `0 4px 6px -1px rgb(0 0 0 / 0.3)` |
| `--shadow-hover` | `0 20px 25px -5px rgb(0 0 0 / 0.1)` | `0 20px 25px -5px rgb(0 0 0 / 0.4)` |

---

## 5. Data (Hardcoded in HTML)

```javascript
const petData = {
  name: "Mochi",
  breed: "Scottish Fold",
  age: 3,
  imageUrl: "https://images.unsplash.com/photo-1514888286974-6c03e2ca1dba?w=400&h=400&fit=crop",
  personality: ["Gentle", "Curious", "Playful", "Cuddly"],
  interests: ["Napping ☀️", "Chasing Laser 🧶", "Window Watching 🪟", "Treats 🍖"]
};
```

---

## 6. Acceptance Criteria

1. ✅ Card displays pet image from Unsplash
2. ✅ Pet name, breed, age displayed clearly
3. ✅ 4 personality tags shown
4. ✅ 4 interests with icons displayed
5. ✅ Dark/light mode toggle works
6. ✅ Theme preference persists in localStorage
7. ✅ Card scales up (1.02) + shadow on hover
8. ✅ Responsive: card adapts to mobile/tablet/desktop
9. ✅ Smooth transitions (300ms)
10. ✅ No console errors

---

## 7. File Structure

```
pet-profile-card/
├── docs/
│   └── DESIGN.md          ← This file
└── dev/
    └── index.html         ← Implementation file
```

---

## 8. Dependencies

- **Tailwind CSS:** CDN (`https://cdn.tailwindcss.com`)
- **Google Fonts:** Optional (system fonts preferred for speed)
- **Images:** Unsplash cat placeholder

---

*Design created by: Ton Ngo Khong (Design)*
*Last updated: 2026-03-01*
