# AI4Rad Lab Website

Official website of **AI4Rad Lab** at the Department of Radiology, Shanghai Sixth People's Hospital, Shanghai Jiao Tong University School of Medicine.

🔗 **Live site**: [https://ai4rad-ssph.github.io/](https://ai4rad-ssph.github.io/)

## Structure

```
.
├── index.html          # English homepage
├── index_ch.html       # Chinese homepage
├── team.html           # English team page
├── team_ch.html        # Chinese team page
├── css/
│   └── style.css       # Shared styles + dark mode
├── js/
│   └── main.js         # Theme toggle, scroll reveal, team renderer
├── data/
│   └── team.json       # Structured team member data
├── images/             # Photos and project figures
└── members/            # Individual member pages (future)
```

## How to update team members

Edit `data/team.json` and add a new entry under the appropriate category:

- `leader`
- `pi`
- `postdoc`
- `phd_engineering`
- `phd_medical`
- `master_engineering`
- `master_medical`
- `alumni`

For members without a real photo, set `avatar_type` to `"dicebear"` and provide `avatar_seed` + `avatar_bg`. A cartoon avatar will be generated automatically via DiceBear.

## Local preview

This is a static website. You can serve it locally with any static server, for example:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000`.

## Deployment

The site is automatically deployed by GitHub Pages when changes are pushed to the `master` branch.
