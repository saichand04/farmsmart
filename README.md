# FarmSmart

> Smart backyard garden planner — two raised beds, sixteen quadrants, seventeen pots, three fence runs for climbers, grouped into eight watering zones for an 8-relay Pi controller.

A personal IoT gardening project. The site (`farmsmart_garden_plan.html`) is a single-file dashboard that captures the full plan before the automation layer goes in: site map to scale, per-quadrant plant mapping, pot strategy, watering zones, and a live weather widget for the garden's location.

## Features

- **Top-down blueprint** rendered to exact scale (21 × 13 ft fabric, two 8 × 4 × 1 ft raised beds, 1 ft gap, fence on SW/SE/NE, house wall on NW, lawn on SE)
- **16 quadrant map** — each bed split into 2 rows × 4 cols of 2 × 2 ft squares (B1Q1–B1Q8, B2Q1–B2Q8) with plants assigned per quadrant
- **17 pots staged** across the NW and SE fabric strips — 3 Bottle Gourd (fence climbers), 4 Capsicum, 6 Green Chili, 2 Cucumber, 2 Zucchini — all movable
- **8 watering zones** mapped cleanly to an 8-channel relay bank on a Raspberry Pi 4
- **Live weather widget** — IP-geolocated via ipapi.co/ipwho.is, data from Open-Meteo, shows current + 6-hour forecast, aura gradient adjusts by sun phase (dawn/day/dusk/night) and intensity by UV + cloud cover
- **Disease watch** — lessons from last season's melon failure, with a cucurbit prevention playbook
- **Responsive dark dashboard** — Space Grotesk display, Inter body, JetBrains Mono for data labels

## Plants

| Plant | Location | Notes |
| --- | --- | --- |
| Okra | B1Q1–Q2 (4 plants) | Z1 · tall back screen |
| Brinjal | B1Q3, Q4, Q8 (3 plants) | Z1/Z2 · + marigold |
| Tomato | B2Q1–Q4 (4 caged) | Z3 · max-yield row |
| Roselle (Gongura) | B2Q5–Q6 (2 shrubs) | Z4 · leaves all season |
| Beetroot | B1Q6, B2Q8 (18 plants) | Z2/Z4 · dense 6" |
| Radish | B1Q7, B2Q8 (32 initial) | Z2/Z4 · succession every 2 wks |
| Bottle Gourd | 3 pots · SW/SE/NE fence | Z5 · 20 gal · climbs |
| Cucumber | 2 pots · SE fence | Z6 · 5 gal · climbs |
| Zucchini | 2 pots · top strip | Z6 · 10 gal · bush variety |
| Capsicum | 4 pots | Z7 · 5 gal · wall-banked |
| Green Chili | 6 pots | Z8 · 3 gal · scattered |

## Watering zones

| Zone | Targets | Schedule |
| --- | --- | --- |
| Z1 | Bed 1 NW row — Okra + Brinjal | Drip · 2×/wk deep |
| Z2 | Bed 1 SE row — Herbs + Beet + Radish + Brinjal | Drip · 4×/wk |
| Z3 | Bed 2 NW row — 4 Tomatoes | Drip · 2×/wk deep |
| Z4 | Bed 2 SE row — Roselle + Basil + Intercrop | Drip · 3×/wk |
| Z5 | Bottle Gourd pots | Emitters · daily |
| Z6 | Cucumber + Zucchini pots | Emitters · daily |
| Z7 | Capsicum pots | Emitters · every 2 days |
| Z8 | Green Chili pots | Emitters · every 2 days |

## View it

Open `farmsmart_garden_plan.html` in a browser. For the weather widget to load (IP-geolocation + Open-Meteo), serve over HTTP locally instead of `file://`:

```sh
python -m http.server
# then open http://localhost:8000/farmsmart_garden_plan.html
```

## Roadmap

Next up: the IoT/automation layer.

- Raspberry Pi 4 with 8-channel relay HAT driving 12V solenoid valves per zone
- 6+ capacitive soil-moisture sensors across beds and reference pots
- DHT22 (temp/humidity), BH1750 (light), Pi Camera v3 (time-lapse + leaf disease detection via TFLite/PlantVillage)
- Home Assistant dashboard
- MQTT + InfluxDB for logging
- Weather-API-aware skip logic (no watering if rain forecast)

## Stack

Pure HTML/CSS/JS, no build step. Fonts from Google Fonts. Weather from Open-Meteo (no API key). Geolocation from ipapi.co with ipwho.is fallback.

---

Personal garden project · Season 2026
