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

### Suggested filenames

| File | Subject |
|------|---------|
| `home-portal.png` | Portal after login |
| `core-users.png` | Users list |
| `rakht-donors.png` | Donor list / register |
| `rakht-camp.png` | Camp day screen |
| `supply-stock.png` | Stock list |
| `supply-po.png` | Purchase order |
| `hr-employees.png` | Employee list |
| `hr-attendance.png` | Attendance |
| `care-opd.png` | OPD visit |
| `care-appointments.png` | Appointment calendar |

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
