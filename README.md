# AI4Rad Lab Website

Official website of **AI4Rad Lab** at the Department of Radiology, Shanghai Sixth People's Hospital, Shanghai Jiao Tong University School of Medicine.

🔗 **Live site**: [https://ai4rad-ssph.github.io/](https://ai4rad-ssph.github.io/)

## Structure

```
.
├── index.html / index_ch.html     # Homepage (EN / CH)
├── team.html  / team_ch.html       # Team page (EN / CH), rendered from data/team.json
├── members/
│   └── index.html                  # Shared template for individual member pages (?id=<id>)
├── css/style.css                   # Shared styles, dark mode, SSPH branding
├── js/main.js                      # Theme toggle, scroll reveal, team renderer
├── data/
│   ├── team.json                   # Team roster (PI-maintained)
│   └── members/
│       ├── <id>.json               # One file per member — owned by that member
│       └── _template.json          # Copy this to start your own page
├── images/                         # Photos, logos, brand assets, paper figures
│   ├── brand/                      # SSPH logos and watermarks
│   └── members/                    # Member photos and figures
├── MEMBER_GUIDE.md                 # How members update their own info & page
└── DESIGN_SYSTEM.md                # Visual identity spec (colors, fonts, logos)
```

## How it works

- **Team page** (`team.html`) fetches `data/team.json` and renders every member via `js/main.js`.
  Add or move a member by editing `data/team.json` only.
- **Member pages** are all served by one template, `members/index.html`, addressed as
  `members/?id=<id>` (and `&lang=cn` for Chinese). It loads `data/members/<id>.json` and
  renders a full personal page in the SSPH style. See `data/members/ruipeng-zhang.json` for a
  complete example.
- A member's team card links to their personal page once their entry in `data/team.json`
  has `"page": true`.

## Updating team members (PI)

Edit `data/team.json` and add an entry under the appropriate category:
`leader`, `pi`, `postdoc`, `phd_engineering`, `phd_medical`, `master_engineering`,
`master_medical`, `alumni`.

For members without a real photo, set `avatar_type` to `"dicebear"` and provide
`avatar_seed` + `avatar_bg`; a cartoon avatar is generated via DiceBear.
Doctoral students (`role: "phd"`) are labelled **PhD & MD** automatically to reflect the
lab's medicine–engineering crossover; set an explicit `degree` to override.

## Members: update your own page

See **[MEMBER_GUIDE.md](MEMBER_GUIDE.md)**. In short: copy `data/members/_template.json` to
`data/members/<your-id>.json`, fill it in, drop your photo in `images/members/`, preview
locally, and open a Pull Request. The PI reviews and merges.

## Local preview

This is a static site:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

## Deployment

The site is deployed automatically by GitHub Pages from the **`main`** branch.
