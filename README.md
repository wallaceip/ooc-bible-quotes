# Out-of-Context Bible Quotes

A mobile app that serves up Bible verses that sound funny, weird, or absurd when taken out of context. Swipe through them like a social feed.

Built with React Native (Expo SDK 57) and TypeScript. Runs on iOS, Android, and web.

## Features

- **Swipe feed** — Full-screen, paginated cards. Swipe vertically to browse quotes. Pull down to shuffle.
- **Bilingual** — Toggle between English (NIV) and Chinese (CUVS) on the fly. All quotes include both translations.
- **Tag filtering** — Quotes are tagged (`#funny`, `#weird`, `#dark`, etc.) and filterable through a bottom-sheet modal.
- **Favorites** — Double-tap or tap the heart icon to save quotes. Persisted locally via AsyncStorage.
- **History** — Tracks recently viewed quotes with relative timestamps. Clearable.
- **Notifications** — Schedule daily or weekly push notifications with a random quote. Configurable time and frequency.
- **Read in context** — Tap the book icon to open the full passage on Bible Gateway (NIV or CUVS based on language).
- **Share** — Native share sheet for any quote.
- **Dark / Light mode** — Manual toggle, persisted across sessions.
- **Glassmorphism UI** — Cards and tab bar use `expo-blur` / `expo-glass-effect` with blur tints.
- **Animations** — Heart bounce (Reanimated spring), big heart overlay on double-tap, slide-in header controls.

## Tech Stack

| Layer | Technology |
|---|---|
| Framework | Expo (SDK 57), Expo Router (file-based routing) |
| Language | TypeScript |
| UI | React Native, Reanimated, expo-blur, expo-glass-effect |
| Storage | AsyncStorage |
| Notifications | expo-notifications |
| Data | Static JSON (~100 curated quotes), fetched from GitHub raw on startup with local fallback |

## Project Structure

```
app/
  _layout.tsx          # Root stack (tabs + modal)
  (tabs)/
    _layout.tsx        # Tab bar config (Home, Favorites, History, Options)
    index.tsx          # Main swipe feed
    favorites.tsx      # Saved quotes list
    history.tsx        # Recently viewed quotes
    options.tsx        # Language, theme, notification settings
components/
  animated-heart.tsx   # Heart bounce + big heart overlay
  filter-modal.tsx     # Tag filter bottom sheet
  glass-card.tsx       # Glassmorphism card wrapper
  header-controls.tsx  # Collapsible menu (language, theme, filter)
  shuffle-toast.tsx    # Refresh/filter toast notification
  tag-chip.tsx         # Selectable tag pill
  tag-filter-modal.tsx # Multi-tag filter modal
services/
  quotes-service.ts    # Fetch, cache, shuffle, Bible Gateway URL builder
data/
  quotes.json          # Curated quote dataset (EN + ZH, tagged)
constants/
  quotes.ts            # Local fallback quote data
  theme.ts             # Color and font definitions
```

## Getting Started

```bash
# Install dependencies
npm install

# Start the Expo dev server
npx expo start
```

Scan the QR code with Expo Go, or press `a` for Android / `i` for iOS / `w` for web.

## Adding Quotes

Edit `data/quotes.json`. Each entry:

```json
{
  "id": "42",
  "text": "She lusted after her lovers, whose genitals were like those of donkeys.",
  "verse": "Ezekiel 23:20",
  "text_zh": "貪戀情人身壯精足，如驢如馬。",
  "verse_zh": "以西結書 23:20",
  "tags": ["#dark", "#weird"]
}
```

Push to `main` — the app fetches from GitHub raw on startup.

## License

MIT
