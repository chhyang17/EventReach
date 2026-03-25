# EventReach

**Find events you can reach in minutes.**

EventReach is a geography-first event discovery prototype for Vancouver. Instead of surfacing events by algorithm or interest graph, it organizes everything by physical proximity — showing you what's happening within your actual travel range right now.

→ **Live demo:** [yangchh17.github.io/EventReach](https://yangchh17.github.io/EventReach/)

---

## What it does

Set a location. Set a travel time. See what's on.

The map draws a real road-network isochrone showing exactly where you can get to by walking or biking within your chosen time budget. Events inside that boundary appear in the sidebar, sorted by distance.

---

## Current status — v0.1 (prototype)

This is an early prototype being used to validate core product hypotheses. The focus is on the core discovery loop, not feature completeness.

**Working:**
- Map with isochrone-based range (OpenRouteService, fallback to circle)
- Event filters by source: Ticketmaster, UBC workshops, Local
- Time filters: Upcoming, 24 hrs, 3 days, This week, This month, Past 30 days
- Places layer: Parks, Public Art, Community Centres, Building Permits
- ORS turn-by-turn routing with Google Maps fallback
- Onboarding modal for first-time visitors
- CartoDB map tiles (compatible with GitHub Pages)

**Known bugs — being tracked in Issues:**
- Ticketmaster events not loading
- UBC workshop data not loading
- Isochrone does not account for elevation (cycling times inaccurate in hilly areas e.g. Burnaby Mountain)
- UBC event scraping unreliable when allorigins.win proxy is down
- Sidebar too cluttered for new users (Search building, Places layer, Show farther events)

---

## Tech stack

| Layer | Technology |
|-------|------------|
| Frontend | Vanilla JS + HTML, single-file, no build step |
| Map | Leaflet.js + CartoDB Voyager tiles |
| Isochrone & routing | OpenRouteService v2 API |
| Events | Ticketmaster Discovery API |
| UBC events | Scraped via `allorigins.win` CORS proxy |
| Places data | Vancouver Open Data Portal (GeoJSON) |
| Geocoding | Nominatim (OpenStreetMap) |
| Hosting | GitHub Pages |

---

## Hypotheses being tested

1. Users have an unmet need for geography-scoped event discovery — separate from search or recommendation feeds
2. Vancouver's public open data is dense enough to support a useful cold-start experience
3. Users will travel further for high-interest events

---

## Design principles

**EventReach owns discovery. Navigation and ticketing belong to external tools.**

- The map is the product. The sidebar is secondary.
- Accessibility (travel time) sets the default range; interest can extend it.
- When events are sparse, surface nearby places — the map should always be worth opening.

---

## Roadmap

See [GitHub Issues](https://github.com/yangchh17/EventReach/issues) for the full backlog.

---

## License

MIT
