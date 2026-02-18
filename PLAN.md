# LionTube — Build Plan

## Phase 1: Local MVP (1-2 sessions)
Get something working you can AirPlay today.

### 1a. Static HTML + YouTube IFrame API
- Single `index.html` with inline JS/CSS (no build step)
- YouTube IFrame Player API for embedding
- Player config: `autoplay: 0`, `rel: 0` (no related videos), `modestbranding: 1`
- Works in Safari → AirPlay to Apple TV immediately

### 1b. Video Management
- **Add single:** Paste a YouTube URL or ID + optional label → saved to localStorage
- **Add bulk:** Paste comma-separated or newline-separated YouTube URLs/IDs
- **Remove:** Delete button per video
- **Reorder:** Up/down arrows or drag
- Parse video ID from all YouTube URL formats (`youtube.com/watch?v=`, `youtu.be/`, `youtube.com/shorts/`, bare ID)
- All data in `localStorage` — no backend needed

### 1c. Two Modes
- **Parent mode** — Manage the list (add/remove/reorder), see the player
- **Kid mode** (`?mode=kid`) — Just titles + player, large tap targets, no management UI
- Mobile-friendly layout (you'll add URLs from your phone)

### 1d. Input Accessibility
- **Keyboard:** Arrow keys to navigate video list, Enter to play, Tab through controls
- **Touch:** Large tap targets, works on phone/iPad for AirPlay
- **Mouse:** Standard click navigation
- Focus states visible on all interactive elements

### 1e. Google Account / Ad-Free
- User must be able to sign into their Google/YouTube account within the app
- This is critical — YouTube Premium suppresses ads on embeds when logged in
- Approach: Use YouTube IFrame API with `origin` set correctly so the embedded player respects the browser's Google login session
- If that's insufficient, may need to open videos in a logged-in YouTube context (e.g., link out to `youtube.com/embed/VIDEO_ID` in a frame where cookies apply)

**Deliverable:** A single HTML file. Open locally, AirPlay from Safari. Done.

---

## Phase 2: Host It (when ready)
- Push to GitHub
- Deploy to Vercel/Netlify/GitHub Pages (all free, static site)
- Optional custom domain
- localStorage still works — data is per-browser, but that's fine for now
- If you later want cross-device sync, can add a simple JSON file backend or lightweight DB

---

## Phase 3: Extras (as needed)
- **Playlists/categories** — Group videos (e.g., "Bluey", "Science", "Music")
- **Parental PIN** — Simple 4-digit PIN to enter parent mode
- **YouTube playlist import** — Pull all videos from a playlist URL
- **Export/import** — Download your list as JSON, import on another device

---

## Phase 4: tvOS App (long term)
- **Start with:** PWA + AirPlay (works today, zero effort)
- **Later:** React Native for Apple TV (`react-native-tvos`) or TVML/TVMLKit
- Only worth building if AirPlay becomes annoying

---

## Ad-Free Playback Note

YouTube embeds still show ads unless:
1. You have **YouTube Premium** — ads suppressed when logged in
2. The video creator disabled ads

`modestbranding` only hides the logo, not ads. YouTube Premium is the cleanest path.
