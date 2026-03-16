# EventReach

**Find events you can reach in minutes.**

EventReach is a geography-first event discovery prototype for Vancouver. Instead of surfacing events by algorithm or interest graph, it organizes everything by physical proximity — showing you what's happening within your actual travel range right now.

→ **Live demo:** [chhyang17.github.io/EventReach](https://chhyang17.github.io/EventReach/)

---

## What it does

Set a location. Set a travel time. See what's on.

The map draws a real road-network isochrone (not a circle) showing exactly where you can get to by walking or biking in your chosen time budget. Events and places inside that boundary surface in the sidebar, sorted by distance.

When there's nothing on nearby, the app automatically shows parks, beaches, restaurants, and public art — so the map is always useful, not just when events are happening.

---

## Features

- **Isochrone-based range** — powered by OpenRouteService, falls back to circular approximation if unavailable
- **Multi-source events** — Ticketmaster API, UBC Career Centre & LibCal (live scraping), local seed events
- **Time filters** — Upcoming, 24 hrs, 3 days, This week, This month, Past 30 days
- **POI fallback** — parks, beaches, restaurants, community centres, public art auto-surface when events are sparse
- **Places layer** — optional toggle to explore amenities alongside events
- **Routing** — ORS turn-by-turn directions with Google Maps fallback
- **Onboarding modal** — first-time guidance for new visitors
- **Pagination** — event list loads 10 at a time, expandable

---

## Tech stack

| Layer | Technology |
|-------|-----------|
| Frontend | Vanilla JS + HTML, single-file, no build step |
| Map | Leaflet.js + OpenStreetMap tiles |
| Isochrone & routing | OpenRouteService v2 API |
| Events | Ticketmaster Discovery API |
| UBC events | Scraped via `allorigins.win` CORS proxy |
| Places data | Vancouver Open Data Portal (GeoJSON) |
| Geocoding | Nominatim (OpenStreetMap) |
| Hosting | GitHub Pages |

---

## Data sources

| Dataset | Source | Notes |
|---------|--------|-------|
| Events | Ticketmaster Discovery API | 50 events, Vancouver, sorted by date |
| UBC workshops | events.ubc.ca + LibCal | Live scrape, 24hr localStorage cache |
| Parks | Vancouver Open Data | ~300 records |
| Public Art | Vancouver Open Data | Artist, description, photo where available |
| Community Centres | Vancouver Open Data | Locations only, no schedule data |
| Restaurants | Vancouver Open Data (business licences) | Filtered to Restaurant type |
| Beaches | Vancouver Open Data | |
| Building permits | Vancouver Open Data | 2025+ issued permits |

---

## Known limitations

- `allorigins.win` is a public CORS proxy — UBC event scraping is unreliable when it's down. LocalStorage cache provides a 24hr fallback.
- ORS free tier: 2,000 requests/day, 40/min. Heavy use will hit rate limits.
- Community Centre event schedules are not available via any public API.
- No backend — all data is fetched client-side at page load.

---

## Design principles

**EventReach owns discovery. Navigation and ticketing belong to external tools.**

- The map is the product. The sidebar is secondary.
- Accessibility (travel time) sets the default range; interest can extend it.
- Content density matters: default to 6–12 nearby items to avoid choice overload.
- When events are sparse, surface places — the map should always be worth opening.

---

## Hypotheses being tested

1. Users have an unmet need for geography-scoped event discovery — separate from search or recommendation feeds.
2. Vancouver's public open data is dense enough to support a useful cold-start experience.
3. Users will travel further for high-interest events — the accessibility + interest interaction model works.

---

## Roadmap

- [ ] Replace `allorigins.win` with a lightweight backend proxy
- [ ] Event clustering for dense marker areas
- [ ] More event sources (community boards, Eventbrite public listings)
- [ ] Mobile-optimized layout
- [ ] User location persistence across sessions

---

## License

MIT
