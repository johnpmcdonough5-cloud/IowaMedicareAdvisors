# Iowa Medicare Advisors — Website

Simple static site: home, about, plans, and contact pages. No build step required.

## Contact details

All taken from the previous site (iowamedicareadvisors.com) so formatting matches:

- Phone: `319-238-4440` — displayed with hyphens, matching the old site. Links use `tel:+13192384440`.
- Email: `jack@aihealthinsure.com`
- Address: 955 N Frederick Ave, Oelwein, IA 50662
- Office hours in `contact.html`: Mon–Fri 9:00–5:00 — **unverified**, these were not on the old site. Edit if wrong.

The phone and address also appear in the `InsuranceAgency` structured-data block in the `<head>` of `index.html`. If either changes, update it there too so search engines stay in sync.

## Host on GitHub Pages

1. Create a new GitHub repository (public) and push this folder to it:

   ```bash
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```

2. On GitHub, go to the repo's **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to `Deploy from a branch`, branch `main`, folder `/ (root)`.
4. Save. Your site will publish at `https://<your-username>.github.io/<repo-name>/`.

To use a custom domain, add a `CNAME` file at the repo root with your domain, and point your domain's DNS to GitHub Pages per [GitHub's custom domain docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site).

## Structure

```
index.html      Home (+ InsuranceAgency structured data)
about.html      About the office
plans.html      Medicare Advantage overview + enrollment periods
contact.html    Contact info + form (opens visitor's email client)
css/style.css   All styling
js/main.js      Mobile nav toggle
images/         Logo assets (blue for light bg, white for dark bg)
images/source/  Original full-size logo files
images/team/    Team photos carried over from the old site
```

## Team photos

Carried over from the old WordPress site and re-encoded — the originals totalled ~3.6 MB, which is slow on rural connections. They are now 376 KB in total (group photo 1000×1000, headshots 440×440, JPEG q84).

Name-to-photo mapping was taken from the old site's carousel order:

| New file | Old file | Name |
|---|---|---|
| `team-kelli.jpg` | `11.png` | Kelli |
| `team-nancy.jpg` | `10.png` | Nancy |
| `team-mckenzie.jpg` | `6.png` | McKenzie |
| `team-karissa.jpg` | `9.png` | Karissa |
| `team-shawn.jpg` | `7-1.png` | Shawn |
| `team-hannah.jpg` | `8.png` | Hannah |

**Please spot-check these against the faces** — the old site paired them by position in a carousel rather than by filename, so the mapping is inferred.

Not carried over: the old cyan logo (superseded), a stock photo, the decorative wave background, the carrier logos (BCBS/Aetna/UnitedHealthcare/Humana), and the *Medicare & You 2024* handbook cover (outdated edition).

## Accessibility notes

This site is built for an older audience, so a few things are deliberate — please keep them if you edit:

- **20px base font size** with a 1.7 line height. Do not shrink this.
- **Colors meet WCAG AAA contrast**: the navy (`#03229e`) is 12.2:1 on white and the red (`#a4231c`) is 7.4:1 — both well above the 4.5:1 minimum.
- **Red is reserved for actions only** (Call / Get Free Help / Contact buttons). Everything structural stays navy, so the red always means "click this."
- **Skip-to-content link** and **4px focus outlines** for keyboard users.
- **`prefers-reduced-motion`** is respected for visitors who get motion sickness.
- Buttons and links are sized for imprecise taps (44px+ targets, full-width on mobile).
