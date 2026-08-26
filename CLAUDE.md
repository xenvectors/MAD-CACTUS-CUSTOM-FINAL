# MAD CACTUS CUSTOMS — PROJECT CONTEXT

## What this is

Static marketing site for **Mad Cactus Customs**, a one-of-one custom firearm finishing atelier in
Dayton, TX. Owner: Julio. Licensed FFL 07 SOT. ~23.7K Instagram followers, 6 years operating.

Pieces sell around **$4,500**. The site's single job is to make that price feel obvious rather than
surprising.

Designed and built by **Xenvectors** (Ivan Geymonat, @xenvectors).

## Stack

Plain HTML/CSS. **No framework, no build step, no package.json.** Deployed on Vercel, auto-deploys
on push to `main`.

```
index.html      gallery.html    shop.html
events.html     contact.html    styles.css
vercel.json     colt_1911.glb   (hero 3D model)
```

Local dev — you need a server, `file://` blocks the `.glb`:

```bash
python3 -m http.server 8000   # then http://localhost:8000
```

## Design rules — read before changing anything

**The current build is deliberate. Do not redesign it.** The restraint is the whole point; it reads
as a real atelier site rather than a generated one. Preserve:

- The hero, **including the white untextured 3D model** — that is intentional as a concept object,
  not a broken asset
- The existing type scale and vertical pacing
- Section numbering (§01, §02, …)
- The dark palette with cyan accent and gold for emphasis

New work is **additive**. Additions inherit existing CSS. Do not introduce a new visual language.

## Voice

Atelier, not agency. Spec-document register. Reference points are watchmaking and auction
catalogues, not marketing copy.

Anchor lines already in use and working:
- "THE CUSTOM FIREARM ATELIER"
- "Bring us your heirloom."
- "the finish you want lived with for the next fifty years"
- "You approve before metal moves."

Named pieces carry unit numbers (№ 001–004) and names: Karma, Pearl Commander, Nightshade,
Reliquary. Naming individual pieces signals one-of-one better than the phrase does.

## Constraints

- No framework, no bundler, no new dependencies
- Mobile first — most traffic arrives from an Instagram bio link on a phone
- Photography is the product. Never compress hero or portfolio images into mush
- Test locally before pushing
- **§05 PROOF currently holds placeholder testimonials and stats.** They are marked in the HTML.
  They must be replaced with Julio's real ones before this points at `madcactuscustoms.com`

## Open questions for the client

1. High-res photos of the four named pieces
2. Real testimonials with screenshots
3. Real numbers: followers, pieces finished, years, rating
4. Confirm bench hours are accurate
5. Whether SHOP and EVENTS get built out
6. **Before building SHOP: confirm his payment processor allows it.** Most mainstream processors
   restrict firearms-related sales. Finishing services on a customer's own firearm is a different
   category from selling firearms, but confirm in writing before building a checkout
7. Domain status — `madcactuscustoms.com` currently serves an error and `www` does not resolve.
   Confirm he controls it and when it expires

## Task list

The full build brief lives in `BRIEF.md`. Work through it in order.
