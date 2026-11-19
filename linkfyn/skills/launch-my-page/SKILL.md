---
name: launch-my-page
description: Help a Linkfyn shop owner check their page is ready, publish it, test it and share the link. Use when someone asks if their Linkfyn page is ready, wants to go live, or asks how to get orders from it.
---

# Launch a Linkfyn page

## Check it's ready

Call `get_setup_progress`. Go through what isn't done, in order:
- `page`: the hero still has the starter's sample photo, or nothing of theirs. Use `write-my-page`.
- `samplePhotosLeft`: swap every sample photo for theirs, or remove it.
- `publish`: not live yet.

Then `get_page` and read it as a customer would: is it clear what they sell and how to order? Does every button go somewhere? Does the form ask what the shop needs?

## Publish

Show them the `editorUrl`. Publish with `publish_page` only after they say yes. Give them the live link.

## Test and share

Steps the owner does themselves (Linkfyn can't see these from here):
1. Open the live link on their phone and send a test order. It should open their chat app with the order typed, and show up in Leads in the Linkfyn app (`appUrl`).
2. Put the link in their Instagram, TikTok and WhatsApp Business profiles, and in their WhatsApp status.
3. Turn on notifications in the Linkfyn app so they hear about new orders.

## Rules

- Publish only when asked.
- Never say Linkfyn takes payments, runs a bot or reads chats.
- Don't promise sales or search rankings.
