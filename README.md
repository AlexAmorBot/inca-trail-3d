# Inca Trail 3D

**Live site:** https://alexamorbot.github.io/inca-trail-3d/

A GPS-accurate 3D walk of the classic Inca Trail, from the Km 82 trailhead at Piskacucho to Machu Picchu. The route, elevation, and stop photos come from a 2012 trek recorded on a Garmin handheld. The site is static HTML, CSS, and JavaScript. GitHub Pages serves it. There is no build step.

![Inca Trail 3D map](images/mapbox-image-1646x769.jpg)

## See it

- [Enter the 3D tour](https://alexamorbot.github.io/inca-trail-3d/3dtour/)
- [How the tour was made](https://alexamorbot.github.io/inca-trail-3d/how-tour-was-made/)
- [How to reserve a permit](https://alexamorbot.github.io/inca-trail-3d/how-to-reserve-inca-trail/)
- [Terms](https://alexamorbot.github.io/inca-trail-3d/terms/)
- [GPS route download (KMZ)](https://alexamorbot.github.io/inca-trail-3d/data/Inca_Trail_GPS_Route.kmz)

### Stop guides

- [Piskacucho (Km 82)](https://alexamorbot.github.io/inca-trail-3d/stops/piskacucho/)
- [Patallaqta](https://alexamorbot.github.io/inca-trail-3d/stops/patallaqta/)
- [Camp 1, Wayllabamba](https://alexamorbot.github.io/inca-trail-3d/stops/camp-1-wayllabamba/)
- [Dead Woman's Pass](https://alexamorbot.github.io/inca-trail-3d/stops/dead-womans-pass/)
- [Camp 2, Pakaymayu](https://alexamorbot.github.io/inca-trail-3d/stops/camp-2-pakaymayu/)
- [Runkurakay](https://alexamorbot.github.io/inca-trail-3d/stops/runkurakay/)
- [Runkurakay Pass](https://alexamorbot.github.io/inca-trail-3d/stops/runkurakay-pass/)
- [Sayacmarca](https://alexamorbot.github.io/inca-trail-3d/stops/sayacmarca/)
- [Phuyupatamarca](https://alexamorbot.github.io/inca-trail-3d/stops/phuyupatamarca/)
- [Wiñay Wayna](https://alexamorbot.github.io/inca-trail-3d/stops/winay-wayna/)
- [Sun Gate](https://alexamorbot.github.io/inca-trail-3d/stops/sun-gate/)
- [Machu Picchu](https://alexamorbot.github.io/inca-trail-3d/stops/machu-picchu/)
- [Huayna Picchu](https://alexamorbot.github.io/inca-trail-3d/stops/huayna-picchu/)

## What the tour does

The tour page is a Mapbox GL JS flyover. Scrolling moves the camera along the recorded track. Each stop opens photos, narration, and a link to a written guide. A second map keeps the whole route in view.

- Mapbox GL JS 2.7.0, loaded from the Mapbox CDN
- Turf.js for the route geometry
- Terrain style: `mapbox://styles/noufelghayati/cl3m1xwi6006z15ld00w5tmt8`
- Overview style: `mapbox://styles/mapbox/dark-v10`
- Stop narration in `3dtour/audio/`
- Stop photos in `3dtour/img/`

Mapbox and OpenStreetMap attribution stay visible on the map.

## Add the Mapbox token

The map will not draw until a public token is set. Open this file and paste the token between the quotes:

`3dtour/mapbox-token.js`

```javascript
window.MAPBOX_PUBLIC_TOKEN = "pk.your-public-token";
```

1. In the [Mapbox access-token dashboard](https://account.mapbox.com/access-tokens/), create a public token. It starts with `pk.`.
2. The token must be allowed to use the terrain style above. A token from the style owner's account can. A token from another account cannot, unless that style is public or has been copied into the new account.
3. Restrict the token URL to `https://alexamorbot.github.io/inca-trail-3d`. The tour page sends the full page URL as the referrer. Chrome's default sends only `https://alexamorbot.github.io`, and that origin gets a 403 against a path restriction.
4. Commit the file and push to `main`. GitHub Pages republishes from that branch.

Do not commit a secret token (`sk.`). A public `pk.` token is visible in the browser. The URL restriction is what stops it from being reused on another site.

If the token is missing, the tour page shows a short notice in place of the map. The rest of the site still works.

## Preview locally

```bash
python3 -m http.server 8765
```

Open http://127.0.0.1:8765/

Menu and canonical links use the live Pages URL, so those clicks leave the local server and open the published site.

## Layout

```
index.html                      Homepage
3dtour/index.html               3D tour
3dtour/mapbox-token.js          Public Mapbox token
3dtour/player.js                Camera and stop playback
3dtour/audio/                   Stop narration
3dtour/img/                     Stop photos
stops/                          Written guides
how-tour-was-made/              Build notes
how-to-reserve-inca-trail/      Permit guide
data/Inca_Trail_GPS_Route.kmz   GPS download
icons/                          Favicons
```

## Credits

Created by Alex Amor from a 2012 Inca Trail trek. GPS was captured on a Garmin handheld. Primary photos are from the trek team. Supplementary images are from Shutterstock. Tour interaction was built with Mapbox GL JS. Map data is © Mapbox © OpenStreetMap.

## Rights

Site content, photographs, narration, and the GPS track are all rights reserved unless a file says otherwise. Mapbox and OpenStreetMap data remain under their own terms.
