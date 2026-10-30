# VB Price Finder

A static, mobile-friendly GitHub Pages site that finds nearby bottle shops with permission-based GPS, shows mapped opening-hours text, supports 6/24/30-pack filters, directions, and optionally compares manually verified VB prices.

## Publish to GitHub Pages
1. On GitHub create a new **public** repository called `vb-price-finder`.
2. Select **Add file → Upload files** and upload `index.html`, `prices.json`, and `manifest.webmanifest` from this ZIP (not the ZIP itself). Commit the files.
3. Open repository **Settings → Pages**. Under **Build and deployment**, select **Deploy from a branch**, branch **main**, folder **/(root)**, then **Save**.
4. Wait a few minutes and open `https://YOUR-USERNAME.github.io/vb-price-finder/`.
5. On your phone tap **Use my location**, then grant location permission. HTTPS is required for GPS and is provided by GitHub Pages.

## Price data limitations
GitHub Pages cannot scrape live specials from major bottle shop retailers on its own. The site deliberately displays **Price unknown** unless a verified price is supplied in `prices.json`. Nearby store data comes from OpenStreetMap via the public Overpass API, which can be slow, incomplete or temporarily unavailable. Opening hours are raw OpenStreetMap tags, **not** reliable live open/closed status. Distance is straight-line, not driving distance. Retailer search links help check current specials.

To add a verified price, replace the `[]` in `prices.json` with entries such as:

```json
[
  {
    "store_osm_id": "node/123456789",
    "pack_size": 24,
    "price_aud": 59.99,
    "verified_on": "2026-10-30",
    "source_url": "https://example.com/actual-product-or-offer"
  }
]
```

**These are placeholder values only.** Use a real OpenStreetMap store ID from the Overpass API and a genuine retailer offer URL. Never publish example prices as actual specials. Refresh prices regularly and check expiry dates before relying on them.

## Further improvements
To show genuine *automatic* specials, integrate a legitimate retailer feed/API or a permitted server-side data collector, then publish a validated JSON price feed. GitHub Pages itself is static and cannot securely store retailer API secrets. Store hours can be parsed with a dedicated opening-hours library in a later version.
