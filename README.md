# YouTube
### Video Recommendation Window — Case Study
**UI/UX Design & Frontend Development Assignment | 2026**

--- 

## 1. Project Overview

TechTube is a frontend case study project built to analyse and replicate the behaviour of a YouTube-style video recommendation sidebar. The project focuses specifically on how a recommendation window is structured, rendered, and interacted with — making it an ideal subject for studying UI patterns, content discovery mechanics, and web component design.

This README documents every aspect of the project: its purpose, structure, design decisions, and how the recommendation window works — serving as a complete academic reference for the case study assignment.

---

## 2. Objectives

- Study the visual and functional anatomy of a video recommendation panel
- Replicate YouTube's sidebar recommendation UI using pure HTML and CSS
- Understand how thumbnail images, metadata, and interaction states are composed
- Analyse the role of recommendation windows in user engagement and watch-time
- Document design decisions and compare against the reference platform (YouTube)

---

## 3. Project Structure

The project is a static two-file web application:

| File | Purpose |
|------|---------|
| `index.html` | Main markup — navbar, category bar, video player, recommendation panel, footer |
| `style.css` | All visual styling — layout, dark theme, component-specific rules |

---

## 4. Page Layout

The page is divided into four primary zones:

| Zone | HTML Element | Description |
|------|-------------|-------------|
| Navbar | `<nav class="navbar">` | Logo, search bar, upload button, user avatar |
| Category Bar | `<div class="categories">` | Horizontal pill buttons for filtering by topic |
| Main Content | `<div class="main-content">` | Two-column grid: video player (left) + recommendations (right) |
| Footer | `<footer>` | Copyright line |

---

## 5. Recommendation Window — Deep Dive

The recommendation panel is the **core focus** of this case study. It sits to the right of the video player and lists related videos in a vertical stack, closely mirroring YouTube's sidebar.

### 5.1 Structure of a Single Recommendation Card

Each recommended video is represented by a `.rec-video` card containing three sub-components:

| Sub-component | CSS Class | Role |
|--------------|-----------|------|
| Thumbnail | `.rec-thumb` | Shows the YouTube-sourced preview image with a duration badge overlay |
| Metadata | `.rec-info` | Displays title (`h4`), channel name (`p`), and view count (`p`) |
| Menu Button | `.rec-menu` | A three-dot (⋮) button that appears on hover for actions |

### 5.2 Thumbnail Source

Thumbnails are fetched directly from YouTube's public image CDN — no API key required:

```
https://img.youtube.com/vi/{VIDEO_ID}/mqdefault.jpg
```

The `mqdefault` quality tier delivers a **320×180 px** image, suitable for sidebar display. The video ID is extracted from each YouTube URL and embedded in the `src` attribute of an `<img>` tag inside `.rec-thumb`.

### 5.3 Duration Badge

A `<span class="duration">` element is absolutely positioned at the **bottom-right corner** of the thumbnail, styled with a semi-transparent dark background (`rgba(0,0,0,0.85)`) and white text — identical to YouTube's native duration chip.

### 5.4 Hover Interaction

Two hover states are implemented:

- **Card hover** (`.rec-video:hover`): background shifts from transparent to `#272727`
- **Menu button hover** (`.rec-menu:hover`): the three-dot button fades in (`opacity: 0 → 1`) and its background becomes `#3d3d3d`

These micro-interactions are driven entirely by **CSS transitions** — zero JavaScript required.

### 5.5 Typography & Metadata Layout

Inside `.rec-info`, content is stacked vertically using flexbox (`flex-direction: column`, `gap: 4px`):

| Element | Font Size | Color | Purpose |
|---------|-----------|-------|---------|
| `h4` (title) | 13px | `#f1f1f1` | Video title, clamped to 2 lines with `-webkit-line-clamp` |
| `p` (channel) | 12px | `#aaaaaa` | Channel name |
| `p` (stats) | 12px | `#aaaaaa` | View count and upload date |

### 5.6 Responsive Considerations

The thumbnail has a fixed width of **168px** and height of **94px**, maintaining the standard 16:9 aspect ratio. The `.rec-info` section uses `flex: 1` to fill remaining horizontal space.

---

## 6. Comparison with YouTube Sidebar

| Feature | YouTube (Reference) | TechTube (This Project) |
|---------|--------------------|-----------------------|
| Thumbnail source | YouTube CDN (auto-generated) | YouTube CDN — same URL pattern |
| Duration badge | Bottom-right overlay on thumb | Identical positioning and style |
| Card layout | Horizontal: thumb + metadata | Identical horizontal layout |
| Hover highlight | Subtle dark bg on hover | CSS transition to `#272727` |
| Three-dot menu | Appears on hover | Fades in on hover via opacity |
| Title clamp | 2 lines max | 2 lines via `-webkit-line-clamp` |
| Dark theme | Default on dark mode | Always-on dark (`#0f0f0f` bg) |
| Dynamic data | Fetched from YouTube API | Static HTML (case study scope) |

---

## 7. Key Learnings from the Case Study

1. **Thumbnail APIs**: YouTube exposes a predictable, keyless CDN URL for video thumbnails — a practical pattern used widely in frontend tooling.
2. **CSS-only interactivity**: Hover states, opacity transitions, and layout shifts can be achieved without any JavaScript.
3. **Absolute positioning for overlays**: Duration badges use `position: absolute` inside a `position: relative` parent — a foundational CSS pattern for media cards.
4. **Flexbox for card anatomy**: The horizontal card (thumb + info) is a flex row; the metadata column inside is a flex column. Nesting flex containers is the standard approach.
5. **Text overflow management**: `-webkit-line-clamp` is the modern standard for multi-line truncation in card titles.
6. **Dark-mode design**: Working in a dark palette teaches contrast management and the importance of muted accent colours.

---

## 8. How to Run

1. Clone or download the project folder
2. Ensure `index.html` and `style.css` are in the same directory
3. Open `index.html` in any modern browser (Chrome, Firefox, Edge, Safari)
4. No build step, no dependencies, no server required

> The embedded YouTube player and recommendation thumbnails require an active internet connection.

---

## 9. Technologies Used

| Technology | Usage |
|-----------|-------|
| HTML5 | Semantic markup, iframe embed, anchor tags |
| CSS3 | Flexbox layout, CSS transitions, absolute positioning, dark theme |
| YouTube oEmbed CDN | Thumbnail images via `img.youtube.com` |
| YouTube IFrame API | Embedded video player via `youtube.com/embed` |

---

## 10. Potential Future Improvements

- Fetch real video data from the **YouTube Data API v3** to make recommendations dynamic
- Add a click handler so selecting a recommendation loads the video in the player
- Implement filter/search within the recommendations panel
- Add **skeleton loading states** to simulate real async data fetching
- Make the layout fully responsive for mobile viewports

---

*YouTube Case Study | UI/UX & Frontend Development | 2026*
