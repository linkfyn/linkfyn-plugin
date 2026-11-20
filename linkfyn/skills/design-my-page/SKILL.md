---
name: design-my-page
description: Design a Linkfyn page so it looks made for the business, not like a template - picks colours, fonts, layouts and words from the business type and from the owner's own photos, logo, Instagram or website. Use when making a new Linkfyn page, when an owner says their page looks plain, generic or not nice, or asks to change its look or style.
---

# Design a Linkfyn page

A plain page with the starter's blocks looks like every other page. Linkfyn's best pages (the sample shops on its homepage) each have their own look: a florist in soft pink with a serif font, a print studio in black and orange, a spa in calm green. Your job is to give this owner's page that kind of look, from what you know about their business and what they show you.

Work in this order. Don't skip step 2: the photos and colours they give you are what make the page theirs.

## 1. Know the business

You need, in plain words: what they sell, to whom, and how a customer orders (a quote, a date, a time slot, or a product). Map it to one kind: food, flowers, print, beauty, events, services, coaching, or other. If you made the shop with `create_shop`, you know it already.

## 2. Gather their style

Look at everything they've already shared in the chat before asking:
- **Photos** of the shop, products, work or themselves: note the main colours, light or dark, and the materials (wood and kraft, marble and gold, neon, pastel, chrome, plants).
- **A logo, sign or packaging**: its strongest colour is the brand colour. Read it as a hex value.
- **An Instagram, TikTok or website link**: if you can open it, read the bio, product names, prices, opening hours, area and how they talk. If you can't open it (Instagram often blocks this), ask them to paste their bio and send a few photos instead.
- **A page they like** ("make it like this"): take its feel only. Never copy its words or photos.

If you have no photos and no colour yet, ask once, in one short message:

> To make it look like your shop, send me 3 to 6 photos of your work, your logo if you have one, and your Instagram or website. If you always use a colour, tell me that too.

If they'd rather not, carry on: you'll design without photos (see below) and say photos can be added later.

Use the photos they send to choose the style. A small one you can read, such as the logo, can go in with `upload_photo` as a `data:image/...;base64` address (2 MB at most). For full photos, or many of them, give the owner `addPhotosUrl` (from `create_shop` or `get_setup_progress`) to upload them from their phone, and use `list_photos` to place them. Photos at a public https address (for example on their own website) can go in with `upload_photo` too. Only ever use the owner's own photos.

## 3. Pick the look

Call `get_design_ideas` with the kind, plus `brand` if you have their colour (and `dark: true` for night, music or streetwear shops). It returns:
- `styles`: ten looks taken from the sample shops, best for this kind first, each with a mood, clues to match against their photos, and the exact theme, colours, font, buttons, corners and headings.
- `palettes` (when you sent `brand`): three ways to use their own colour, each a background, text and brand already checked for contrast: `tinted` (a soft page tinted with it), `clean` (near-white, their colour only on buttons) and `dark`. `palette` is the tinted one.
- `schemes`: Figma's 53 website colour palettes (figma.com/resource-library/website-color-schemes), in its five groups (neutral, warm, cool, bold, modern), the ones that suit this kind first. Each has Figma's name, a mood, Figma's own `colours`, and the background, text and brand colour to use on the page, already checked for contrast. `dark: true` marks a dark page.
- `plan`: the blocks the best page of this kind uses, in order, with layouts, what each does, hero lines, button labels and the form's questions.

Choose one look by matching its `clues` and `mood` to what they showed you. The look gives the font, buttons, corners and headings. Then choose its colours:
- **They have a colour** (logo, sign, packaging, or they told you): use one of `palettes`. `tinted` suits most shops, `clean` suits a busy logo or colourful photos, `dark` suits night, music and streetwear.
- **No colour of their own**: the look's own colours are a safe choice. If their photos say otherwise, pick a scheme from `schemes` whose mood matches them (warm for food and handmade, cool for calm and trust, neutral to let photos lead, bold for fun and parties, modern for sleek shops, a dark one for nightlife and premium). Show two or three schemes by name and mood in one short message ("Honey opal sunset: mustard and taupe, timeless. Terrazzo: ochre and sand. Neutral elegance: beige and brown.") and recommend one; carry on with your pick if they don't answer.
- Send the colours with `set_look` as `background`, `text` and `brand`. A dark scheme or dark palette also sets theme `midnight`.

Tell the owner the look in one line, with why ("Soft and romantic, in your logo's rose pink, because your bouquets are pastel"). Don't ask them for fonts or hex codes.

Rules for colours: most of the page is the background, text is for reading, and the brand colour is only for buttons, links and small marks. One brand colour only, a light page unless the shop is dark by nature, and no pattern unless the look has one. To take off a pattern the page already has, send `set_look` with `reset: ["pattern"]`. Linkfyn's own navy is for Linkfyn, not for shops.

## 4. Build it

Read the page with `get_page`, and `get_block_catalogue` for each block type you'll fill. Then make the whole design in one `edit_page` call:
1. `set_look` with the theme and the design values.
2. Follow the plan's blocks in order: add, update, move and remove blocks so the page matches it. Use the layouts it names. Set `background` on the blocks the plan marks `surface` or `tint`; that rhythm of plain and tinted sections is what makes a page look designed.
3. Leave out any block whose `needs` they can't give. No reviews means no reviews block, no rating and no proof line in the hero. No real numbers means no stats. Never make them up, and never leave the starter's sample text ("Add a review from one of your customers here", "Say what's included and the price").
4. Make the form ask what the plan's `form` says, with their real options and prices (`set_form`).

### Words

The words matter as much as the colours. Write them like the samples:
- **Hero title**: a promise in six words or fewer ("Cakes worth gathering for.", "Your design. Printed loud."). For a person (photographer, coach, artist), their name works as the title.
- **Badge**: "NAME · WHAT THEY ARE" in capitals ("MAISON FLEUR · FLORAL STUDIO"), or what's open now ("Booking 2027 dates"). In the side-by-side (`split`) hero the text column is narrow, so keep the badge under 18 characters ("CAKE STUDIO · KL") or it wraps.
- **Subtitle**: what they sell, for whom, and how ordering works, in under 25 words.
- **Buttons** say what happens: "Price my cake", "Check my date", "Book a treatment".
- **Headings** with some voice: "Our favourites", "From the people who ate them", "Before you order". Never "Our Services" or "Welcome to our website".
- **Form heading** as the result they get: "Price your cake in 30 seconds", "Is your date still free?".
- **About**: a text block in the owner's own voice, "Hi, I'm Hana", two short paragraphs.
- **Footer note**: "Name · what they do · area".
Match the look's `voice`. Keep to the language the owner writes in.

### Without photos

Follow `withoutPhotos` from `get_design_ideas`: a profile hero with their logo, emoji icons in features, cards without photos, and no gallery or categories. It should still look finished. Remove the starter's sample photos rather than leave them.

## 5. Check before showing

Read the result of `edit_page` and go through this list. Fix anything that fails in one more `edit_page`:
- The hero has their photo (or logo), a short promise and one main button.
- One brand colour, and the look you named is what `set_look` saved.
- Sections alternate: at least one `tint` (usually the form) and one `surface` block.
- Every button goes somewhere real; the main button opens the form or the appointment page.
- No sample photos, sample text, made-up reviews, ratings or numbers; `problems` is empty.
- The page is short enough to scroll on a phone in under a minute: about 6 to 9 blocks.

Then send the `editorUrl` and say in two lines what you chose: the look and why, and what would make it better (usually more photos or real reviews). Publish only when they ask.

## Changing an existing look

When the owner says the page looks plain or they don't like it, ask what they don't like if it isn't clear, then go back to step 2: ask for photos and colours if you don't have them, pick a different look, and rebuild with the plan. Small changes ("make it pinker", "a rounder font") are one `set_look`. "Other colours" means offer two or three `schemes` (or the other `palettes`) and keep the layout.

## Rules

- Never say Linkfyn takes payments, runs a bot or reads chats.
- Don't put prices in unless the owner gave them.
- Say "appointment", not "booking". Shops that take appointments use the `take-appointments` skill and a button with `{"kind": "book"}`, not a date form.
- Never use another business's photos, logo or words.
