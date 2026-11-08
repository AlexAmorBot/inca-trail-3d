# Inca Trail 3D

Virtual 3D trek of the classic Inca Trail to Machu Picchu.

Published with GitHub Pages. The previous domain is retired.

## Map tiles

The tour reads a public Mapbox token from `3dtour/mapbox-token.js`.
Create a public token (`pk.`) that can read the custom style, restrict it to
`https://alexamorbot.github.io`, and set `window.MAPBOX_PUBLIC_TOKEN`.
Do not commit a secret token (`sk.`).

## Local preview

```bash
python3 -m http.server 8765
```

Open http://127.0.0.1:8765/
