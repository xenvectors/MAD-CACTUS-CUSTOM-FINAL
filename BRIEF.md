# MAD CACTUS — CLAUDE CODE HANDOFF

Repo: `https://github.com/xenvectors/MAD-CACTUS-CUSTOM-FINAL`
Stack: plain HTML/CSS. No framework, no build step, no package.json.
Deploy: Vercel, auto on push to main.

---

# PART 1 — SETUP (run these once, in your terminal)

```bash
# 1. Clone
git clone https://github.com/xenvectors/MAD-CACTUS-CUSTOM-FINAL.git
cd MAD-CACTUS-CUSTOM-FINAL

# 2. Start Claude Code in the project
claude

# 3. In a SECOND terminal tab, serve locally so the .glb model loads
#    (opening index.html with file:// will block the 3D model — you need a server)
python3 -m http.server 8000
#    then open http://localhost:8000
```

Deploying is just:

```bash
git add -A
git commit -m "…"
git push
```

Vercel picks it up automatically. No build command to configure.

---

# PART 2 — PASTE THIS INTO CLAUDE CODE AS THE BRIEF

---

## PROJECT BRIEF

This is a static HTML/CSS site for Mad Cactus Customs, a one-of-one custom firearm finishing
atelier in Dayton, TX. Pieces sell around $4,500. The site's job is to make that price feel
obvious rather than surprising.

**The current build is deliberate and mostly right. Do not redesign it.** The restraint is the
point — it reads as a real atelier site, not a generated one. Preserve the existing hero
(including the white 3D model, which is intentional as a concept object), the type scale, the
section numbering, the dark palette, and the overall pacing.

Your task is additive. Bring specific proven elements in from a second prototype without
disturbing what already works.

---

### TASK 1 — Add a primary CTA to the hero

The hero currently ends at "SCROLL TO EXPLORE" with no action. Add a **START A BUILD** button.

- Place it under the "THE CUSTOM FIREARM ATELIER · DAYTON, TX" line, above the unit/finish strip
- Anchor link to the commission form (`#commission`)
- Match existing button styling from the site's own CSS. Do not introduce a new visual language
- Keep it single. One CTA in the hero, not two

---

### TASK 2 — Add bench hours to Selected Pieces (§03)

Each of the four pieces gets an hours figure alongside its existing UNIT and FINISH rows:

| Piece | Hours |
|---|---|
| № 001 Karma — Desert Eagle .50 | `94H` |
| № 002 Pearl Commander — Colt 1911 .38 Super | `62H` |
| № 003 Nightshade — Browning Hi-Power | `48H` |
| № 004 Reliquary — Micro Uzi 9mm | `120H` |

Label it `BENCH`. Same type treatment as UNIT and FINISH.

**Why:** this is the strongest price justification on the site. 94 hours of hand work makes $4,500
read as cheap. Give it equal visual weight to FINISH, not smaller.

Also add a `COMMISSION SIMILAR →` link to each piece, anchored to `#commission`.

---

### TASK 3 — Add a DOCTRINE section

Insert a new section between the hero and the current §01, and renumber everything after it.

Content — one line, nothing else on the screen:

> **We finish firearms the way old-world houses finished pocket watches — patient, by hand, and never the same piece twice.**

Set in the site's existing serif display face. Emphasise "patient" in the gold accent already used
elsewhere. Give it generous but not excessive space — roughly one viewport, not three.

---

### TASK 4 — Add a trust block

Four items, placed directly above the commission form:

- `48H` — First reply from the bench
- `1:1` — Direct with the artisan, not a rep
- `FFL` — Fully insured transfer both ways
- `6YR` — Every finish backed by a written guarantee

Same grid treatment as the existing §05 PROOF stats.

**Why:** each one kills a specific objection someone has about mailing a stranger their firearm.

---

### TASK 5 — Build the commission form (highest priority)

Add `id="commission"` section before the final invitation. This is the conversion engine.

Fields:

- **HOST FIREARM** (select one): 1911 / 2011 · Glock · Sig P320 / P365 · AR Platform · Revolver · Shotgun · Other
- **SERVICES** (select multiple): Cerakote · Laser Engraving · Hand Scroll · 24K Gold Plate · Chrome Polish · Stippling · Full Custom Build
- **TIMELINE**: ASAP · 1–3 months · 3–6 months · Flexible
- **INVESTMENT**: $500–1.5K · $1.5K–4K · $4K–10K · $10K+
- **NAME**, **EMAIL**, **PHONE**
- **REFERRED BY** (optional)
- **VISION / NOTES** (textarea)

Submit: `SEND INQUIRY →`
Fine print: "You'll receive a reply within 48H."

**Backend:** static site, so use a form service. Web3Forms or Formspree — both are a single POST
action attribute, no build step, no serverless function. Put the endpoint in a clearly marked
placeholder so it can be swapped.

**The INVESTMENT field is the most important element on the page.** It qualifies budget before
any conversation happens. Style it as a deliberate choice, not a buried dropdown — segmented
buttons in the same style as the services selector.

---

### TASK 6 — Audit the secondary pages

`gallery.html`, `shop.html`, `events.html`, `contact.html` exist in the repo. Check each one
actually has content. Report back which are empty or placeholder — do not delete anything without
asking. If SHOP is empty, that's a separate phase, not something to hide.

---

### CONSTRAINTS

- No framework. No build step. Keep it plain HTML/CSS.
- No new dependencies beyond what the 3D model already needs.
- Do not restyle existing sections. Additions must inherit the current CSS.
- Mobile first — most traffic arrives from an Instagram bio link on a phone.
- Test locally with `python3 -m http.server 8000` before pushing; `file://` breaks the .glb load.
- Placeholder testimonials and stats are currently in §05 PROOF. Leave them, but mark them clearly
  in the HTML with a comment so they are impossible to ship to a live domain by accident.

---

# PART 3 — STILL NEEDED FROM JULIO

Build proceeds without these, but they go in before it points at his domain:

1. High-res photos of the four named pieces
2. Real testimonials with screenshots
3. Real numbers: followers, pieces finished, years operating, rating
4. Confirm the bench hours above are accurate
5. Whether SHOP and EVENTS should be built out
