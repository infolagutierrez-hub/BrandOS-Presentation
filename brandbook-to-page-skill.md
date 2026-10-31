# brandbook-to-page

Un skill para Thaura: convierte cualquier brandbook o documento de dirección visual (markdown) en una página web con calidad de dirección de arte.

**Cómo instalarlo:** pega todo el texto de la sección «Skill» (desde la línea `name:` hasta el final) en un chat de Thaura y di: «guárdame esto como skill». También puedes crearlo a mano en la barra lateral → Customize → Skills → escribir uno propio, copiando el nombre, la descripción y el cuerpo de abajo.

---

## Skill

```markdown
name: brandbook-to-page
description: Build a distinctive, high-quality web page from any brandbook / visual-direction markdown (or rebuild a page from one). Use when the user provides a brand md and asks for a landing page, site, or page from it.

# Brandbook → page

Turn any brandbook or visual-direction markdown into a web page that feels art-directed, not generated. The brandbook is the floor, not the ceiling: its hard rules are followed exactly, and the craft is spent on everything it leaves open.

## Inputs

- The brandbook markdown (required). Read it IN FULL with the read tool before anything else — never build from an excerpt or from the user's summary of it.
- Copy. If the brandbook says to ask for it and none was given, ask once, briefly. If the user says to use placeholder/filler text, write demo copy as if it were final copy, in the brand's voice: filler never means sloppy or lorem-ipsum copy. Note at the end which text to swap.
- Page type (default: scrolling landing; single screen when the copy is one message).
- Language of the page: match the user's language unless the brandbook or copy says otherwise.

## Process

1. **Extract, don't skim.** From the brandbook pull out: tokens (color, type, spacing scale, radius, easing), hard rules (anything marked non-negotiable, exact, "use this exact", "must"), system defaults, and expressive-only fields (marked "deduce it"): those are deduced from the decisions above and kept constant, never invented from scratch.
2. **Ask only what materially blocks you** — usually real copy and the page's one primary action. Never ask about anything the brandbook already answers; a structural field left unanswered takes the brandbook's default, not an invented value.
3. **Plan before building.** Most brandbooks demand the answer open with a numbered structure list: format, the goal and its one primary action, then per section: name, archetype, background, first words of its copy. Produce that list even when not explicitly asked, then build from it.
4. **Design pass (the anti-meh step).** Before writing code, decide:
   - The ONE signature element of this page, derived from the brand's own motifs (a shape, a device, a compositional idea). One memorable thing; everything around it stays quiet and disciplined.
   - Composition: vary the rhythm between sections — no two consecutive sections with the same background, alignment, column count and density when the brandbook's alternation rules say so; asymmetric splits, generous whitespace, one clear focal point per section.
   - Type at full strength: use the display steps the scale allows where hierarchy allows it. Following the scale timidly reads as a template.
   - Generic tells to refuse even when the brandbook is silent: identical rounded cards in even rows for content that isn't parallel; a tracked-out all-caps eyebrow above every heading; middle-dot meta strings; a gradient wash as decoration; drop shadows the brandbook never sanctioned; the hero as "big number + small label + gradient accent"; italicizing one word of a headline for emphasis.
5. **Build.** One self-contained HTML file. Inline fonts as data: URIs (subset to Latin with pyftsubset if the brand names real families; fall back to the brandbook's own fallback stack). Tokens as CSS custom properties. Any pattern the brandbook provides verbatim (markup, CSS, easing) is used as given, not re-derived. Mobile-first, `clamp()` type steps, `svh` not `vh`, meta viewport, no fixed widths, no CDN requests of any kind.
6. **Motion.** One orchestrated page-load moment, then motion only where it answers an action or marks a reveal: scroll reveals sparing and consistent, accordions/toggles with the brandbook's easing, count-ups only where figures exist. Everything silent under `prefers-reduced-motion`. Never scattered decorative animation.
7. **QA in a real browser (mandatory, not optional).** Playwright: load the file at 360, 390, 768, 1280, 1600 px. At each: no horizontal scroll, no element wider than the viewport, no clipped or overlapping text. Check contrast of the actual token pairs (4.5:1), visible focus rings, keyboard-reachable interactions. Take full-page screenshots at 1280 and 390, look at them, and critique against the plan: if it looks like the generic version of this brand, fix composition and re-shoot before delivering.
8. **Deliver.** Present the single file. In the reply: the numbered structure, one line on the signature element, and which strings to replace with real copy. No long postamble.

## Hard rules

- The brandbook's explicit rules always win over anything in this skill, including the design taste here. When the brandbook demands a "generic" look on purpose, that is the brief.
- No external network requests from the page: fonts, images, libraries all inlined (data URIs, npm-inlined builds). Illustrations are drawn with code from the palette, never fetched.
- Never draw recognizable third-party characters, logos or covers; original brand motifs only.
- Accessibility is part of the quality bar, not a checklist item: semantic HTML, real buttons, alt text on meaningful graphics, 44px touch targets, `env(safe-area-inset-*)` on fixed elements.
- One primary action per viewport; everything else secondary or text link.
- Deliverable is one file in /mnt/user-data/outputs, presented with present_files.
```
