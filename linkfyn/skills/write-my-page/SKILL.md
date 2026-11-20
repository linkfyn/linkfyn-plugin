---
name: write-my-page
description: Write or improve the words, blocks and order form on a Linkfyn page. Use when a Linkfyn shop owner asks to change their page, rewrite it, add a section, add or change a form, or change its look.
---

# Write a Linkfyn page

A Linkfyn page is read on a phone, by someone who arrived from Instagram, TikTok or a shared link. It should say in a few seconds what the shop sells, why it's good, and how to order.

## How to edit

1. `get_page` for the draft and its `revision`.
2. `get_block_catalogue` before adding a block, or with a block type to see all its fields. Use only blocks, layouts and fields it lists.
3. `edit_page` with all the changes together and the revision. It returns a new revision and any `problems` that would stop a publish; fix those.
4. Changes stay in the draft. Send the `editorUrl` so they can see it. Publish only when they ask (`publish_page`).

If `edit_page` says the page changed since it was read, call `get_page` again and redo the change.

## What good looks like

- Hero: the business name and one line that says what they sell and for whom ("Custom birthday cakes, delivered in Shah Alam"). A real photo.
- Then what they sell (Cards, Gallery or Features), proof (Reviews or Stats) if they have it, the order form, opening hours and location, and FAQ for questions they get every day.
- Buttons say what happens: "Order a cake", "Ask for a quote", "Book an appointment".
- Short sentences. Their words, not marketing words. No made-up reviews, numbers, awards or prices: ask for real ones or leave the block out.

## Order forms

A form is how orders arrive. Ask what they need to know before they can reply with a price or a time: what, how many, when, pickup or delivery. Every form ends with name and phone. Keep it under a minute to fill in. Use `set_form` in `edit_page`.

For shops that take appointments (salons, spas, classes), use the `take-appointments` skill instead of a form that asks for a date.

## Look

`set_look` changes the theme, colours, font and background pattern. Pick one that suits the business, and say what you chose. To take a setting off, such as the pattern, send it in `reset` (`["pattern"]`). To remove a field from a block, such as a photo, set it to null in `update_block`.

## Rules

- Never say Linkfyn takes payments, runs a bot or reads chats.
- Don't put prices in unless the owner gave them.
- Keep to the language the owner writes in. A page in Malay is fine.
