# Bad Manager Simulator v0.2

A satirical, static website from **Subversive Management**. One playable campaign, *The Promotion Trap*, contains the original five workplace crises. Four additional scenario cards are intentionally disabled.

## Publish with GitHub Pages

1. Create a repository, for example `bad-manager-simulator`.
2. Upload **the contents of this folder** to the repository root (not the folder itself).
3. In repository **Settings → Pages**, select **Deploy from a branch**, `main`, `/ (root)`.
4. Wait for GitHub Pages to publish. For a custom subdomain, enter it in Pages settings and configure its CNAME record with your DNS provider.
5. Enable HTTPS after DNS and certificate provisioning finish.

## Test locally

Because the site loads JSON with `fetch()`, opening `index.html` directly with `file://` will not work reliably. Run a tiny local server from the folder:

```bash
python3 -m http.server 8000
```

Visit http://localhost:8000 . (Alternatively use VS Code's Live Server extension.) No installation, backend or build step is required for GitHub Pages.

## Where things live

- `index.html`: page structure, splash screen, game screen and results screen.
- `style.css`: colours, layout, responsive design.
- `game.js`: game engine, scenario loading, decisions, scoring, saving and sharing.
- `data/campaigns.json`: splash-screen card catalogue.
- `data/promotion.json`: **all five existing scenarios**, character details, choices and outcomes.
- `assets/*.svg`: original illustrative graphics inspired by the supplied office aesthetic.

## Add a campaign later

Create `data/new-campaign.json` using the structure of `promotion.json`, then add an entry in `data/campaigns.json` with `status: "available"`, `file: "new-campaign.json"`, and an `image` path. The engine automatically loads the new campaign. Each option's `delta` is ordered as executive visibility, productivity, morale, accountability. Keep scenario IDs unique and use the same structure.

## Save data

The game stores progress only in the player's browser (`localStorage`, key `bms-save-v2`). No data is sent to a server. There is no analytics or player account system.

## Notes

The character names are currently shown as labelled initials, not bespoke portraits. Character portraits can be added later without changing the scenario format. Fonts are loaded from Google Fonts, with system fallbacks.
