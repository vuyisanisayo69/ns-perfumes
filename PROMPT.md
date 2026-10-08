# Claude Code prompt: NS Perfumes & N.S Detergents website

Paste everything below the line into Claude Code, run from an empty project folder.
Before you start, copy the brand images into `./assets-in/` (logo + perfume stickers + detergent stickers).

---

Build a production-ready website for **NS Perfumes** (sister brand: **N.S Detergents**), a women-owned business that brings a cleaner, better-smelling environment to homes. Use **Next.js (App Router) + TypeScript + Tailwind CSS**. Keep it **simple, light, vibrant and very user friendly**, mobile-first (most customers browse on phones in South Africa).

## Brand and look
- Logo: an afro-haired woman in a rounded arch, with a blue "NS" monogram. Copy it to `public/images/logo.png`.
- Palette taken from the logo and the soap-bubble stickers: sky blue `#1fb2ff` / `#0a86e0`, pink `#ff6fb5`, purple `#9b6bff`, teal `#14d1c0`, sunny yellow `#ffc43d`, on white and very pale tints (`#e3f5ff`, `#fff0f8`, `#e9fffb`).
- **Light mode only and light by default.** Do NOT add a dark theme and ignore `prefers-color-scheme`.
- Vibrant but clean: soft multi-colour gradients in the hero and section backgrounds, gradient (blue to purple) buttons, product cards with a coloured top strip that cycles blue, pink, teal, yellow, gradient section headings, rounded corners, generous spacing. A thin rainbow gradient line under the sticky header.
- Put the colours in Tailwind theme tokens (`tailwind.config.ts`) so the palette is changeable in one place.

## Pages and sections
Single-page home (`/`) with a sticky header (logo, links to Perfumes, Detergents, Contact, and a Cart button with item count):
1. **Hero**: logo, headline "A cleaner, better-smelling home", short line about a women-owned brand, two buttons (Shop perfumes, Shop detergents).
2. **Perfumes**: 100ml clear glass bottle, **every perfume R150**. A sticker goes on each bottle. Products: Red Door, Tsar, Poison, Dolce & Gabbana. Each card shows the sticker image, name, "100ml", price and Add to cart.
3. **Detergents**: standard bottles; each product has a size dropdown and the price updates on change. Add to cart adds the chosen size. Short note: "Washing powder is sold per kg."
4. **Contact**: WhatsApp button (`https://wa.me/27810234107`, label +27 81 023 4107) and email `nngavu@gmail.com`.
5. Footer.

## Detergent price list (Rand)
| Product | 1l | 2l | 5l |
|---|---|---|---|
| Dishwasher Liquid | 25 | 50 | 80 |
| Multi Surface Cleaner | 30 | 60 | 90 |
| Fabric Softener | 20 | 40 | 80 |
| Thick Bleach | 30 | 60 | 90 |
| Pine Gel | 40 | 80 | 200 |
| Bubble Bath | 20 | 40 | 80 |
| Hand Wash Liquid | 25 | 50 | (not sold in 5l) |

Washing Powder (hands & machine): 1kg R25, 2kg R50, 5kg R125.

## Cart and ordering
- Client-side cart (React context + localStorage persistence), slide-in drawer, quantity +/- and remove, running total in Rand.
- **Order on WhatsApp** button builds a message ("Hi NS, I'd like to order: 2 x Red Door 100ml (R300) ... Total: R...") and opens `wa.me/27810234107?text=...`. No payment gateway or backend for now.

## Images
- Sticker images are in `./assets-in/`. Copy to `public/images/stickers/` with clean names (`red-door.png`, `tsar.png`, `poison.png`, `dolce-gabbana.png`, `fabric-softener.png`, `dishwasher-liquid.png`, `multi-surface-cleaner.png`, `detergents.png`).
- Products without their own sticker (Thick Bleach, Pine Gel, Bubble Bath, Hand Wash Liquid, Washing Powder) use `detergents.png` until a dedicated sticker is added. If a perfume sticker is missing, fall back to the logo.
- Use `next/image` with sensible sizes and alt text.

## Easy to edit (important)
The owner is not a developer. Put ALL content in typed data files so changing a price or adding a product never touches components:
- `data/perfumes.ts` (name, image, price default R150)
- `data/detergents.ts` (name, image, sizes with prices)
- `data/site.ts` (business name, tagline, WhatsApp number, email)
Write a short `README.md` section "How to edit products and prices" with copy-paste examples.

## Quality bar
- Accessible (semantic HTML, labels, focus states, contrast), responsive from 360px up, fast (Lighthouse 90+), SEO metadata and Open Graph image from the logo, favicon from the logo.
- No unused dependencies. ESLint and `next build` must pass.

## Deliver
1. Scaffold, build and run it locally; check it at mobile and desktop widths.
2. Initialise git, commit in sensible steps, and write a clear README (run, build, edit products, deploy to Vercel).
3. Ask me before adding anything beyond this scope (accounts, payments, a CMS).
