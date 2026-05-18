# Fantail HVAC Website — Full Session Handoff

**Last updated:** 2026-05-18
**Project owner:** Logan Hempel (logan@emporom.org, 029 123 6538)
**Client:** Chris Spayes (founder & MD, Fantail Services Ltd)
**Working directory:** `/Users/loganhempel/Downloads/Fantail HVAC Work/`
**Live demo:** `fantail-website.vercel.app` (Vercel, auto-deploys from main on push)
**Source repo:** `https://github.com/loganhempel/Fantail-Website` (public)
**Purpose of this file:** Paste into the next Claude session as a primer so nothing is missed.

---

## ⚠️ READ FIRST — Critical context

1. **This is NOT the attribution demo.** The `hvac-attribution-demo/` subfolder is a separate Next.js side-project (it has its own `HANDOFF.md`). Ignore unless explicitly asked. The CURRENT focus is the static HTML files at the root of this folder — Fantail's marketing website demo, which will be rebuilt in WordPress once Chris approves the design.

2. **Don't hallucinate Fantail facts.** Past hallucinations Chris would catch:
   - **Largest project = $3.1M** (NOT $60M — earlier hallucination, scrubbed site-wide)
   - **No ammonia (NH₃) or CO₂ refrigerant certification** — not stated on their site, don't claim it
   - **No "3-pipe" VRF technology** — Daikin-specific, not Fantail-stated
   - **No F-gas log book** — that's EU terminology. NZ uses "refrigerant handler certification"
   - Largest concrete advertised credentials: BWOF 12A, COC issuer for electrical, PS1/PS3 design documentation, Approved Handler for refrigerants

3. **Banned photos — never use these URLs again:**
   - `https://images.unsplash.com/photo-1771902985060-6133bb4b2eb6` (snowy rusty rooftop HVAC — Chris hated)
   - `https://images.unsplash.com/photo-1636887584784-954392022b75` (rusty industrial pipes — Chris hated)
   - `https://images.unsplash.com/photo-1556761175-5973dc0f32e7` (office with "WIN" + "BRAZOS" branding — has another company's logo)
   - `https://images.unsplash.com/photo-1503387762-592deb58ef4e` (architect — implied Fantail when it isn't)
   - Anything visibly rusty, dingy, abandoned-looking, AI-stylized, or with foreign-company logos. Use clean modern photos only.

4. **I cannot send emails or text messages.** No email/SMS tools in this session. When asked to send, draft a copy-paste-ready version instead and flag the limitation upfront.

5. **User preferences (durable):**
   - Wants autonomous execution
   - Wants minimal token waste
   - Wants animations and interactivity to be obviously interactive (not subtle)
   - Wants structured/segmented info, not crowded grids
   - Wants schematics + diagrams to be factually accurate (Chris scrutinizes)
   - Wants everything verifiable — no fabricated specifics

---

## 🚨 Pending verification with Chris (TODO list)

Every entry below has a matching `TODO(chris-verify)` HTML comment in the code. Find them with:

```bash
grep -rn "TODO(chris-verify)" *.html
```

| # | Item | Files affected | What's currently shown |
|---|---|---|---|
| 1 | Heat-pump pricing ("from $X" figures) | shop.html × 6, FAQ schema × 3 | "Quote on Request" |
| 2 | Response SLA (enquiry, site survey, emergency callout times) | All 3 index FAQs + visible accordions | Vague "during business hours" + "24/7 emergency" |
| 3 | Warranty terms (workmanship, manufacturer per category) | FAQ schema × 3 | Generic "ask for details" |
| 4 | Residential heat-pump brand list | residential.html (×2) | "all major heat pump brands" |
| 5 | Industrial compressor brand list | industrial.html | "all major industrial compressor platforms" |
| 6 | Shop brand lists (heat pumps, EV, solar inverters, hot-water HP, HRV) | shop.html | Generic copy |
| 7 | 5% price-beat — exact terms | index.html / index2 / index3 (ticker + product cards + FAQ) | Marketing claim left intact (HANDOFF notes it's on the live Fantail site); needs term confirmation |
| 8 | Suburb-level project counts (CBD / Lower Hutt / Upper Hutt / Porirua / Kāpiti / Johnsonville) | commercial / residential / industrial map sections + showcase coverage list | "Active service area" / "HQ · service base" |
| 9 | Solar PV sizing range | shop.html | Generic copy (was "5–10kW") |
| 10 | Hot water heat pump savings | shop.html | Removed "70% cost cut" claim |
| 11 | Heat pump install timeline | shop.html | Removed "Installed within 2 weeks" |
| 12 | $250 install credit / waitlist incentive | shop.html footer | Removed |
| 13 | Real client testimonials (minimum 3 per page for commercial / residential / industrial / homepage) | commercial / residential / industrial + all 3 homepages | Whole testimonial sections wrapped in `<section hidden>` |

**Mechanism for un-doing the hide-and-soften when Chris supplies data:**
- Testimonial sections: remove the `hidden` attribute on the `<section>` tag inside each TESTIMONIALS marker block, then replace the inline placeholder quotes/names
- TODO HTML comments: each comment documents the original wording so you can restore it verbatim if a claim is confirmed true
- For pricing: swap "Quote on Request" `<span>` back to "From $X" format inside the product tile

---

## File inventory (all in `/Users/loganhempel/Downloads/Fantail HVAC Work/`)

### Active website pages (8 HTML files)

| File | Purpose | State |
|---|---|---|
| `index.html` | Dark-theme homepage v1 | Includes the "Inside Fantail" feature block with animated blueprint schematic. Pill nav has Inside link (cyan). Testimonials hidden. FAQ + JSON-LD softened. |
| `index2.html` | Light-theme homepage | Same softened content as index.html, light palette |
| `index3.html` | Chris-feedback baseline (dark) | Has 3-up Res/Comm/Industrial split, Shop preview block, AI Price-Match mock |
| `commercial.html` | Commercial sub-page | **Blue primary palette** (`#01B7F1`) to distinguish from residential. Scope-pill section uses branded blueprint visual block (no stock photos). FAQ pending. Suburb counts softened. |
| `residential.html` | Residential sub-page | **Red primary palette** (kept). Home Comfort Planner widget. Suburb counts softened. Brand lists softened. |
| `industrial.html` | Industrial sub-page | Scope-pill section uses branded blueprint visual block. Suburb counts + compressor brands softened. |
| `shop.html` | E-commerce preview / "Coming Soon" | All "From $X" prices replaced with "Quote on Request". Brand names softened. "$250 install credit" removed. |
| `showcase.html` | "Inside Fantail" scroll-driven page | NEW SVG project constellation (5 sector clusters around Fantail HQ node, all 55 projects as labeled dots). NEW inline consultation form (replaces the bounce-to-index button). |

### Documentation files

| File | Purpose |
|---|---|
| `HANDOFF.md` | THIS file |
| `.gitignore` | Excludes `hvac-attribution-demo/`, .DS_Store, .claude, node_modules |
| `hvac-attribution-demo/` | Separate Next.js attribution demo (different project — ignore unless asked) |

### Image library notes

**Approved Fantail-CDN images** (real Fantail photos via imagedelivery.net):
- Logo: `17ea4896-89bf-4efe-b603-f9c128bedc00/public`
- Team photo: `48be1fba-5aa1-4e43-9823-ab07c2ce7b00/public`
- Wellington home: `2381949d-56b1-479c-8ac3-1414842efb00/public`
- Commercial project: `2c733409-dc95-4d06-59e6-f2d1a607d200/publicContain`

**Approved Unsplash photos currently in use:**
| Photo ID | Context |
|---|---|
| `photo-1554469384-e58fac16e23a` | Commercial hero side widget — modern glass skyscraper |
| `photo-1716643863806-989dd76ae093` | Industrial hero side widget — clean modern machinery |
| `photo-1776860150272-653efc74193c` | Heat pump (residential service card + shop tile) |
| `photo-1745187946672-2c1d8cf26a2b` | Residential solar PV |
| `photo-1564998115952-368e7d4969ea` | Commercial beverage coolers (refrigeration card) |
| `photo-1628630470704-851b2a73271b` | EV charger (shop tile) |
| `photo-1521791136064-7986c2920216` | (still referenced — commercial; consider removing) |
| `photo-1581094271901-8022df4466f9` | (still referenced — commercial; consider removing) |
| `photo-1581092918056-0c4c3acd3789` | (still referenced — industrial; consider removing) |
| `photo-1504917595217-d4dc5ebe6122` | (still referenced — industrial; consider removing) |
| `Heating-and-Air-Conditioning-Fantail.jpg` | (fantailservices.co.nz/wp-content) — residential service card |
| `Electrical-and-Solar-Data.jpg` | (fantailservices.co.nz/wp-content) — electrical service card |
| `Service-Maintenance.jpg` | (fantailservices.co.nz/wp-content) — service & maintenance card |

The previously-used scope-pill stock photos for commercial/industrial have been REPLACED with icon-based blueprint visuals — no longer needed.

---

## Deployment

### Live setup
- **GitHub:** https://github.com/loganhempel/Fantail-Website (public repo)
- **Vercel:** auto-deploys on every push to `main`
  - Framework Preset: Other
  - Build Command: (none)
  - Output Directory: (none — root serves index.html)
- **Auth:** macOS Keychain stores a GitHub PAT (`credential.helper=osxkeychain`). If push fails, the token was likely revoked — generate a new one with `repo` scope at https://github.com/settings/tokens/new and re-save:
  ```bash
  printf "protocol=https\nhost=github.com\nusername=loganhempel\npassword=<new_pat>\n\n" | git credential approve
  ```

### Local dev server

```bash
cd "/Users/loganhempel/Downloads/Fantail HVAC Work" && /usr/local/bin/node -e "
const http = require('http'); const fs = require('fs'); const path = require('path');
http.createServer((req,res)=>{
  let p = req.url === '/' ? '/index.html' : req.url.split('?')[0];
  const fp = path.join(process.cwd(), p);
  fs.readFile(fp,(e,d)=>{ if(e){res.writeHead(404);res.end('404');return;} res.writeHead(200,{'Content-Type':fp.endsWith('.html')?'text/html':'application/octet-stream'}); res.end(d); });
}).listen(8080, ()=>console.log('ready on 8080'));
" > /tmp/fantail-srv.log 2>&1 &
disown
```

Then open `http://localhost:8080/<page>.html` — try `/showcase.html` for the centerpiece visual.

**Node:** `/usr/local/bin/node` (v22.22.2) · **npm:** `/usr/local/bin/npm` (v10.9.7)

---

## Real Fantail facts (verified — never get wrong)

| Fact | Value |
|---|---|
| Founded | 2010 |
| Years active (as of 2026-05-18) | **16** |
| Founder / Managing Director | **Chris Spayes** |
| Staff | 42 |
| Service vehicles | 22 |
| Largest project value | **$3.1M** (NOT $60M — that was a hallucination) |
| Total projects (verified scrape) | 55 |
| HQ address | 5 Pretoria Street, Hutt Central, Lower Hutt 5010 |
| PO Box | 38252, Wellington Mail Centre, Lower Hutt 5045 |
| Phone | (04) 212 4763 |
| Email | office@fantailservices.co.nz |
| Hours | Mon–Fri 7:30am–5:00pm (24/7 emergency) |
| Social | facebook.com/fantailservices · linkedin.com/company/fantail-services-ltd |

**Service sectors actually advertised on their site:**
- Large commercial construction
- Residential new build housing
- Industrial / manufacturing
- Commercial fit-outs & replacement works
- Education buildings
- Residential heat pump installs / replacements
- Service & maintenance contracts
- Design & build projects

**Multi-trade disciplines actually advertised:**
HVAC (mechanical) · Electrical · Solar PV · Data · Security

**Brand partners actually on their site (commercial HVAC page only):**
Daikin · Gree · Hitachi · Mitsubishi · Temperzone

**Industries served they explicitly mention:**
Bio labs · Server rooms · UPS facilities · Produce storage

**Real Fantail mission statement (from about-us, use verbatim):**
> "When founding Fantail, my mission was to be consistently recognised as the supplier of choice, the employer of choice, the solution of choice and a company that supports the communities where we do business." — Chris Spayes

### 55 verified real Fantail projects (from fantailservices.co.nz/commercial/our-projects/)

| Sector | Projects |
|---|---|
| **Apartment Blocks (8)** | 114 The Terrace, 120 Victoria Street, Book House, Colombo Street, Frederick Street, Haining Street, Hyde Lane, Kotuku Apartments |
| **Commercial (9)** | 134 Queens Drive, Bamford Warehouse, Capital City Ford & Mazda, Lane Street Studios, Placemakers, Plumbline Head Office, TerraCat, Tesla Centre, Maritime Tower |
| **Community (4)** | Alex Moore Park, Maidstone, Hutt Park Indoor Sports, Regional Bowls Centre |
| **Education (8)** | Brooklyn School, Kelburn School, Raphael House Rudolf Steiner, Te Wananga o Aotearoa, Tararua College, Te Kura Porirua, Thorndon School, Wellington East Girls College |
| **Fit Out (6)** | 17 Ihakara Street, 318 Lambton Quay, Home of Compassion, PSA House Roof, Skyline Medical Centre, Whenua Tapu Cemetery |
| **FMCG / Retail (3)** | Farrah's Headquarters, Whitby New World, KFC Porirua |
| **Government (7)** | Callaghan Innovation, CIT Campus, MetService Kapiti, Samoan High, Trentham Camp, Newtown Fire Station, Upper Hutt Railway Station |
| **Heritage / Culture (2)** | 135 Jackson, Ministry of Heritage & Culture Trust |
| **Industrial (2)** | Macaulay Metals, MSD |
| **Residential (2)** | 28 Palliser Road, Wellington Mansion |
| **Healthcare (3)** | Mary Potter Hospice, Onslow Medical Centre, Ora Toa Pōneke Medical Centre |
| **Subdivisions (1)** | Dwell Housing |

**Total: 55** — all rendered in `showcase.html` § 5 as the SVG constellation + sector chip grid.

### Open roles (from careers page, as of last scrape)
- Admin Coordinator
- Refrigeration & Air-Conditioning Service Engineer
- Industrial Electrician
- Mechanical (HVAC) Electrician — Central North Island
- Senior Estimator

---

## Change log — full history

### Round 1: Initial demos (pre-Chris-feedback)
- Built dark + light home page variants (index.html, index2.html)
- Both have hero, trust numbers, 3-up segment, services, How It Works, Projects, Featured Projects + Coverage map, About, Why Fantail, Testimonials, FAQ, CTA Band, Contact form, Footer
- Added mobile sticky CTA bar (Call + Get Quote)
- Replaced 3 AI-looking service-card photos with real ones (Chris feedback round 1)
- Reordered "Commercial/Residential split" to come ABOVE Services section (Chris's funnel logic)
- Redesigned "How It Works" with step icons, hover effects, animated connecting line

### Round 2: Chris's main feedback email (industrial / shop / pop)
- Built `index3.html` as Chris's feedback baseline
- Replaced 2-up split with **3-up split**: Residential / Commercial / Industrial
- Added Shop preview section (6 product tiles + AI Price-Match mock UI)
- Built `industrial.html` (mirror of commercial.html with industrial copy)
- Built `shop.html` standalone page
- Added "Inside" link to nav across sub-pages
- Updated nav on commercial.html + residential.html for parity

### Round 3: Showcase page + factual cleanup
- Built `showcase.html` "Inside Fantail" scroll-driven creative page
- Saved reusable skill: `~/.claude/skills/schematic-animation/SKILL.md`
- Scrubbed all `$60M` claims site-wide (replaced with 55+ projects / multi-million-dollar M&E)
- Added residential schematic (§02), commercial schematic with prev/next nav (§03)
- Reordered commercial schematic to real construction sequence (Structure → Electrical → HVAC → VRF → Refrigeration → Server → Solar LAST)
- Constellation replaced with sector-card chip grid (cleaner, no overlap, all 55 projects)

### Round 4: Big polish round
- **Wellington map rebuilt** across commercial, residential, industrial — geographically-recognisable region map
- **Hero side widgets** on commercial + industrial: dashboard widget replaced with clean photo + overlay
- **Scope-panel switcher** on commercial + industrial: image swap per scope with fade animation
- **Showcase hero rebuilt**: animated rotating compass + line-drawing building schematic
- **Residential Home Comfort Planner** polished
- **Industrial services** restructured into 3 categories × 3 cards
- **Shop page** branding tightened
- **SEO + schema**: every page got Wellington-keyword titles + meta + OG + JSON-LD `HVACBusiness` schema. Homepage variants got `FAQPage` schema.

### Round 5: GitHub + Vercel deployment
- Initialised git repo, pushed to GitHub (`loganhempel/Fantail-Website`)
- Set up Vercel auto-deploy on push to `main`
- Configured macOS Keychain credential helper for PAT-based git auth

### Round 6: Initial Inside Fantail integration
- Added "Inside" nav link (desktop + mobile) on index.html
- Added prominent "Inside Fantail" feature banner between trust numbers and comm/res split
- Replaced showcase.html's bounce-to-index "Talk to the team" button with a full inline consultation form (contact details + enquiry form in blueprint style)

### Round 7: Showcase constellation rebuild + scope-panel redesign + colour split
- **Showcase project constellation:** rebuilt as inline SVG with 5 sector clusters (Commercial, Education, Healthcare, Government, Industrial) laid out on non-overlapping grid regions around a central Fantail HQ node. All 55 projects shown as labeled colored dots. Fixed the prior reveal bug where sector chip-grid cards stayed at opacity:0 because they were inserted after the global IntersectionObserver ran.
- **Scope-pill section redesign (commercial + industrial):** stock photos out entirely (one had foreign company's "WIN/BRAZOS" branding; another was irrelevant beverage coolers). Replaced with a branded blueprint visual card with a large scope icon that swaps per pill (drafting-compass → handshake → contract → wrench on commercial; industry → handshake → arrows-rotate → gauge on industrial).
- **Commercial palette swap:** primary accent moved from red to blue (`#01B7F1`) to differentiate from residential (which stays red `#EC263C`). Industrial untouched.

### Round 8: Pill gap fix + Inside Fantail right-block animation
- **Pill section gap:** root cause found and fixed. The `scope-design` div had a Tailwind `grid` utility class that survived the `.active` class being removed (CDN Tailwind's `.grid{display:grid}` rule loaded after the custom `.scope-panel{display:none}` rule, so it won by source order). That meant inactive panels stayed `display:grid` with `opacity:0`, taking ~270px of layout space — the gap. Removed the redundant `grid` class.
- **Inside Fantail right block:** replaced the duplicate stats grid (42 / 22 / 55 — which duplicated the trust numbers above it) with the animated blueprint schematic from the showcase hero (rotating compass, counter-rotating crosshair, building + HVAC unit + solar panel line-drawing with pulse markers, LIVE/UP status badges). Reduced-motion-aware.

### Round 9: Full hallucination audit + strip-and-soften pass
- **Audit findings:** dozens of fabricated specifics flagged across all 8 HTML files
  - Geographic per-suburb project counts (45+ in CBD, 60+ in Lower Hutt, etc.) — invented; HANDOFF only has total of 55
  - Heat-pump pricing ($1,299, $2,200-$4,000) — invented
  - SLA timings ("within 2 business hours", "site survey same week", "tech on site inside the hour") — invented
  - Warranty terms (12-month workmanship, 5-7yr/10yr/25yr) — invented
  - 8 fabricated testimonial personas across all pages (James T., Sarah R., Daniel M., Karen W., Mike B., Anna T., Mei K., Dave K.). Mei K. also used banned "F-gas reporting" terminology.
  - Brand names beyond HANDOFF's verified list (Fujitsu, Panasonic, Toshiba, Bitzer, Frick, Mycom, Sabroe, Sungrow, Fronius, Tesla, EVNEX, Wallbox, Reclaim Energy, Apricus, Stiebel Eltron, SmartVent, HRV-as-brand)
  - "Cut hot-water cost by 70%" performance claim — invented
  - "Installed within 2 weeks" timeline claim — invented
  - "$250 install credit" waitlist hook — invented
  - "Wellington's leading" superlative — unverifiable
  - Year math errors ("15 years" — Fantail founded 2010, today 2026 = 16)
- **Strip-and-soften pass:** removed/softened every fabricated specific. All 8 pages now have only verified-or-vague content. Inline `TODO(chris-verify)` HTML comments at each replacement spot list the original claim verbatim so it can be restored when Chris confirms.
- **Testimonial sections:** wrapped all 6 in `<section hidden>` (HTML attribute) with TODO comments so they're invisible but easy to find and re-enable with real client quotes.
- **FAQ JSON-LD schemas:** rewritten on all 3 homepages to remove pricing/SLA/warranty/brand claims while keeping the verified BWOF/PS1/PS3/COC/24-7 facts. Original claims documented in HTML comments at top of each schema.

---

## What's NOT done (open work)

| Item | Why deferred |
|---|---|
| **Real shop with cart/checkout** | Out of demo scope — WooCommerce or similar, 2–4 weeks WP work |
| **Real AI price-match engine** | Out of demo scope — backend project, 4–8 weeks. UI mock only. |
| **FAQ section on commercial.html** | Doesn't have one yet (only homepages do) |
| **FAQ section on industrial.html** | Same |
| **Light-theme variant of index3** | index2.html is still the original light baseline |
| **Real videos** | Need real footage from Chris |
| **Real client testimonial content** | All 6 testimonial sections currently hidden — needs Chris to supply quotes |
| **Light-mode contrast WCAG sweep** | index2.html has muted text (#999 on #F7F6F2 ≈ 3.4:1) that fails WCAG AA |
| **WordPress build** | Final step after Chris approves the design |
| **Chris-confirmed values for all 13 TODO items above** | Pending Chris's verification round |

---

## Skills & memory saved

- **Skill:** `~/.claude/skills/schematic-animation/SKILL.md` — reusable pattern for scroll-driven SVG schematic pages (blueprint aesthetic). Reference impl: `showcase.html`.
- **Memory:** `/Users/loganhempel/.claude/projects/-Users-loganhempel/memory/project_fantail_focus.md` — explains the two-projects-in-one-folder situation.

---

## Design language / brand notes

- **Brand primary red:** `#EC263C` (residential primary, industrial primary, showcase accent)
- **Brand secondary blue:** `#01B7F1` (**commercial primary** as of Round 7 — was red, swapped to differentiate)
- **Showcase blueprint accent:** `#7dd3fc` (cyan — only on showcase.html)
- **Type:**
  - Dark home (index.html): Poppins (headings) + Plus Jakarta Sans (body) + Playfair Display italic for accents
  - Light home (index2.html): Montserrat (headings) + Plus Jakarta Sans (body) + Playfair Display italic
  - Sub-pages (commercial/residential/industrial): Montserrat + Inter
  - Showcase: Poppins + JetBrains Mono (callouts) + Plus Jakarta Sans
- **Animation grammar:**
  - Subtle reveal on scroll (`.r` / `.rev` class + IntersectionObserver)
  - SVG line-draw via stroke-dasharray + stroke-dashoffset
  - Hover lift + glow for interactive cards
  - Pulse for live indicators (red dot + ring)
  - Drift/breathe with `prefers-reduced-motion` respected

---

## Common pitfalls to avoid (lessons learned this session)

1. **Don't claim refrigerants Fantail hasn't certified.** Avoid: CO₂, ammonia (NH₃), F-gas log book. Safe: refrigerant handler certification, approved handling.
2. **Don't reference "3-pipe" VRF.** Daikin-specific tech. Say "heat recovery VRF" instead.
3. **Don't put solar PV first in install sequence.** It goes LAST. Real order in commercial: Structure → Electrical → HVAC → VRF → Refrigeration → Server cooling → Solar → Commissioning.
4. **Cool rooms run at +2°C, not −2°C.** −2°C is freezer territory.
5. **Don't use rusty/snowy/foreign-branded photos.** Banned URLs listed above.
6. **When adding nav links, update both desktop AND mobile nav AND footer.**
7. **Update meta tags + canonical when adding pages.**
8. **`#map-section` was a broken anchor in the original** — should be `#coverage`. Replaced site-wide.
9. **Plant Dashboard / Project Dashboard sidebar widgets are out** — Chris hated them. Real photo + minimal overlay only.
10. **CDN Tailwind class-order pitfall:** custom `<style>` blocks in `<head>` load BEFORE the CDN Tailwind script injects its CSS. So Tailwind utility classes like `grid`, `block`, `hidden` will override your custom CSS for the same property. Either avoid duplicate Tailwind utilities on elements that also have custom-CSS-controlled display states, or use `!important` in custom CSS, or put your custom rules in a `<style>` block AFTER the Tailwind script.
11. **`<section hidden>` is the cleanest way to temporarily disable a marketing section** without deleting content — content stays in source for easy restoration.

---

## Pages-to-CRO-element checklist

| Element | index | index2 | index3 | commercial | residential | industrial | shop | showcase |
|---|---|---|---|---|---|---|---|---|
| Hero photo background | ✅ | ✅ | ✅ | photo widget | photo widget | photo widget | ❌ | bespoke animated SVG |
| Mobile sticky CTA | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ |
| FAQ section | ✅ | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ | ❌ |
| FAQ schema markup | ✅ softened | ✅ softened | ✅ softened | ❌ | ❌ | ❌ | ❌ | ❌ |
| LocalBusiness schema | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| OG + Twitter cards | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Wellington coverage map | ❌ | ❌ | ❌ | ✅ | ✅ | ✅ | ❌ | uses constellation grid |
| 3-up segment block | ❌ (2-up) | ❌ (2-up) | ✅ | n/a | n/a | n/a | n/a | n/a |
| Shop preview | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | full page | n/a |
| AI Price-Match mock | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ✅ | n/a |
| Showcase nav link | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | n/a |
| Inside Fantail feature block | ✅ NEW | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | n/a |
| Testimonials visible | ❌ hidden | ❌ hidden | ❌ hidden | ❌ hidden | ❌ hidden | ❌ hidden | ❌ | ❌ |
| Inline consultation form | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ NEW |
| Project constellation SVG | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ NEW |

---

## Outstanding asks from Chris (his original email)

| Ask | Status |
|---|---|
| Industrial section, all 3 stand out | ✅ Done (index3 has 3-up, industrial.html exists) |
| Online shop heat pumps / EV / solar / hot water HP / smart panels / HRU | ✅ Preview on index3 + dedicated shop.html (pricing now "Quote on Request" pending real prices) |
| AI quote price-match | ✅ Mock UI on index3 + shop.html (clearly demo) |
| Visual "pop" like the drinks photo | ⚠️ Partial — service cards have photos; could go further on hero/projects |
| Study competitor refs (Naylor Love, Aquaheat, Turn You On, Smart EV, etc.) | ❌ Not done — went on instinct |
| Real videos & images | ❌ Need Chris to supply |
| Industrial sub-page | ✅ industrial.html exists |

---

## Quick "next session" prompts to consider

- "Plug in Chris's confirmed values from the TODO(chris-verify) list and unhide the testimonials sections with real quotes"
- "Build out FAQ sections on commercial.html and industrial.html, with sector-specific SEO-targeted questions"
- "Make a Wellington-services-only specific landing page for [solar / heat pumps / EV chargers] with deep SEO targeting"
- "Add a project case study page template — `case-study-template.html` — and populate 3 (Whitby New World, Mary Potter Hospice, Onslow Medical) with detailed scope, photos, results"
- "Build the residential booking-flow mock — step-by-step quote builder for heat pumps with instant-price-estimate"
- "Build a Wellington Coverage interactive — clickable suburbs with detailed sub-region coverage info"
- "Apply the same content audit to any new copy added — verify every specific claim against this HANDOFF before committing"

---

## Email/SMS limitation

This session has NO email or SMS tool. When asked to send:
- Draft a copy-paste-ready email or SMS in the response
- Flag the limitation upfront
- Don't pretend it's been sent

Logan's contact: logan@emporom.org · 029 123 6538

---

## End of handoff
