# How to add screenshots & videos

Trainers and admins can drop real media into this repo. Pages already point at expected file names.

## Screenshots

1. Capture the screen at a normal desktop width (about 1280–1440 px).
2. Crop out personal data (patient names, phone numbers, Aadhaar, salary figures).
3. Save as PNG under `assets/screenshots/`.
4. On the help page, replace the placeholder block with:

```html
<figure class="media-frame">
  <img src="assets/screenshots/your-file.png" alt="Short description" />
  <figcaption>What the user should notice in this screen.</figcaption>
</figure>
```

### Screenshots in this site

Current screenshots were captured at 1440 × 900 from the demo organisation **caretest** (`cat`), using demo patients and staff only. Keep the same file name when you refresh one, and every page that uses it updates.

| Prefix | Module |
|--------|--------|
| `login.png`, `home-portal.png`, `core-*.png` | Core portal and organisation admin |
| `rakht-*.png` | RakhtSetu |
| `supply-*.png` | SupplySetu |
| `hr-*.png` | HRSetu |
| `care-*.png` | CareSetu |
| `security-*.png` / `.svg` | Security & compliance diagrams |

### Still needed

SwasthaSetu is not enabled for the demo organisation, so these pages still show placeholders:

| File | Subject |
|------|---------|
| `ohc-dashboard.png` | SwasthaSetu dashboard |
| `ohc-pre-employment.png` | Pre-employment exam |
| `ohc-periodic.png` | Periodic medical exam |
| `ohc-ambulance-check.png` | Ambulance daily checklist |
| `ohc-bmw.png` | Biomedical waste log |

## Videos

Use short clips (2–5 minutes) for flows that are hard to show in one image.

1. Upload to YouTube (unlisted) or host an `.mp4` under `assets/videos/`.
2. Replace the placeholder with either:

**YouTube (unlisted):**

```html
<figure class="video-frame">
  <iframe src="https://www.youtube.com/embed/VIDEO_ID" title="Training video" allowfullscreen></iframe>
  <figcaption>Title of the training clip.</figcaption>
</figure>
```

**Local file:**

```html
<figure class="video-frame">
  <video controls src="assets/videos/your-clip.mp4"></video>
  <figcaption>Title of the training clip.</figcaption>
</figure>
```

<figure class="video-frame">
  <p><em>Video placeholder — “First day: sign in and open your module” (2–3 min)</em></p>
  <figcaption>Suggested: <code>assets/videos/first-day-login.mp4</code> or YouTube unlisted embed</figcaption>
</figure>

## Privacy checklist before publish

- No real patient / donor identifiers
- No salary or bank details
- No SMTP secrets or API keys
- Prefer demo organisation data (`caretest`, training donors, etc.)
