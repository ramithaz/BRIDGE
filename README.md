# BRIDGE

**Find food, shelter, water, and help. No reading required.**

BRIDGE is a mobile-first web app that helps people with low literacy find nearby essentials using pictures, voice, and photos instead of text. It also helps users build reading skills gradually, just by using the app.

## The Problem

54% of U.S. adults read below a 6th-grade level. Most resource finders (shelter directories, transit apps, job boards) assume users can read fluently, type, and fill out forms. That locks out the people who need these services most, including:

- People experiencing homelessness (up 18% from 2023 to 2024)
- People in rural areas with limited access to services
- Non-native English speakers

When you can't read a sign, a map, or a website, finding a place to sleep, a restroom, or clean water becomes a daily struggle.

## What BRIDGE Does

- **Picture-first navigation.** Seven big buttons with: Shelter, Food + Water, Restrooms, Charging + WiFi, Bus, Jobs, Learn. Tap one and hear its name out loud.
- **Photo reading.** Snap a picture of a sign, flyer, bus schedule, or form. BRIDGE reads it aloud in plain language and tells you what to do next.
- **Nearby results.** The 3 closest options with a photo, walking time, open/closed status (green/red), and a big "Go" button.
- **Landmark directions.** Step-by-step walking directions with photos, arrows, and voice guidance.
- **Jobs.** Day labor, hiring events, and job centers explained by voice, including what to bring and how to get there.
- **Literacy layer.** Common words (BED, FOOD, OPEN, CLOSED) are highlighted and read aloud every time they appear. An optional Learn tab offers 1-minute word games built from words the user has already seen.
- **English and Spanish and French and Chinese** at launch.

## Tech Stack

- **Frontend:** React PWA (installable, offline via service worker)
- **Maps:** Leaflet + OpenStreetMap
- **Voice:** Web Speech API for speech-to-text and text-to-speech, LLM fallback for intent parsing
- **Photo reading:** Vision model for OCR and plain-language explanation
- **Data sources:** 211 / findhelp.org style listings, OpenStreetMap (toilets, drinking water, WiFi), public library locations, GTFS transit feeds, local shelter listings

## Getting Started

```bash
git clone https://github.com/<your-org>/bridge.git
cd bridge
npm install
cp .env.example .env   # add your LLM and vision API keys
npm run dev
```

Open `http://localhost:5173` on your phone (same network) or in a mobile emulator.

### Environment Variables

| Variable | Purpose |
|---|---|
| `LLM_API_KEY` | Intent parsing for voice search |
| `VISION_API_KEY` | Photo reading |
| `DEFAULT_CITY` | City used for mock data (default: San Francisco) |

## Project Structure

```
bridge/
├── public/            # icons, audio clips, manifest, service worker
├── src/
│   ├── components/    # CategoryGrid, ResultCard, MicButton, CameraButton
│   ├── screens/       # Home, Results, Directions, Learn
│   ├── services/      # voice, vision, locations, transit
│   ├── data/          # mock location data
│   └── i18n/          # English and Spanish strings + audio
└── README.md
```

## Team

Mridini Kulkarni & Ramitha Viswasekar

