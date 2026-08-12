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

## Team

Four advisors, each with a direct number and a call button. The list appears on both the homepage and the About page — **edit both** when it changes.

| File | Name | Direct number |
|---|---|---|
| `team-kelli.jpg` | Kelli | 563-278-2526 |
| `team-nancy.jpg` | Nancy | 563-412-6693 |
| `team-mckenzie.jpg` | McKenzie | 563-893-8350 |
| `team-shawn.jpg` | Shawn | 512-399-5547 |

Headshots are 440×440 JPEG q84, displayed as circular crops. Photos came from the old WordPress site, where names were paired to faces by carousel position rather than filename — **worth a spot-check that each name is on the right face.**

Shawn's `512-399-5547` is an Austin, Texas area code, unlike the 563/515/319 numbers elsewhere. Reproduced as the old site had it; verify it is current.

`team-group.jpg` is the three-person group photo (Nancy, Kelli, McKenzie), cropped to 3:2 and compressed from 4.3 MB to 164 KB. Full-size originals live in `images/source/team-originals/`.

The grid uses **fixed** column counts (4 across, 2 below 900px), not `auto-fit`. An auto-fit grid picks its own column count and will orphan the last person on a row alone. If you add or remove an advisor, update `grid-template-columns` in `css/style.css` to keep the rows even.

Not carried over from the old site: the cyan logo (superseded), a stock photo, the wave background, the carrier logos (BCBS/Aetna/UnitedHealthcare/Humana — see below), and the *Medicare & You 2024* handbook cover (outdated edition).

Karissa and Hannah were removed from the team in August 2026. Their original headshots remain in `images/source/team-originals/` if they are ever needed again.

## Carrier logos

The old site displayed BlueCross BlueShield, Aetna, UnitedHealthcare and Humana logos. These are deliberately **not** on this site: CMS marketing rules around Medicare Advantage co-branding generally require carrier approval. Add them only if you have that sign-off on file.

## Accessibility notes

This site is built for an older audience, so a few things are deliberate — please keep them if you edit:

- **20px base font size** with a 1.7 line height. Do not shrink this.
- **Colors meet WCAG AAA contrast**: the navy (`#03229e`) is 12.2:1 on white and the red (`#a4231c`) is 7.4:1 — both well above the 4.5:1 minimum.
- **Red is reserved for actions only** (Call / Get Free Help / Contact buttons). Everything structural stays navy, so the red always means "click this."
- **Skip-to-content link** and **4px focus outlines** for keyboard users.
- **`prefers-reduced-motion`** is respected for visitors who get motion sickness.
- Buttons and links are sized for imprecise taps (44px+ targets, full-width on mobile).
