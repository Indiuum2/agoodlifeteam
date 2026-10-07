# A Good Life Team Website: Site Notes

How agoodlifeteam.com is built and wired together. Keep this file updated when something changes.

Last updated: October 2026

---

## The basics

- **Live site:** https://agoodlifeteam.com
- **Test address:** https://agoodlifeteam.netlify.app
- **Team:** Jason & Kari Bollinger, A Good Life Team, powered by eXp Realty
- **Built with:** plain HTML and CSS files. No WordPress, no database.

## Where everything lives

| What | Where |
|---|---|
| Domain name | GoDaddy |
| DNS records | GoDaddy (not Netlify DNS) |
| Website files | GitHub: Indiuum2/agoodlifeteam (public, view-only to others) |
| Hosting | Netlify project "agoodlifeteam," auto-publishes from GitHub |
| HTTPS padlock | Netlify (free Let's Encrypt certificate, renews on its own) |
| Email | Google Workspace on agoodlifeteam.com |
| Home search | Lofty (eXp's IDX), jasonbollinger.expportal.com |

## GoDaddy DNS: what each record does

Only two records point to the website. Everything else runs email. **Do not edit the email records.**

| Type | Name | Value | Purpose |
|---|---|---|---|
| A | @ | 75.2.60.5 | Website (Netlify) |
| CNAME | www | agoodlifeteam.netlify.app | Website (Netlify) |
| MX | @ | smtp.google.com | Email delivery. Don't touch. |
| TXT | @ | google-site-verification=... | Google verification. Don't touch. |
| TXT | @, dc-..._spfm, google._domainkey, _dmarc | SPF / DKIM / DMARC | Email security. Don't touch. |

If the site ever breaks after a DNS change, compare against this table.

## Email

- Jason and Kari each have a mailbox on agoodlifeteam.com
- **info@agoodlifeteam.com** is a Google Group (not a mailbox). It delivers to both. Outside senders are allowed to post.

## Pages

| File | Page | Notes |
|---|---|---|
| index.html | Home | Hero, how we help, meet Jason & Kari, contact. Holds the Google structured data. |
| about.html | About Us | Bio, how we work, service areas |
| buyers.html | Buyers | 5-step buyer process, buyer agreement note |
| sellers.html | Sellers | 5-step seller process, home value offer |
| search.html | Search Homes | Branded page with city buttons that open Lofty |
| contact.html | Contact | Netlify form |
| thanks.html | Thank you | Shown after the form is sent. Hidden from Google. |

Other files:
- **css/styles.css** controls the look of every page
- **images/** holds the logos, headshot, and link-preview image (share.jpg)
- **sitemap.xml** and **robots.txt** help Google find the pages

## Contact form

- Netlify Forms, form name **contact**
- Form detection is turned on in Netlify
- Email alerts go to **info@agoodlifeteam.com**
- Email subject reads **NEW LEAD-AGL WEBSITE | [Name]**. Set by a hidden "subject" field in contact.html. Leave the subject box in Netlify blank.
- Links like contact.html?interest=Buying or ?interest=Selling pre-check that option on the form
- Spam filter: hidden "bot-field" honeypot

## Home search (Lofty)

- Every Search Homes button on the site goes to **search.html** first, then out to Lofty
- Full search: https://jasonbollinger.expportal.com/listing
- City buttons use Lofty's search filter in the link. Two ways to filter:
  - **By city:** `{"location":{"city":["Titusville, FL"]}}`
  - **By zip code:** `{"location":{"zipCode":["32940"]}}`
- **Viera** uses zip 32940 and **Port St. John** uses zip 32927, because most listings there are filed under Melbourne or Cocoa
- **The Beaches** searches six towns: Cocoa Beach, Cape Canaveral, Satellite Beach, Indian Harbour Beach, Indialantic, Melbourne Beach
- To add a city: search it in Lofty, copy the address bar, and follow the same pattern
- **Embedding Lofty inside the site was tested and rejected.** It loads on computers but shows blank on iPhones.

### Lofty site cleanup (done)
- Header logo: team mark with gold divider (eXp logo is locked in place by eXp)
- Home page reduced to one branded intro block
- Text color tip: highlight the text first, then change the color

## Google

- **Analytics:** Measurement ID G-NNYSGWHN13, in the head of every page
- **Search Console:** URL-prefix property for https://agoodlifeteam.com, verified through Analytics. Sitemap submitted.
- **Structured data:** RealEstateAgent code at the bottom of the head in index.html. Lists team members, phones, service areas, eXp, and social links. Update the service-area list when adding cities.
- **Link previews:** og: tags on each page. Texts and social posts show "A Good Life Team | eXp Realty" with images/share.jpg.
- **Business Profile:** verified as a service-area business (address hidden). Kari is an owner.
- **Review link:** https://g.page/r/CcZwB6-S0Ux2ECE/review (also in the site footer)

## Brand kit

| Item | Value |
|---|---|
| Navy | #103450 |
| Gold | #C5A264 (RGB 197, 162, 100) |
| Ocean blue | #3C80AD |
| Light background | #EAF1F6 |
| Heading font | Outfit |
| Body font | Source Sans 3 |

## Compliance reminders

- eXp Realty must appear on every page. The header and footer logo handle this.
- Florida rule: the brokerage name must be at least the same size as the team name. Use the official logo files as-is.
- Footer brokerage address: eXp Realty, LLC, 10752 Deerwood Park Blvd #100, Jacksonville, FL 32256 (confirm with eXp)
- Fair housing: describe places and amenities, never who an area is "good for"
- Get eXp approval before using any new logo layout

## How to make changes

1. Start a chat and say: "I want to update the A Good Life Team website. The repo is Indiuum2/agoodlifeteam."
2. Claude pulls the current files from GitHub and makes the change
3. Upload the changed files to GitHub. Files in css/ or images/ go inside those folders.
4. Use the commit message Claude provides
5. Netlify publishes in about a minute. Hard refresh to check (Cmd+Shift+R on Mac).

To delete a file in GitHub: open it, then the three dots (⋯) at the top right next to "History."

## Open to-dos

- [ ] Lofty support: remove the Texas notice from the footer
- [ ] Lofty support: set up the team so Kari appears in "Our Team"
- [ ] Lofty support: fix footer phone and email (currently 321-693-5794 and exprealty.com address)
- [ ] Lofty support: ask about the Vanity Domain upgrade (search.agoodlifeteam.com) and widgets
- [ ] eXp compliance: approve the stacked square logo, then upload it as the Google logo
- [ ] Google Business Profile: add hours and services, set the wide cover photo
- [ ] Google Business Profile: make jason@agoodlifeteam.com the primary owner (after the 7-day wait)
- [ ] Analytics: add Kari as an Administrator
- [ ] Add Palm Bay and Port St. John to the service areas on About, Contact, and the structured data
- [ ] Update the DBPR mailing address (privacy)
- [ ] Add YouTube once there's content
- [ ] Later: city area pages, testimonials, and a Join Our Team page after a few closings and 10+ reviews
