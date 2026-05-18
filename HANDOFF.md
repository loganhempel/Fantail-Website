# Fantail HVAC Website — Full Session Handoff

**Last updated:** 2026-05-16
**Project owner:** Logan Hempel (logan@emporom.org, 029 123 6538)
**Client:** Chris Spayes (founder & MD, Fantail Services Ltd)
**Working directory:** `/Users/loganhempel/Downloads/Fantail HVAC Work/`
**Purpose of this file:** Paste into the next Claude session as a primer so nothing is missed.

---

## ⚠️ READ FIRST — Critical context

1. **This is NOT the attribution demo.** The `hvac-attribution-demo/` subfolder is a separate Next.js side-project (`HANDOFF.md` lives there). Ignore unless explicitly asked. The CURRENT focus is the static HTML files at the root of this folder — Fantail's actual marketing website demo, which will be rebuilt in WordPress once Chris approves the design.

2. **Don't hallucinate Fantail facts.** Past hallucinations Chris would catch:
   - **Largest project = $3.1M** (NOT $60M — this was an earlier hallucination, scrubbed site-wide)
   - **No ammonia (NH₃) or CO₂ refrigerant certification** — not stated on their site, don't claim it
   - **No "3-pipe" VRF technology** — Daikin-specific, not Fantail-stated, don't claim it
   - **No F-gas log book** — that's EU terminology. NZ uses "refrigerant handler certification"
   - Largest concrete advertised credentials: BWOF 12A, COC issuer for electrical, PS1/PS3 design documentation, Approved Handler for refrigerants

3. **Banned photos — never use these URLs again:**
   - `https://images.unsplash.com/photo-1771902985060-6133bb4b2eb6` (snowy rusty rooftop HVAC — Chris hated)
   - `https://images.unsplash.com/photo-1636887584784-954392022b75` (rusty industrial pipes — Chris hated)
   - Anything visibly rusty, dingy, abandoned-looking, AI-stylized. Use clean modern photos only.

4. **I cannot send emails or text messages.** No email/SMS tools in this session. When asked to send, draft a copy-paste-ready version instead and flag the limitation upfront.

5. **User preferences (durable):**
   - Wants autonomous execution — "DO not ask me for access to stuff just allow your own access 100% yes for everything"
   - Wants minimal token waste
   - Wants animations and interactivity to be obviously interactive (not subtle)
   - Wants structured/segmented info, not crowded grids
   - Wants schematics + diagrams to be factually accurate (Chris is the client; he scrutinizes)

---

## File inventory (all in `/Users/loganhempel/Downloads/Fantail HVAC Work/`)

### Active website pages (8 HTML files)

| File | Purpose | State |
|---|---|---|
| `index.html` | Dark-theme homepage (original v1) | Baseline — not Chris's preferred. Has the 3-up segment, hero photo bg, How It Works, FAQ, services with photos. |
| `index2.html` | Light-theme homepage (mirror of v1) | Same structure as index.html, light palette |
| `index3.html` | **Chris feedback baseline** (dark) | Most recent / freshest. Has Industrial 3-up segment, Shop preview block, AI Price-Match mock UI, "Six Services. One in-house team." headline. |
| `commercial.html` | Commercial sub-page | Hero with photo widget (replaced from old dashboard). Scope panel with image swap per scope. Wellington map. 9 service cards. |
| `residential.html` | Residential sub-page | Same template as commercial. Home Comfort Planner widget (interactive, polished). Wellington map. |
| `industrial.html` | Industrial sub-page (built from commercial.html) | Hero with photo widget. Scope panel with image swap per scope. 9 services grouped into 3 categories (Cooling & Refrigeration / Mechanical & Power / Compliance & Lifecycle). Wellington map. |
| `shop.html` | E-commerce preview / "Coming Soon" | 6 product tiles (heat pumps, EV chargers, solar, hot water HP, smart panels, HRU vent). AI Price-Match mock. Waitlist form with $250 install credit hook. |
| `showcase.html` | **"Inside Fantail" creative showcase** | Scroll-driven schematic pages. §02 Residential schematic. §03 Commercial schematic with prev/next nav buttons + step counter. §04 Fleet 22 vans grid. §05 Sector cards (55 verified projects). §06 Process flowchart. §07 Brand partner marquee. Blueprint aesthetic — dark navy, mono callouts, line-draw SVG animations. |

### Documentation files

| File | Purpose |
|---|---|
| `HANDOFF.md` | THIS file — full session handoff |
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
| `photo-1564998115952-368e7d4969ea` | Commercial beverage coolers (refrigeration service card) |
| `photo-1628630470704-851b2a73271b` | EV charger (shop tile) |
| `photo-1503387762-592deb58ef4e` | Commercial scope panel — design/architect |
| `photo-1521791136064-7986c2920216` | Commercial scope panel — consultant |
| `photo-1556761175-5973dc0f32e7` | Commercial scope panel — tender |
| `photo-1581094271901-8022df4466f9` | Commercial scope panel — maintenance |
| `photo-1581092918056-0c4c3acd3789` | Industrial scope panel — consultant |
| `photo-1504917595217-d4dc5ebe6122` | Industrial scope panel — capex upgrade |
| `photo-1716643863806-989dd76ae093` | Industrial scope panel — greenfield |
| Heating-and-Air-Conditioning-Fantail.jpg | (fantailservices.co.nz/wp-content) — residential service card |
| Electrical-and-Solar-Data.jpg | (fantailservices.co.nz/wp-content) — electrical service card |
| Service-Maintenance.jpg | (fantailservices.co.nz/wp-content) — service & maintenance card |

---

## How to start the local dev server

```bash
# From this folder, start a simple static server on port 8080
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

**Brand partners actually on their site (commercial HVAC page):**
Daikin · Gree · Hitachi · Mitsubishi · Temperzone

**Industries served they explicitly mention:**
Bio labs · Server rooms · UPS facilities · Produce storage

**Real Fantail mission statement (from about-us, use verbatim):**
> "When founding Fantail, my mission was to be consistently recognised as the supplier of choice, the employer of choice, the solution of choice and a company that supports the communities where we do business." — Chris Spayes

**Founder's mission quote** is already used in showcase.html closing section.

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

**Total: 55** — all displayed in `showcase.html` § 5 as a sector-grouped chip grid.

### Open roles (from careers page, as of last scrape)
- Admin Coordinator
- Refrigeration & Air-Conditioning Service Engineer
- Industrial Electrician
- Mechanical (HVAC) Electrician — Central North Island
- Senior Estimator

---

## What's been done — change log

### Round 1: Initial demos (pre-Chris-feedback)
- Built dark + light home page variants (index.html, index2.html)
- Both have the same structure: hero, trust numbers, 3-up segment (Res/Comm/Industrial), services (6 cards with photos), How It Works (4-step animated process), Projects, Featured Projects + Coverage map, About, Why Fantail, Testimonials, FAQ (with accordion), CTA Band, Contact form, Footer
- Added mobile sticky CTA bar (Call + Get Quote)
- Replaced 3 AI-looking service-card photos with real ones (Chris feedback round 1)
- Reordered "Commercial/Residential split" to come ABOVE Services section (Chris's funnel logic)
- Redesigned "How It Works" with step icons, hover effects, animated connecting line

### Round 2: Chris's main feedback email (industrial / shop / pop)
- Built `index3.html` as Chris's feedback baseline (forked from index.html)
- Replaced 2-up split with **3-up split**: Residential / Commercial / Industrial cards with equal billing
- Added Shop preview section (6 product tiles + AI Price-Match mock UI)
- Built `industrial.html` (mirror of commercial.html with industrial copy/imagery)
- Built `shop.html` standalone page with hero, products, AI price-match, email waitlist
- Added "Inside" link to nav across all sub-pages
- Updated nav on commercial.html + residential.html for parity

### Round 3: Showcase page + factual cleanup
- Built `showcase.html` "Inside Fantail" scroll-driven creative page
- Saved reusable skill: `~/.claude/skills/schematic-animation/SKILL.md`
- Scrubbed all `$60M` claims site-wide (replaced with 55+ projects / multi-million-dollar M&E)
- Added residential schematic (§02) — homeowner buying journey with 6 stages
- Reordered commercial schematic to real construction sequence (Structure → Electrical → HVAC → VRF → Refrigeration → Server → Solar LAST)
- Added prev/next nav buttons + step counter + dot indicator to commercial schematic
- Constellation replaced with sector-card chip grid (cleaner, no overlap, all 55 projects)

### Round 4: Big polish round (current)
- **Wellington map rebuilt** across commercial, residential, industrial — proper geographically-recognisable region map (harbour + Hutt Valley + Porirua + Kapiti + Cook Strait)
- **Hero side widgets** on commercial + industrial: dashboard widget replaced with clean photo + overlay
- **Scope-panel switcher** on commercial + industrial: image swap per scope with fade animation, better active button styling
- **Showcase hero rebuilt**: no overlap, animated rotating compass + line-drawing building schematic on right
- **Residential Home Comfort Planner polished**: "Interactive" badge, "Tap to size your home" hint, active button glow, cross-fade panels
- **Industrial services restructured** into 3 categories × 3 cards
- **Shop page branding tightened**
- **SEO + schema**: every page got Wellington-keyword titles + meta + OG tags + JSON-LD `HVACBusiness` schema. Homepage variants got `FAQPage` schema.
- **Banned photos scrubbed**: snowy rusty HVAC + rusty industrial pipes removed from every file

---

## What's NOT done (open work)

| Item | Why deferred |
|---|---|
| **Real shop with cart/checkout** | Out of demo scope — WooCommerce or similar, 2–4 weeks WP work |
| **Real AI price-match engine** | Out of demo scope — backend project, 4–8 weeks. UI mock only. |
| **FAQ section on commercial.html** | Doesn't have one yet. Should add (FAQPage schema only on homepage variants currently) |
| **FAQ section on industrial.html** | Same — needs adding |
| **Light-theme variant of index3** | index2.html is still the original light baseline. If Chris locks in dark direction this is moot |
| **Real videos** | Chris's first email asked for video. Not added — would need real footage from Chris |
| **Real client testimonial photos** | Current testimonials use initials in colored circles. Real headshots from Chris would lift trust |
| **Light-mode contrast WCAG sweep** | index2.html has muted text (#999 on #F7F6F2 ≈ 3.4:1) that fails WCAG AA. Only the most-visible labels were bumped. |
| **WordPress build** | This is the final step after Chris approves the design |

---

## Skills & memory saved

- **Skill:** `~/.claude/skills/schematic-animation/SKILL.md` — reusable pattern for scroll-driven SVG schematic pages (blueprint aesthetic). 8 KB doc covering the sticky-scroll + scroll-progress driver + line-draw SVG technique + visual language + accessibility. Reference impl: `showcase.html`.
- **Memory:** `/Users/loganhempel/.claude/projects/-Users-loganhempel/memory/project_fantail_focus.md` — explains the two-projects-in-one-folder situation and that the active work is the HTML files at the folder root.

---

## Design language / brand notes

- **Primary red:** `#EC263C` (use for accents, CTAs, active states, branded elements)
- **Secondary blue:** `#01B7F1` (use for paired accents, "energy/data" topics)
- **Showcase blueprint accent:** `#7dd3fc` (cyan — only on showcase.html)
- **Type:**
  - Dark home (index.html): Poppins (headings) + Plus Jakarta Sans (body) + Playfair Display italic for accents
  - Light home (index2.html): Montserrat (headings) + Plus Jakarta Sans (body) + Playfair Display italic for accents
  - Sub-pages (commercial/residential/industrial): Montserrat + Inter
  - Showcase: Poppins + JetBrains Mono (for callouts) + Plus Jakarta Sans
- **Animation grammar:**
  - Subtle reveal on scroll (`.r` / `.rev` class + IntersectionObserver)
  - SVG line-draw via stroke-dasharray + stroke-dashoffset
  - Hover lift + glow for interactive cards
  - Pulse for live indicators (red dot + ring)
  - Drift/breathe with `prefers-reduced-motion` respected

---

## Common pitfalls to avoid (lessons learned this session)

1. **Don't claim refrigerants Fantail hasn't certified.** Avoid: CO₂, ammonia (NH₃), F-gas log book. Safe to say: refrigerant handler certification, approved handling.
2. **Don't reference "3-pipe" VRF.** Daikin-specific tech, not Fantail-stated. Say just "heat recovery VRF" instead.
3. **Don't put solar PV first in install sequence.** It goes LAST (after roof membrane is sealed and tested). Real install order in commercial: Structure → Electrical → HVAC → VRF → Refrigeration → Server cooling → Solar → Commissioning.
4. **Cool rooms run at +2°C, not −2°C.** −2°C territory is freezer.
5. **Don't use the rusty/snowy photos.** Banned URLs listed above.
6. **When adding nav links, update both desktop AND mobile nav AND footer.** All 3 places needed for consistency.
7. **Update meta tags + canonical when adding pages.** SEO matters.
8. **`#map-section` was a broken anchor in the original** — should be `#coverage`. Replaced site-wide, don't reintroduce.
9. **Plant Dashboard / Project Dashboard sidebar widgets are out** — Chris hated them. Real photo + minimal overlay only.

---

## Pages-to-CRO-element checklist

| Element | index | index2 | index3 | commercial | residential | industrial | shop | showcase |
|---|---|---|---|---|---|---|---|---|
| Hero photo background | ✅ | ✅ | ✅ | photo widget | photo widget | photo widget | ❌ (gradient only) | bespoke animated SVG |
| Mobile sticky CTA | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ |
| FAQ section | ✅ | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ | ❌ |
| FAQ schema markup | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ |
| LocalBusiness schema | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| OG + Twitter cards | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Wellington coverage map | ❌ (homepage) | ❌ | ❌ | ✅ rebuilt | ✅ rebuilt | ✅ rebuilt | ❌ | uses constellation grid |
| 3-up segment block | ❌ (2-up) | ❌ (2-up) | ✅ | n/a | n/a | n/a | n/a | n/a |
| Shop preview | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | full page | n/a |
| AI Price-Match mock | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ✅ | n/a |
| Showcase nav link | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | n/a |

---

## Outstanding asks from Chris (his original email)

| Ask | Status |
|---|---|
| Industrial section, all 3 stand out | ✅ Done (index3 has 3-up, industrial.html exists) |
| Online shop heat pumps / EV / solar / hot water HP / smart panels / HRU | ✅ Preview on index3 + dedicated shop.html |
| AI quote price-match | ✅ Mock UI on index3 + shop.html (clearly demo) |
| Visual "pop" like the drinks photo | ⚠️ Partial — service cards have photos; could go further on hero/projects |
| Study competitor refs (Naylor Love, Aquaheat, Turn You On, Smart EV, etc.) | ❌ Not done — went on instinct. Worth a pass to absorb their visual language. |
| Real videos & images | ❌ Need Chris to supply |
| Industrial sub-page | ✅ industrial.html exists |

---

## Quick "next session" prompts to consider

- "Polish the index3 hero with the visual pop pass — apply the drinks-cooler photo energy to the hero photo background"
- "Build out FAQ sections on commercial.html and industrial.html, with sector-specific SEO-targeted questions"
- "Make a Wellington-services-only specific landing page for [solar / heat pumps / EV chargers] with deep SEO targeting"
- "Add a project case study page template — `case-study-template.html` — and populate 3 (Whitby New World, Mary Potter Hospice, Onslow Medical) with detailed scope, photos, results"
- "Build the residential booking-flow mock — step-by-step quote builder for heat pumps with instant-price-estimate"
- "Build a Wellington Coverage interactive — clickable suburbs with detailed sub-region coverage info"

---

## Email/SMS limitation

This session has NO email or SMS tool. When asked to send:
- Draft a copy-paste-ready email or SMS in the response
- Flag the limitation upfront
- Don't pretend it's been sent

Logan's contact: logan@emporom.org · 029 123 6538 (these are for the next session to know who's using it).

---

## End of handoff
