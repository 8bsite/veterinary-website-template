# Free HTML veterinary website template with GSAP scroll animations — Burrow

**Website for a veterinary clinic or animal hospital: a free HTML template in one file, with GSAP scroll animations, no build step, MIT license. Made by [8B](https://8b.com/), the AI website builder.**

[![License: MIT](https://img.shields.io/badge/license-MIT-blue)](LICENSE) ![one HTML file: no build](https://img.shields.io/badge/one%20HTML%20file-no%20build-orange) ![GSAP: ScrollTrigger](https://img.shields.io/badge/GSAP-ScrollTrigger-88ce02)

**[Live demo](https://8bsite.github.io/veterinary-website-template/)** · **[Use this template](https://github.com/new?template_name=veterinary-website-template&template_owner=8bsite)** · **[Download ZIP](https://github.com/8bsite/veterinary-website-template/archive/refs/heads/main.zip)**

<a href="https://8bsite.github.io/veterinary-website-template/"><img src="previews/desktop.png" alt="Burrow, a free HTML template: first screen on a desktop" width="76.1%"></a> <a href="https://8bsite.github.io/veterinary-website-template/"><img src="previews/phone.png" alt="Burrow, a free HTML template: first screen on a phone" width="21.9%"></a>

<p align="center"><a href="https://8bsite.github.io/veterinary-website-template/"><img src="previews/scroll.gif" alt="Burrow, a free HTML template: scrolling through the first sections on a desktop" width="40%"></a><br><sub>Scroll animation</sub></p>

A one-page site for a neighbourhood vet clinic that sees dogs, cats, rabbits, birds and reptiles, with services, vets, prices, recent patients and a visit request form. Warm cream and dark brown with six muted accent colours; a set of flat shapes (arch, circle, diamond, plus) does the moving: the small coral arch grows into a doorway on the first scroll, colour panels are dealt out like cards and the patient cards roll past like a wheel.

Good for: veterinary clinic or animal hospital; exotic-pet or specialist vet practice; pet groomer, boarding or other pet-care business; any small local clinic with a team, services and a price list. Free for personal and commercial use (MIT), made by [8B](https://8b.com/).

## Quick start

Pick one:

- **With an AI coding agent** (Claude Code, Codex, Cursor, Windsurf…). Download the files into your project (in Windows PowerShell type `curl.exe`):
  ```bash
  curl -LO https://raw.githubusercontent.com/8bsite/veterinary-website-template/main/index.html
  curl -LO https://raw.githubusercontent.com/8bsite/veterinary-website-template/main/AGENTS.md
  curl -LO https://raw.githubusercontent.com/8bsite/veterinary-website-template/main/LICENSE
  curl -LO https://raw.githubusercontent.com/8bsite/veterinary-website-template/main/CREDITS.md
  ```
  Then give your agent this prompt:
  ```text
  Read AGENTS.md, then edit index.html. Use this template as the base for a veterinary clinic site for <your practice: name, town and address, which animals you see, services and prices, vets and nurses, opening hours, how to book>. Keep the layout, the motion and the single-file format; replace the brand name, copy, photos, staff, patient stories, prices, hours, links and contacts, and recolour it through the CSS variables if needed.
  ```
  Give the agent the downloaded file, not a link: an agent reads a link as a summary and would rebuild a different page.
- **No code.** Download the ZIP, unzip it, replace the contacts and texts in `index.html`, put `index.html` into an empty folder and drag that folder onto [Netlify Drop](https://app.netlify.com/drop). The page is online in a minute.
- **On GitHub.** Click **[Use this template](https://github.com/new?template_name=veterinary-website-template&template_owner=8bsite)** to get your own copy, then **Settings → Pages → Deploy from a branch → main**. Your site appears at `https://<you>.github.io/<repo>/`.

## What's on the page

- **Navigation** — top bar: arch logo and wordmark, section links, Book a visit button; phone menu overlay
- **Calm, thorough, kind. Vet care for every animal.** — first screen: headline, two buttons, wide photo and floating shapes; second screen: four numbered steps of a visit on a coral arch
- **Two doors. Cats never wait with dogs.** — two arch-cut photos either side of the copy (demo: separate cat and dog sides of the clinic)
- **Small, scaly, feathered or furry.** — four overlapping colour panels, one per group (demo: animals the clinic treats)
- **What we do here.** — list of six services, each row with a photo, text and a short note
- **Who you’ll meet in the room.** — four people with portraits, role and one line (demo: vets and head nurse)
- **This month at Burrow.** — pinned horizontal row of seven cards (demo: patients of the month, name, breed, age, why they came)
- **Prices you see before we start.** — dark band: price list (service, what is included, price) and a note on estimates
- **On Lombard Street since 2014.** — sticky building photo beside three dated paragraphs (demo: the clinic's history)
- **Before you come in.** — questions and answers (native &lt;details&gt;)
- **Come in.** — coral arch panel: address, phone, email, hours, photo and a visit request form
- **Footer** — rounded panel: brand line, address, three link columns, copyright and the Design: 8B credit

## Before you publish

- Replace everything marked `data-8b-placeholder` (social preview image, favicon, phone, email, map, form, social) and the invented demo facts — prices, dates, address. [AGENTS.md](AGENTS.md) lists them.
- The contact form does not send anything yet: connect it to a form service (Formspree, Netlify Forms) or remove it; [AGENTS.md](AGENTS.md) shows both.

## Customize

- **Colours and fonts**: CSS variables in the `:root` block at the top of `<head>`.
- **Text**: edit it in place.
- **Photos**: replace `src`, delete `srcset` and `sizes` (they list Unsplash sizes) and update the `alt` texts.
- **Animations**: each section's animation is one `<script data-8b-part="scene:<id>">` block at the end of the file. For native scroll, delete the Lenis block in `page-init`.

## For developers

- **Stack.** HTML and CSS (custom properties, cascade layers) with GSAP 3.13.0, ScrollTrigger, SplitText, Lenis 1.3.27 from jsDelivr. No build step, no framework, no npm. 104 KB.
- **Layout of the file.** `<head>`: CSS variables, shared classes, then one style block per section. Then the markup, one element per section with a one-line comment above it. End of `<body>`: small behaviour scripts, the libraries, smooth scroll (`page-init`), the effects, one animation script per section.
- **Browsers.** Chrome and Edge 108+, Safari 15.4+, Firefox 101+ (it uses cascade layers, small/dynamic viewport units).
- **Accessibility.** Motion runs only when the visitor's system allows it; with "reduce motion" the page is complete and still. FAQ answers use native `<details>` and open without JavaScript. Every photo has alt text.
- **External requests.** fonts.gstatic.com, images.unsplash.com, cdn.jsdelivr.net. No analytics, no cookies. To self-host everything (offline use, or Google Fonts and GDPR in the EU), download those files and change the URLs.
- **Licences of the parts.** GSAP is free, commercial use included, under its own standard licence (not MIT); Lenis is MIT; fonts are SIL OFL; photos are under the Unsplash License. See [CREDITS.md](CREDITS.md).

## FAQ

**Can I use it for a client or a commercial site?** Yes. The code is MIT: use it, change it, sell the site you build with it.

**Do I have to keep the "Design: 8B" link?** No. It is welcome, not required.

**Can I use it in React, Next.js, Astro or Vue?** Yes. Move each section's markup and style block into a component and run its animation script in `useGSAP()` (React) or `onMounted` (Vue); start Lenis once. Or keep it as a separate static landing page next to your app (`example.com` for the landing, `app.example.com` for the app).

**Why doesn't the contact form send?** It is a demo. Connect it to Formspree, Netlify Forms or your backend; AGENTS.md has the steps.

**Where are the photos from?** Unsplash; they load from Unsplash's servers. Replace them with your own when you can.

## More free templates

[More 8B templates on GitHub](https://github.com/8bsite) · [8b.com](https://8b.com/)

## License

The template code is MIT licensed — see [LICENSE](LICENSE). Photos, fonts and libraries keep their own licences — see [CREDITS.md](CREDITS.md).
