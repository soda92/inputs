# inputs

A single-file demo of mobile HTML input `type` / `inputmode` / `enterkeyhint`
combinations. Open it on a phone and tap each field to see which keyboard or
picker appears.

Bilingual (English / 中文) with automatic browser-language detection and a manual
`EN` / `中文` toggle. The choice is remembered in `localStorage`.

## Files

- `index.html` — self-contained page (no build step, no dependencies).

## Internationalization

- On first load the page reads `navigator.languages` / `navigator.language` and
  picks `zh` when it starts with `zh`, otherwise `en`.
- The header toggle overrides detection and is persisted under the
  `inputs-demo-lang` key in `localStorage`.
- All UI strings live in the `I18N` object at the top of the `<script>` block.
  To add a language, copy the `en` dictionary, translate the values, and add a
  toggle button with a matching `data-lang` value.

## Preview locally

Open the file directly, or serve it:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy to GitHub Pages

Because the entry point is `index.html` at the repo root:

1. Push this repo to GitHub.
2. Repo **Settings → Pages**.
3. **Source:** *Deploy from a branch*.
4. **Branch:** `main` (or your default) and folder `/ (root)`.
5. Save, wait a moment, then open `https://<user>.github.io/<repo>/` on your phone.

Any other static host (Netlify, Cloudflare Pages, Vercel, S3) works the same way —
just serve the repo root.

## What's covered

1. Numeric numpad — the `type="text" inputmode="numeric" pattern="[0-9]*"` combo
2. `inputmode` values — `none`, `text`, `tel`, `search`, `email`, `url`, `numeric`, `decimal`
3. `type` values that change the keyboard — `email`, `tel`, `url`, `search`, `number`, `password`
4. Native pickers — `date`, `time`, `datetime-local`, `month`, `week`, `color`, `range`, `file`
5. `enterkeyhint` — `done`, `go`, `next`, `previous`, `search`, `send`
6. Cheat sheet + why to avoid `type="number"` for IDs/OTP

> Keyboard layouts vary by OS and browser, so verify on the actual devices you care about.
