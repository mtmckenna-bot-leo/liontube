# LionTube 📺

A distraction-free YouTube player for kids. No autoplay, no thumbnails, no recommendations, no ads (via Google account login). AirPlay to Apple TV, eventually a native tvOS app.

## The Problem

You want your kids to watch specific YouTube videos without:
- Autoplay dragging them into rabbit holes
- Thumbnails/recommendations distracting them
- Ads interrupting the experience
- Any YouTube UI beyond the video itself

## The Solution

A simple web app with:
1. **A curated URL list** — You add YouTube URLs, each gets a plain text label
2. **A clean player** — Kids see a list of titles, tap one, it plays. Nothing else.
3. **No distractions** — No thumbnails, no suggestions, no autoplay, no sidebar
4. **Ad-free** — Embedded player via your logged-in Google account (or YouTube Premium)
5. **AirPlay support** — Works in Safari, cast to Apple TV

## Tech Stack

- **Frontend:** React (or even plain HTML/JS to start) + YouTube IFrame API
- **Storage v1:** localStorage (works immediately, no backend)
- **Storage v2:** Supabase (Postgres + auth, free tier, shareable across devices)
- **Hosting:** Vercel or Netlify (free, instant deploys)
- **Future:** tvOS app via TVML/TVMLKit or React Native for Apple TV
