# Burrow — notes for AI coding agents

One HTML file: markup, inline CSS and inline scripts; GSAP with ScrollTrigger and SplitText, Lenis smooth scroll, all from jsDelivr. No build step, no framework.

## Files
Work from the files: a page read through a link comes back as a summary, and a page rebuilt from it would differ.
```bash
curl -LO https://raw.githubusercontent.com/8bsite/veterinary-website-template/main/index.html
curl -LO https://raw.githubusercontent.com/8bsite/veterinary-website-template/main/AGENTS.md
curl -LO https://raw.githubusercontent.com/8bsite/veterinary-website-template/main/LICENSE
curl -LO https://raw.githubusercontent.com/8bsite/veterinary-website-template/main/CREDITS.md
```
In Windows PowerShell type `curl.exe`. Publish `index.html` with LICENSE and CREDITS.md; this file, README.md and `previews/` are not part of the site.

## Do not break
- Keep it one file unless the user asks otherwise; no framework or bundler for copy, colour or photo changes.
- Keep the ids and the `data-8b-section` / `data-8b-motion` attributes. Each section has its styles in `<style data-8b-part="section:<id>">` and its animation, if any, in `<script data-8b-part="scene:<id>">`.
- The scripts find these classes and attributes; when you change a section's markup, keep them or update the script:
  - `section-script:navigation`: `.nav__sheet` `.nav__toggle` `.nav__close`
  - `section-script:opening`: `.op-first`
  - `scene:opening-door`: `.op-shape--arch` `.op-door` `.op-second` `.op-photo` `.op-visit__title` `.op-step__mark` `.op-shape`
  - `scene:doors-open`: `.dr-grid` `.dr-door` `.dr-door__frame`
  - `scene:species-deal`: `.sp-row` `.sp-panel`
  - `scene:care-index`: `.ca-row` `.ca-frame` `.ca-rule`
  - `scene:patients-track`: `.pt-pin` `.pt-track` `.pt-card` `data-track`
  - `section-script:contact`: `.ct-form` `.ct-status`
  - `scene:story-walk`: `.st-frame` `.st-text`
  - `scene:contact-arch`: `.ct-panel`
- Colours, fonts, radii and shadows are CSS variables in the `:root` block (`data-8b-part="tokens"`); change them there and keep body text at 4.5:1 contrast or more.
- Animations run only when the visitor allows motion (`prefers-reduced-motion: no-preference`); the page must stay readable without them.
- Keep the header comment and `<meta name="generator">`; the "Design: 8B" footer link is optional.

## Replace before publishing
- Everything marked `data-8b-placeholder` (og-image, favicon, phone, email, map, form, social); remove the attribute once the real value is in. With no real value: no preview image — delete the `og:image` tag and set `twitter:card` to `summary`; no phone, email or address — remove that link or row.
- Book a visit buttons (nav, phone menu, hero, footer): link to #contact now; point them to your online booking page, or keep them on the contact form.
- Privacy link in the footer: link to #contact now; point them to your privacy policy page.
- **The form sends nothing.** `section-script:contact` checks the fields and shows a thank-you message without sending. Pick one:
  - Formspree: set `action="https://formspree.io/f/<id>"` on the form; in the script, before the thank-you message, `await fetch(form.action, { method: 'POST', body: new FormData(form), headers: { Accept: 'application/json' } })` and show it only if the response is ok.
  - Netlify Forms (site on Netlify): add `name="contact" data-netlify="true"` and `<input type="hidden" name="form-name" value="contact">`; send with `fetch('/', { method: 'POST', headers: { 'Content-Type': 'application/x-www-form-urlencoded' }, body: new URLSearchParams(new FormData(form)) })`.
  - No form service: remove the `<form>` together with the script that handles it (it would fail without the form) and keep the email link.
- Invented demo facts (ask the user for the real ones; do not make up prices, dates or addresses):
  - Place: North Lombard Street, Portland, Oregon — "2140 N Lombard Street, Portland, OR 97217" with a Google Maps link (contact, footer), "A neighbourhood clinic on North Lombard Street" (opening), "On Lombard Street since 2014" (story), the Willamette river (services, Vaccines), and in the `<title>` and the meta description.
  - Phone 503 000 0000 and email hello@burrow.example are placeholders (opening button, faq, contact, footer); also "texts welcome", "text us from the car park" (contact, opening step 1).
  - Opening hours: "Open six days" (opening), Monday–Friday 8 am – 7 pm, Saturday 9 am – 3 pm, Sunday closed (contact), "Mon–Fri 8–7, Sat 9–3" (footer); nights and Sundays sent to "the city's 24-hour emergency hospital" (faq).
  - Same-day sick visits: "four slots every day", "call before 10 am" (opening, services, faq).
  - How a visit works: check in by text from the car, 30-minute exams on the floor, a written plan and price before any treatment, a text the next morning and free questions by text for a week (opening steps).
  - Prices (prices): check-up $78, same-day sick visit $92, rabbit, bird or reptile exam $86 (forty minutes), vaccine $32 each, microchip $55 with lifetime registration, dental cleaning from $420, cat spay or neuter from $310, dog spay or neuter from $420, nail trim $18 without appointment; estimates with a low and a high number and a call before passing the high one.
  - Payment: "work with every insurer" and the claim form filled in before you leave; bills over $500 in three monthly parts with no interest (faq).
  - Service schedule and promises: check-ups once a year, twice for older animals, any weekday; vaccines given during a check-up; dental patients home by the afternoon and a photo of every extracted tooth; surgery on Tuesdays and Thursdays, a nurse watching the anaesthetic, a call when they wake; home visits and goodbyes at home or in "our garden room"; a referral letter the same day (services, team, faq).
  - The building: split into separate cat and dog sides in 2018 with their own entrances and waiting rooms, shelves for carriers, a scale in the floor, a heated warm room kept at 82°F (clinic-sides, species, team, story).
  - Animals seen: dogs, cats, rabbits, guinea pigs, rats, ferrets, parrots, lizards, snakes, tortoises; first shots at eight weeks (species).
  - Staff (team, story, species): Dr. Martin Hale (founder, twelve years in an emergency hospital, Tuesday surgery list), Dr. Priya Raman (co-founder, ran a feline clinic at a teaching hospital), Dr. Leo Marchetti (rabbits, birds and reptiles, "twenty years"), Rosa Delgado, LVT (head nurse and anaesthesia); the portraits are stock photos and their alt texts carry these names. The species paragraph says "Four of our vets", the team says "Three vets and a head nurse".
  - Patients (patients): Pip (Maltese, 3), Fern (tabby, 11), Mochi (lop rabbit, 2), Biscuit (poodle cross, 5 months), Snow (kitten, 10 weeks), Kiwi (conure, 6), Atlas (German shepherd, 13), with their treatments, "in September", "the cone comes off on the 14th" and "shared with their people's permission"; the photos are stock photos, not patients.
  - History (story): since 2014 in a former fish café with "a sign we never took down" and a borrowed X-ray machine; the upper floor and the split in 2018; Leo joining and the whole corner in 2023.
  - Service times: "We reply within two hours while we are open" and the thank-you message "We will call you back within two hours" (contact form); "New patients are welcome" (contact).
  - Business name and form: "© 2026 Burrow Veterinary PC" (footer) and "Burrow Veterinary" in the logo, title and copy.
- `<title>`, the meta description and the og tags; photos (Unsplash, see CREDITS.md) when the user has their own.

## Notes
- The coloured shapes, the arch logo mark and the coral doorway are CSS (border-radius and clip-path), not images: recolour them through the --color-* variables.
- The second screen of the opening (the four steps on the coral arch) belongs to the same section as the first screen; the arch animation measures both, so keep them together.
- On phones the growing arch is stretched more in height than in width, so mid-scroll it reads as a tall coral door; it lands exactly on the second screen's arch.
- The service photos fold back into their small pill as a row leaves the top of the screen; at rest (no JavaScript, reduced motion) every photo is open.
- The building photo in story shows a shop sign and street signs of the real place it was taken; replace it with a photo of your own building.
- Without JavaScript the phone menu button cannot open the link sheet; the links stay reachable in the footer.

## Common edits
- Rebrand: search the old name (`Burrow`) in any letter case and replace every match; change the favicon letter and colours in `<link rel="icon">`.
- Photos: replace `src` and delete `srcset` and `sizes` (they list Unsplash sizes), keep `width`/`height` to the new photo's ratio, update `alt` and CREDITS.md.
- Remove a section: delete its markup, its `section:<id>` and `scene-style:<id>` styles, its `scene:<id>` and `section-script:<id>` scripts, and links to `#<id>`.
- Native scroll instead of smooth scroll: delete the Lenis block in `page-init` and the Lenis `<script>` tag.

## Check and publish
- Open the page at 375 and 1440 px, with reduced motion on, with the console open.
- Search `data-8b-placeholder` and the old name: nothing should be left but class names.
